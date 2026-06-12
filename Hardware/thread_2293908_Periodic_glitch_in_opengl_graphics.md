---
title: "Periodic glitch in opengl graphics"
date: 2015-09-08
forum: Hardware
---

### Post by sperka on 2015-09-08
I have an application used for rendering graphics at high frame rates using ubuntu. My application derives its OpenGL context using glX. Normally I run using a bare X server (no dm OR wm) and run my application using a full screen, double-buffered drawable. For several years we've run successfully, generating 100Hz frame rates under Ubuntu 6. Fast forward to today, and I must update the version of ubuntu to get graphics drivers for more modern video cards. 

Here is the problem: All my applications suffer from a periodic glitch - the periodicity is VERY steady - in its rendering. A simple application (below) using GLFW3 and simple opengl illustrates the problem. The application _should_ display a column of dots (GL_POINT) moving smoothly across the screen from left to right. What we observe (confirmed by high speed photography) is that each dot follows a pattern like this as it moves across the screen:

frame 0: Display at position x
frame 1: position x+step
...
frame n:       x + n*step
frame n+1:   x + n*step  (same frame is repeated)
frame n+2:   x + (n+2)*step  (frame n+1 never displayed)
...

There is a single frame which is repeated, and then it "catches up" after the repeat. The net effect is that about twice per second you see a "hitch" in the dots. Its easy to observe that the motion is not smooth. 

It is a maddening bug, which I cannot track down! Here is a list of things I've eliminated:

**tearing**: Nope. Timing measurements indicate ALL frames are displayed without missing any buffer swaps. We sync to vblank in all cases. (We do this type of thing a LOT and its extremely important to our work). Tearing would be obvious with my test application because you'd see the tear in the column of dots moving across the screen. 

**video card**: Happens with nvidia, ATI/AMD cards, different driver versions (nvidia, radeon, fglrx; nouveau doesn't do 3d acceleration)

**Ubuntu version**: happens with 14.04 and 15.04

**Monitor**: This happens with CRT, LCD, and a high speed DLP projector we use. 

**Frame rate**: happens at all EDID frequencies of the tested monitors, from 60Hz - 120Hz. 

**Software**: The software I've developed relies on the OpenSG Scenegraph library; the test program below doesn't use it, instead uses GLFW3 to simplify window creation at full screen.


I've found quite a few references to similar problems of tearing, but few of the references have the *periodic* glitch I've described. Some comments suggest the X "COMPOSITE" module, but my attempts to disable it have not helped (the X log isn't helpful, as it will say the module is disabled, but later will show a line indicating the COMPOSITE module is being initialized. I am not sure what that means). 

I am searching for ideas. Has anyone seen effects like this? Does anyone else (game developers, e.g.) demand frame-by-frame control of their output, and also have the means to verify that an effect like what I describe is NOT happening? 

Thanks! 

Dan


Here is a sample program which will produce the effect on my machine. I'm sorry it requires GLFW3; I had to build it for trusty as the repos have GLFW2. I can post another version without glfw later today...


```

#include <iostream>
#include <stdlib.h>
#include <GLFW/glfw3.h>

using namespace std;

int f_w, f_h;
int f_pointsize;
int f_separation;
int f_stepsize;
int f_step = 0;  // incremented each time through display()


static void error_callback(int error, const char* description)
{
	cerr << description << endl;
}

static void key_callback(GLFWwindow* window, int key, int scancode, int action, int mods)
{
	if (action != GLFW_PRESS) return;
	switch(key)
	{
	case 'P':
		if (mods & GLFW_MOD_SHIFT)
			f_pointsize++;
		else
			if (f_pointsize > 1) f_pointsize--;
		break;
	case 'S':
		if (mods & GLFW_MOD_SHIFT)
			f_stepsize++;
		else
			if (f_stepsize > 1) f_stepsize--;
		break;
	case 'N':
		if (mods & GLFW_MOD_SHIFT)
			if (f_separation < f_h/2) f_separation++;
		else
			if (f_separation > 10) f_separation--;
		break;
	case 'Q':
		glfwSetWindowShouldClose(window, GL_TRUE);
		break;
	}

   	cerr << "pointsize " << f_pointsize << " stepsize " << f_stepsize << " separation " << f_separation << endl;

}

void display()
{
	int x = (f_stepsize * f_step) % f_w;
	int npts = f_h / f_separation;
	if (npts == 0) npts = 1;

	glClear(GL_COLOR_BUFFER_BIT);
	glMatrixMode(GL_MODELVIEW);
	glLoadIdentity();
	glPointSize(f_pointsize);

	glBegin(GL_POINTS);
	for (int i=0; i<npts; i++)
		glVertex2f(x, (i+0.5)*f_separation);
	glEnd();
	glFlush();
	f_step++;
	if (f_step % 500 == 0)
	{
		double sec = glfwGetTime();
		cerr << "Frames " << f_step << " time " << sec << " rate " << (double)f_step/sec << " FPS" << endl;
	}
}


int main(int argc, char **argv)
{
    GLFWwindow* window;

	if (argc < 6)
	{
		cerr << "usage (all params int): render-dots width height pointsize separation stepsize" << endl;
		return -1;
	}
	else
	{
		f_w = atoi(argv[1]);
		f_h = atoi(argv[2]);
		f_pointsize = atoi(argv[3]);
		f_separation = atoi(argv[4]);
		f_stepsize = atoi(argv[5]);
		cerr << "w " << f_w << " h " << f_h << " pointsize " << f_pointsize << " separation " << f_separation << " stepsize " << f_stepsize << " timerMS " << endl;

	}

    glfwSetErrorCallback(error_callback);
    if (!glfwInit())
        exit(EXIT_FAILURE);
    window = glfwCreateWindow(f_w, f_h, "Simple example", NULL, NULL);
    if (!window)
    {
        glfwTerminate();
        exit(EXIT_FAILURE);
    }
    glfwMakeContextCurrent(window);
    glfwSwapInterval(1);
    glfwSetKeyCallback(window, key_callback);
    glfwSetTime(0.0);
    while (!glfwWindowShouldClose(window))
    {
        int width, height;
        glfwGetFramebufferSize(window, &width, &height);
        glViewport(0, 0, width, height);
        glMatrixMode(GL_PROJECTION);
        glLoadIdentity();
        glOrtho(0, f_w, 0, f_h, -1.0, 1.0);

        display();

        glfwSwapBuffers(window);
        glfwPollEvents();
    }
    glfwDestroyWindow(window);
    glfwTerminate();
    exit(EXIT_SUCCESS);
}


```

---

