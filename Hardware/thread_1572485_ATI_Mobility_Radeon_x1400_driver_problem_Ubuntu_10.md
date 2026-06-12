---
title: "ATI Mobility Radeon x1400 driver problem Ubuntu 10.04"
date: 2010-09-11
forum: Hardware
---

### Post by phguisset on 2010-09-11
I am running Ubuntu on my laptop Toshiba A100-168 PSAAA9. There is a built in graphic card ATI Radeon Mobility X1400.
When I first installed it the graphic display stopped during the  installation but I left it working. Then when the PC restarted Ubuntu  run fine with high resolution. However 2 min after the display went  unstable and the screen started to go black.
Here by using the remote desktop I tried to find solution to my problem by reading forums.
My first thought was to check the free driver was well installed. It was  but actually was not appropriate to have a stable display.
Afterwards I tried to install the proprietary driver ATI 9.3 the latest  from ATI to support my card. But unfortunately I couldn't as the Kernel  of Ubuntu 10.04 do not allow me to run the installation properly.
So I tried to install the fglrx from the depot. And surprisingly after  restarting I have got a stable graphic display in normal resolution.  However I cannot use my the 3D effects of my graphic card.
I tried then to uninstall the free dirver radeon, I restarted and my PC  with only fglrx is in very low resolution. No way to increase it. So I  reinstalled radeon to have a stable environment and a normal resolution.  I would like though to use my 3D capabilities.
I there a know solution to my problem: Why the free driver radeon do not  allow me to have a stable graphic display; as it gets black after 2 min  or less, should I set it up in a particular way...? Alternatively is  there a way to install the proprietary driver 9.3 under Ubuntu 10.04?
Thanks for you help!

---

### Post by Fafler on 2010-09-11
Try this:

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get-upgrade
sudo reboot
```

It gave me a 1000%(!) framerate boost in the Doom 3 timedemo on two different machines, but its still not perfect and KMS seems to screw up powersaving.

More info about the PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

---

### Post by phguisset on 2010-09-11
I tried your solution but I still can't use 3D effects. When I am trying to run them it is said that I have no pilot installed.

---

### Post by Fafler on 2010-09-11
Did it upgrade the packages?

If you have the old version, glxinfo should output something like this:

```
fafler@carbon:~$ glxinfo | grep string
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV530 71C4) 20090101 x86/MMX/SSE2 TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
fafler@carbon:~$ 

```

While the new version should look like this:

```
fafler@carbon:~$ glxinfo | grep string
server glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on RV530
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20
fafler@carbon:~$ 
```

---

### Post by Yellow Pasque on 2010-09-11
> **phguisset said:**
> When I am trying to run them it is said that I have no pilot installed.
What? Can you copy and paste the exact output?

Also, make sure you have fully removed fglrx: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

> Alternatively is there a way to install the proprietary driver 9.3 under Ubuntu 10.04?
No.

---

### Post by phguisset on 2010-09-11
As I said when I remove fglrx, the pc restart, I get the ubuntu logo in high resolution and then the display crashes within a minute. Then I have to use the pc remotelyas my screen gets black For Falfer i ran from the remote PC.
```

phg@ubuntu:~$ glxinfo | grep string
server glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on RV515
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20

```But I cannot use my PC that way, that is why I had again to install fglrx from the depot in order to get a stable display.
The question now is how can I prevent my display from crashing when fglrx is fully uninstalled? Currently to have a system stable and in normal resolution I need to have fglrx and the radeon driver installed at the same time.
> 
                                     
                 *When I am trying to run them it is said that I have no pilot installed.*
                                 What? Can you copy and paste the exact output?After looking for drivers i get the message, "Visual effect could not have been activated".

---

### Post by phguisset on 2010-09-12
Maybe I should add a Xorg.conf to stabilize the radeon driver. However I don't know how to build it.

---

### Post by phguisset on 2010-09-12
For your guide my PC works well with Ubuntu 9.10, so the instability is under 10.01 only. is there any explanation for this ?

---

### Post by Fafler on 2010-09-13
Well, a new (unknown?) error in X.org, the kernel or somewhere else. Do a lot of searching anf, if nothing turns up, file a bug report at launchpad. Or wait it out and use just 9.10 for now.

---

### Post by phguisset on 2010-09-13
on another forum i found someone with the same problem but he doesn't have any solution. 
Do you know how to draw developers attention to such a problem in order to have upcoming version correction the bug ?

---

