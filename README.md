# week05.cpp

#include <GL/glut.h>
#include <stdio.h>
float vx[2000], vy[2000];
int N=0;
void display()
{
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    ///glBegin(GL_LINE_LOOP);
    glColor3f(1,1,1);
    glBegin(GL_TRIANGLE_FAN);
    glVertex2f(0,0);
    for(int i=0; i<N; i++){
        glVertex2f(vx[i], vy[i]);
    }
    glEnd();
    glutSwapBuffers();
}
void mouse(int botton,int state,int x,int y)
{
}

void motion(int x, int y)
{
    printf("%d %d\n", x, y);
    vx[N] = (x-150)/150.0;
    vy[N] = -(y-150)/150.0;
    N++;
    display();
}

int main(int argc, char *argv[])
{
    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("08160431如 week05");

    glutDisplayFunc(display);
    glutMouseFunc( mouse );
    glutMotionFunc(motion);
    glutMainLoop();
}
