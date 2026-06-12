---
title: "Ubuntu 9.04 Nvidia Quadro FX 3700 &quot;Failed to initialize the NVIDIA Kernel module&quot;"
date: 2009-09-09
forum: Hardware
---

### Post by The_Jars on 2009-09-09
Hi, I started using Ubuntu a few months ago so I know a few important things but am not fully fluent with it. I've been trying for a while now to get my graphics card to work on Ubuntu. I am able to get the correct resolution but unable to use any visual effects. 

When I boot I get an error message saying, among other things "Failed to initialize the NVIDIA Kernel module" and "Error: Screen(s) found but none have a usable configuration."

I have been struggling with this for a while now and have tried many things. I have used Envy, which doesn't work. 
I have ensured that make, gcc, pkg-config, xserver-xorg-dev, as well as my needed linux-headers and build-essential are all installed. But still the problem persists. 
I have tried to manually install drivers which I assume are the correct version, but still nothing. 
If I have posted in the wrong area, not provided enough information, or otherwise, please let me know and I will take the steps to rectify my mistake.

---

### Post by Fafler on 2009-09-10
> I have tried to manually install drivers which I assume are the correct version, but still nothing

Did you get any errors while doing so? Like incorrect gcc version or something?

The X server falls back to the generic nv driver, which doesn't support OpenGL used for visual effects, when the binary nvidia driver doesn't work. The FX 3700 is a nice card, BTW.

---

### Post by The_Jars on 2009-09-10
> Did you get any errors while doing so? Like incorrect gcc version or something?

During installation, it says: "No precompiled kernel interface was found to match your kernel." 
Then it asks to download one from the website, then it fails to connect. After that, the installation tries to compile one on its own and the installation completes saying it was successful. However, the problem persists.

---

### Post by Fafler on 2009-09-10
That's weird. Try CTRL + ALT + F1 to get to a console, login and:
*NOTE: This ends your corrent X session, so please save and all that before you start*

```
sudo /etc/init/gdm stop
sudo rmmod nvidia
sudo insmod nvidia > dmesg.txt
sudo X -probeonly 2> probeonly.txt
sudo /etc/init/gdm start

```

ALT+F7
Login, get back and attach dmesg.txt and probeonly.txt here.

---

### Post by The_Jars on 2009-09-10
When performing "rmmod nvidia" I get "Error: Nvidia does not exist in /proc/modules
When performing "insmod nvidia" I get "Error: Can't read 'nvidia': No such file or directory
However, here is the probeonly.txt

My apologies for the problems

---

### Post by Fafler on 2009-09-10
For insmod nvidia, try modprobe nvidia instead. If that don't work, then find /lib/modules | grep nvidia and if theres a nvidia.ko matching your kernel. If there is, try insmod /complete/path/to/module/nvidia.ko. Do a dmesg aftarwards and post anything relevant.

Probeonly.txt didn't really contain any info. That's probably also my fault. Try attaching /var/log/Xorg.0.log instead.

---

### Post by The_Jars on 2009-09-10
When performing insmod on the nvidia.ko I got this error: "-1 Invalid Module Format"
Which part of the Xorg.log file do I need to show? The entire thing is too large to attach.

---

### Post by Fafler on 2009-09-10
Just the part related to the problem ;-)
The parts mentioning nvidia, and a few lines before and after. But i'm not even sure it's going to give us any usefull information as it's not going to work, unless the nvidia module is installed.

I don't have any more ideas right now. Maybe someone else has one?

---

### Post by The_Jars on 2009-09-10
Thank you for the help, I appreciate your patience especially in the face of my ignorance. 
Here is some of the text from Xorg.log

---

### Post by The_Jars on 2009-09-10
Bump

---

### Post by The_Jars on 2009-09-10
Surely someone can help me with this?

---

