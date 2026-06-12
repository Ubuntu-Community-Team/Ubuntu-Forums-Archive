---
title: "version 11.04"
date: 2011-06-12
forum: Hardware
---

### Post by Mr JB on 2011-06-12
I am a new Ubuntu user, but I like it so far. I do have a issue that is driving me crazy.  I installed this version on my Macbook Pro using bootcamp and VMware Fusion. In Fusion, I could not get the VMware tools to download. In both bootcamp and VMware, the OS installed. But at the end of the install, Ubuntu would not run, saying that my hardware did not support Unity. I installed it on my desktop as a stand alone OS but got the same results. I tried to install it on my laptop running W7 with Virtual Box, and the same thing happened. I tried about 3 or 4 different methods of installing 11.04 that I found online, but after the install, I still got the Unity error message. What is it with this version having to run with Unity. I don't care if it doesn't have Unity. Version 9.10 runs great and doesn't give me this issue.

---

### Post by garvinrick4 on 2011-06-12
VMware will run 11.04 gnome-classic but not Unity interface and use 32-bit it only uses one of your processors.

---

### Post by Mr JB on 2011-06-12
Thankyou: Does the gnome version have to run in VMware, or can it be installed as a stand alone OS, or with Virtual box?.

---

### Post by garvinrick4 on 2011-06-12
After install using VMware when at boot screen click on user and at bottom will be a button
to make choice of what you want to boot set it at gnome-classic and then log-in.

If you want to run as a partition install put in your install cd and boot off of it and choose
Try Ubuntu when it boots up open a terminal ctrl/alt/t and copy and paste this the results
says all yes then you can run Unity in a regular partition install. Unity will just not run in
a VMware install.
```
/usr/lib/nux/unity_support_test -p 
```Above is a test just to see if Unity interface is supported on your Machine.
There is Unity interface, Unity 2D interface and Gnome-classic available on install.
Gnome classic and Unity 2D run on just about anything you throw at it. Unity runs on
most machines, some older models not.

---

