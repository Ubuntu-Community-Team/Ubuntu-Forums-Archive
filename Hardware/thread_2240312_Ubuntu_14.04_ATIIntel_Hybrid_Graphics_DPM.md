---
title: "Ubuntu 14.04 ATI/Intel Hybrid Graphics DPM"
date: 2014-08-19
forum: Hardware
---

### Post by anchitsingh9 on 2014-08-19
Hi,
I have a Dell Inspiron 3521 with hybrid ATI/Intel graphics. (AMD Radeon 7670M / Intel HD 4000)
I am using Ubuntu 14.04 with open source drivers for graphics. (xserver-xorg-video-ati)
I read that Ubuntu 14.04 with the linux kernel version 3.13 supports auto switching between graphics and dynamic power management. Is it correct?
Anyway, if it is true, I dont think that it is working in my system :(, because fan runs constantly and battery backup is less than 2 hours.

lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] (rev ff)

What should I do??
Is there any hope that this gets fixed in future kernels..?

---

### Post by anchitsingh9 on 2014-08-21
So no one knows..??

---

### Post by Bashing-om on 2014-08-21
anchitsingh9; Sorry;

It is considered bad form to make a response " I do not know" as it adds nothing to a resolvement.
As there is no other response though, maybe I can give a direction that might help:
see:
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) <- special case for Intel/AMD hybrid graphics
[https://github.com/beidl/amd-indicator](https://github.com/beidl/amd-indicator) <- This indicator applet allows owners of laptops with AMD/Intel hybrid graphics capabilities to easily switch between the graphics cards without the need of running CCC or terminal commands.

[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355) 
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphicshttp://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphicshttp://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics) <-  The mega thread AMD/Intel Hybrid Graphics works

As you are aware hybrid graphics is a problem in linux as the OEMs offer little support for their hardware to linux. Our developers are working hard on the problem.
Maybe these work-a-rounds can offer some relieve.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by anchitsingh9 on 2014-08-22
Thank you Bashing-om, I know that the developers are really working hard.
I am in no hurry for a solution, I just needed info on the future of hybrid graphics in linux.
I will try to find the answers in the links you provided.

---

### Post by Bashing-om on 2014-08-22
anchitsingh9; No real sweat then;

Wheewhhh 

The 1st link and launch pad will be good places to start. Not really kept up with things on that front, but these are latest I am presently aware of.

As I find different, I will update in this thread.

[INDENT][INDENT][INDENT]we all want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by ivan-cuadros-chavez on 2014-08-25
Hello
I made a tutorial in [Optimizar DELL INSPIRION 15R 5521]("http://www.taringa.net/posts/linux/18073964/Optimizacion-de-energia-Dell-Inspirion-5521.html") this is in Spanish. Maybe, it can help you and the batery may take more hours . In my case my battery consumed 14Watts and after configuring, now consumes 6-8watts.

Sorry my English is bad

---

### Post by anchitsingh9 on 2014-08-26
thanks Ivan, but the problem is caused due to constantly running fans, which is a driver problem probably.
Anyone else having a similar problem may see this :

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/1304912](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/1304912)

and also

[http://allsoftwaresucks.blogspot.in/2013/11/using-hybrid-graphics-laptop-on-linux.html](http://allsoftwaresucks.blogspot.in/2013/11/using-hybrid-graphics-laptop-on-linux.html)

---

### Post by anchitsingh9 on 2014-12-23
There has been a little development.
Recently, my machine received some library updates which also included > xserver-xorg-core
I have been observing my machine since, and the problem of fans running constantly has vanished, atleast for now.
Can someone else who have had similar problems confirm this please??

---

### Post by Bashing-om on 2014-12-23
anchitsingh9; Hey hey: Good news, indeed.

> **anchitsingh9 said:**
> There has been a little development.
Recently, my machine received some library updates which also included 
I have been observing my machine since, and the problem of fans running constantly has vanished, atleast for now.
Can someone else who have had similar problems confirm this please??

We see our developers are hard at work .

[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

### Post by anchitsingh9 on 2014-12-24
Hey Bashing-om, I really appreciate the work of the developers.
I thought that the problem will only be fixed in the next hardware-enablement-stack, but it seems to have been fixed(partially atleast).
I have made more observations and fans do not run constantly on AC power as it used to do earlier.
But whenever there is a graphic intensive work (like playing a video), the fans again start to run constantly.
I am sure this will get fixed too.
Though, I will be really relieved if more and more people with the same problem, report similar observations as I have.

---

