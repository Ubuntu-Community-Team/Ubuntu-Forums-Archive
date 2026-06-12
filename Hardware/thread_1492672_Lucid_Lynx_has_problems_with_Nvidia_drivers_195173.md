---
title: "Lucid Lynx has problems with Nvidia drivers 195/173 HELP!"
date: 2010-05-25
forum: Hardware
---

### Post by martincasc on 2010-05-25
Hi,

First of all I hope you Understand Me 'cause my English it's not good, I'm from Argentina.

I have this problem since I installed Lucid. I made a clean instalation.

Once installed the system, I've installed nvidia private drivers from Hardware Controller. I've tried the Recommend one looking from Synaptic they are: 195.36.15 version.

I could activate Compiz, the Cube, and a lot of 3D effects, But A Few hours later the performance of Lucid went down, for example: the mouse doesn't run good, it's stop and continue, stop and continue (Spanish, el puntero se trababa) and in general all the 3D effects and Acceleration works very bad.

So I've Decided to use nvidia drivers 173 version;a They work fine, But hours later the effects continue working well except 3D windows, beacuse when I try to use the cube them slow down, it's had some little locks, same with Google Earth, the movment isn't good, is not smooth, Have a little locks that annoy me enough.

I have a Core 2 Duo, 2 gb RAM; Gforce 6600 AGP 8x... Asus motherboard...

I've tried glxgears and i got this:

```
casco@casco-lucid:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
7427 frames in 5.0 seconds
8048 frames in 5.0 seconds
8045 frames in 5.0 seconds
8051 frames in 5.0 seconds
8024 frames in 5.0 seconds
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 39 requests (39 known processed) with 0 events remaining.
```

As you can see, it doesn't show me the FPS, so I tried with glxears -printfps and this command doesn't work on Lucid.

So, I want use the last nvidia drivers available from reps, but they are the 195.36.15 and when I use them, a few hours of runnig Ubuntu, the render or aceleration -whatever- goes down and it's turn imposible to work. Last time I used them, after GDM appear the NVIDIA screen (I never saw that before), and nvidia-settings doesn't work. So i'm using now the drivers 173 and the performance is not perfect like in karmic.

I've been searching for almost a month, and I can't solve this, With karmic evrything was perfect, but now I have not idea what's going on and what can I do for solve this problem.

I need your help, please.

---

### Post by martincasc on 2010-05-26
No one can help me?

---

