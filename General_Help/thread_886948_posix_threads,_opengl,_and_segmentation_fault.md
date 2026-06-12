---
title: "posix threads, opengl, and segmentation fault"
date: 2008-08-11
forum: General Help
---

### Post by atlantis9860 on 2008-08-11
Hi, 
I need some help with using posix threads and opengl...this is my first attempt at doing some multithreading in ubuntu.  I've got this simple file that creates a thread, and calls a function to do glut initializations and then display a box.  This is the code I'm referring too: 

#include <GL/glut.h>

#include <GL/glu.h>

#include <GL/gl.h>



#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>


int argc_ptr; 

char **argv_ptr;


void display1() {

  glClear( GL_COLOR_BUFFER_BIT );
  glColor3f( 1,1,0 );
  glBegin( GL_POLYGON );
  glVertex2f( -0.5, -0.5 );
  glVertex2f( -0.5,  0.5 );
  glVertex2f(  0.5,  0.5 );
  glVertex2f(  0.5, -0.5 );
  glEnd();
  glFlush();

}




void *thread_function1(void *Ptr){
  //printf("Thread number 1, ID = %d\n", pthread_self() );
  printf("1");
  glutInit( &argc_ptr, argv_ptr );
  printf("2");
  glutInitDisplayMode( GLUT_RGB );
  printf("3");
  glutInitWindowPosition( 100, 100 );
  printf("4");
  glutInitWindowSize( 600, 600 );
  printf("5");
  glutCreateWindow("demo");
  printf("6");
  glutDisplayFunc( display1 );
  printf("7");
  glutMainLoop();
  printf("8");
}

int main(int argc, char **argv ){
    argc_ptr = argc;

    argv_ptr = argv;

      pthread_t p_thread;

      pthread_create( &p_thread, NULL, &thread_function1, NULL );


}

..my make file looks like this: 
threadtest:	threadtest.o
	g++ -o threadtest threadtest.o -lglut -lGLU -lGL -lpthread

..the program compiles ok, but throws a segmentation fault.  I threw in some debugging printf's and determined that the segmentation fault is thrown for glutCreateWindow.  ...this is what my screen output looks like: 
l8do1@renatus:~/Research/threadtest$ ./threadtest
12345Segmentation fault
l8do1@renatus:~/Research/threadtest$ 

Does anyone have any idea why I would be getting a segmentation fault on glutCreateWindow?  I've never before gotten segmentation fault with opengl programming, and I'm guessing it has something to do with the posix threads, but my google searching hasn't come up with any possible solutions to my problem

---

