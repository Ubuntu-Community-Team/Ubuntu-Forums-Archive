---
title: "How to install openGL drivers on my laptop"
date: 2008-08-25
forum: Hardware
---

### Post by Amurican on 2008-08-25
I have a Dell Inspiron E1505 laptop with an ATI Mobility Radeon X1400 graphics card. I installed Ubuntu with Wubi to dual boot with my Windows XP OS. I'm trying to installed the openGL drivers for a class. My 3d accelerated graphics is currently working with Compiz on my laptop. My question is how would I install the openGL drivers (if possible) and if I do would it change the performance at all?

Thanks

---

### Post by raul_ on 2008-08-25
What do you mean with OpenGL drivers?

---

### Post by Amurican on 2008-08-25
Well I'm taking an openGL programming class. My Professor provided sample code to test on our own machines. After compiling, when I run the program a window is supposed to pop up displaying a basic square, but when I run it a black square flashes (in an instant) on my screen and I get this message:

freeglut (./a.out): Unable to create direct context rendering for window 'A basic OpenGL Window'
This may hurt performance.

My Prof. says my problem might be that I don't have the necessary openGL drivers installed on my graphics card. (I do have the GLUT libraries installed).

Any suggestions??

Thanks for the quick response.

---

### Post by raul_ on 2008-08-25
If you can run compiz, my guess is that you have OpenGL installed. I remember that when I ran OpenGL code I had some compile time flags.

try compiling with &#8211;lSDL -lGL and -lGLU

---

### Post by S.A.A on 2008-08-25
Type the output of:
```
[CODE]glxinfo | grep direct
```[/CODE]

---

### Post by stchman on 2008-08-25
> **Amurican said:**
> I have a Dell Inspiron E1505 laptop with an ATI Mobility Radeon X1400 graphics card. I installed Ubuntu with Wubi to dual boot with my Windows XP OS. I'm trying to installed the openGL drivers for a class. My 3d accelerated graphics is currently working with Compiz on my laptop. My question is how would I install the openGL drivers (if possible) and if I do would it change the performance at all?

Thanks

Enable the restricted driver.

I also believe Mesa(open source version of OpenGL) is installed by default.

---

### Post by Amurican on 2008-08-25
I'm assuming you meant type that in a terminal. I did and it gave me this:

direct rendering: No (LIBGL_ALWAYS_INDIRECT set)


Any thoughts on what that means or what I should do??

Thanks

---

### Post by Amurican on 2008-08-25
I have already enabled all the drivers in under system> administration> hardware drivers. Is that what you mean?

---

### Post by Amurican on 2008-08-25
> **raul_ said:**
> If you can run compiz, my guess is that you have OpenGL installed. I remember that when I ran OpenGL code I had some compile time flags.

try compiling with &#8211;lSDL -lGL and -lGLU
When I compile with those I get this:

/usr/bin/ld: cannot find -lSDL
collect2: ld returned 1 exit status


???

---

### Post by raul_ on 2008-08-25
> **Amurican said:**
> When I compile with those I get this:

/usr/bin/ld: cannot find -lSDL
collect2: ld returned 1 exit status


???

That means you don't have SDL installed. My gues is that you'll need to install it later, but I don't think you need it for displaying a square. Try without the -lSDL

---

### Post by Amurican on 2008-08-25
> **raul_ said:**
> That means you don't have SDL installed. My gues is that you'll need to install it later, but I don't think you need it for displaying a square. Try without the -lSDL
If I compile without out it I ge the same response as before:

freeglut (./a.out): Unable to create direct context rendering for window 'A basic OpenGL Window'
This may hurt performance.


I'll try installing SDL and give that a go.

---

### Post by stchman on 2008-08-25
> **Amurican said:**
> I have already enabled all the drivers in under system> administration> hardware drivers. Is that what you mean?

Yes, the restricted drivers(fglrx) install openGL.  You are set.

---

### Post by Amurican on 2008-08-25
> **Amurican said:**
> If I compile without out it I ge the same response as before:

freeglut (./a.out): Unable to create direct context rendering for window 'A basic OpenGL Window'
This may hurt performance.


I'll try installing SDL and give that a go.
I installed SDL with:

 sudo apt-get install libsdl1.2-dev

It compiled fine, but when I ran the program it gave me the same results as before.

---

### Post by raul_ on 2008-08-25
The thing is, that message is just a warning, it doesn't prevent your code from running. The thing you should be worrying is about your window not showing. In fact, you shouldn't be worrying at all, because your code is correct, and you can see the square. But by default, running opengl code, just runs the program, and the window closes when the program is finished. Since all your program does is drawing (and showing) a square, it does that, and then exits. 

You can verify this by adding (for example) a line with

```

sleep(10);

```

before the end of your code.
I remember that there was an option to keep the window open, but I can't remember which. I thought it was some of those flags, but quite honestly, it was stupid. Try the sleep thing.

---

### Post by S.A.A on 2008-08-26
Read this forum: [http://ubuntuforums.org/showthread.php?t=246746](http://ubuntuforums.org/showthread.php?t=246746)

---

