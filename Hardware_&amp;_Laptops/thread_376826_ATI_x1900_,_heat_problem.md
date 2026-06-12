---
title: "ATI x1900 , heat problem"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by y2kprawn on 2007-03-05
Hi All,

I have managed to get the ATI driver working with Envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
on my HP nx9420 . It has a x1900 with 256MB ram, also 2GB ram and Dual core 1.8GHZ CPU.
The problem I am having now is that the CPU fan is on all the time when I boot into Ubuntu, this only happened after I installed the ATI drivers. 
Its very annoying, also the battery drains very quickly. 

Has anyone had the same problem with Ubuntu on a laptop ?
Its a little worrying.

---

### Post by y2kprawn on 2007-03-05
funny story , if i type the command aticonfig --set-powerstate 1 the fan seems to return to normal speed. Please if anyone has this problem, let me know how to resolve it, i am soooo close to replacing windows !!!! I like the freedom but need the whole part to work on this partitiion. 
I still will keep XP for XNA and DirectX as I am a student of video games development, and as good as it is , OpenGL does not really cut it!!

---

### Post by lodp on 2007-03-06
well, seems like you found the solution already -- that command you typed needs to be executed every time the system starts.

i can only tell you how to do that for kubuntu:

create a file called atipowerstate in ~/.kde/Autostart
> 
nano ~/.kde/Autostart/atipowerstate

and fill in the following:
> 
#! /bin/sh -e
aticonfig --set-powerstate=1

then make it executable:

[CODE]chmod a+x ~/.kde/Autostart/atipowerstate/CODE]

and you're set...

i'm sure there's an easy way to do it in gnome, too..

---

