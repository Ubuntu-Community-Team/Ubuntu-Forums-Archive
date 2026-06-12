---
title: "Ubuntu hang with my nVidia 6800LE"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by ultima2k on 2005-04-18
I have had really problems that ubuntu hangs when I try to log on och opens the session menu.
At the same time it worked on another of my computers so I knew it was something weird with the hardware.

Just tried using my old half-broken GeForce4600, and it worked!

I currently have clocked, BIOS-modded unlocked all pilelines with the card so I thought it were somthing about that so I made everything default, but still not working.....


What could be the problem?? :S

---

### Post by diebels on 2005-04-18
There are an unresolved bug with nvidia-glx. Try to disable it to see if it's at fault.

---

### Post by ultima2k on 2005-04-19
How do I disable it (I'm yet a linux-n00b :p)

EDIT: feels weird that it works for a friend which has a nVidia 6800U :S

---

### Post by diebels on 2005-04-20
Oh, sorry. I mis-asumed you used nvidia-glx? You can switch video drivers by running "sudo dpkg-reconfigure xserver-xorg" choose nv, vesa or nvidia. Vesa is the slowest and safest, so if you don't get hang with it you can guess that nv or nvidia is causing the hang. Experiment and see what works best for you. To get the nvidia choice, firts:
[ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

I'm currently running with nv since nvidia causes hang on my geforce2 go. 2d performance of nv is almost equal to nvidia but no opengl :(

---

