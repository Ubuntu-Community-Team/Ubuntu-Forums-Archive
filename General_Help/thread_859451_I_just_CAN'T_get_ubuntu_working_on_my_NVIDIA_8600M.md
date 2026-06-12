---
title: "I just CAN'T get ubuntu working on my NVIDIA 8600M GT!"
date: 2008-07-14
forum: General Help
---

### Post by Duranxl on 2008-07-14
Hi all.
I'm having a hard time getting my gfx driver to work on my 8600M GT.

What i've tried:

**1) Install via proprietary drivers (hardware drivers).**

Result: 
It installs nvidia-glx-new and upon reboot i have low-graphics-mode with colors all over the place (can't see or click the buttons).
I tried sudo apt-get install nvidia-glx-new but i get the infamous lib32 error. (same goes when i try to uninstall it)

**2) Install via [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)**

Now it only says 8700M GT so that's the one i took (should i pick another one:confused:)
I did the whole sudo sh NVIDIA*.run thing and it installed successfully (though i got some lib32 error again)

Result:
Once again I get low-graphics mode, but this time i can see the buttons and press continue.
Configuring the screen won't change anything.
I can't go to nvidia-settings because it says im not on NVIDIA X server. I did "sudo nvidia xconfig" and restarted X server to no avail.
I also tried going to "graphics and screen" in the main menu.
But after selecting the right resolution (instead of 800x600) it says: "users must log-off to change resolution"
Logging off will result in Low-graphics mode again.

**3) Install via EnvyNG**
Result:
All goes well, it says it's installed (auto-mode) but upon reboot i still have low-graphics mode.
I uninstalled the drivers via EnvyNG and i'm back without NV drivers but at least now i have 1280x800

64bit, btw
Sorry for the big story, please help:(


-squishy

---

### Post by Duranxl on 2008-07-14
bump

---

### Post by Duranxl on 2008-07-14
Maybe it's because it says it can't find a the appropriate nvidia kernal?
I also get this error message at boot.
This is the one i installed:
NVIDIA-Linux-x86_64-173.14.09-pkg2.run

---

### Post by damis648 on 2008-07-14
That's wierd... mine works fine. :confused:

---

### Post by Duranxl on 2008-07-14
```
wp@wp-laptop:~$ sudo apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-new is already the newest version.
```


It's installed, but it won't work!!
What's with the kernel thing?
Do I have the wrong linux-restricted-modules:confused::confused::confused::confused:
:(

edit:
Kernel version
Linux wp-laptop 2.6.24-19-generic #1 SMP 
Installed linux-restricted-modules: 2.6.24.19.21
Seems it matches!:S

---

### Post by Duranxl on 2008-07-14
bedtime bump

---

### Post by Jim! on 2008-07-14
Is your system up to date? Also when you installed the first time "1) Proprietry Drivers" did you do this via System>Administration>Hardware Drivers?

---

### Post by jonian_g on 2008-07-14
You might try this:

Open synaptic and completely remove everything that starts with nvidia-glx-*

Uninstall the driver that you downloaded from the nvidia website. You must have the file and follow the same procedure when you installed it and type sudo sh NVIDIA* --uninstall

Reboot and install the driver with envy.

More info:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Old Installs Conflicting](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Old Installs Conflicting)

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by Duranxl on 2008-07-15
> **jonian_g said:**
> You might try this:

Open synaptic and completely remove everything that starts with nvidia-glx-*

Uninstall the driver that you downloaded from the nvidia website. You must have the file and follow the same procedure when you installed it and type sudo sh NVIDIA* --uninstall

Reboot and install the driver with envy.


That seemed to work!
I got the NVIDIA logo at startup and nvidia-settings worked for the first time.
However, my 2nd screen (which i use all the time) doesn't work.
I set it up via nvidia-settings but it causes LOW-GFX-MODE again.
Setting it up via "screens and graphics" also results in LOW-GFX-MODE
-.-
:(

I did nvidia-xconfig the 1st time and it fixed it again, but that doesn't seem to work anymore:(

edit:
So I deleted xorg.conf and ran nvidia-xconfig again and now it's working again.
I got my dual monitor working too but everything is a pain in the ***
Resolution seems correct 1/10 reboots and when i close my laptop lid the dualscreen turns itself off
Apparently it thinks my 2nd screen is my laptop screen..
Any tips/progs to get it fixed?

---

### Post by jonian_g on 2008-07-15
Weird...

I forgot, on my previous post, to tell you to delete the xorg.conf before rebooting.
So what you can try is, remove the driver with envy, delete xorg.conf, reboot and install again with envy.

Don't use nvidia-xconfig, setup everything with nvidia-settings.

I know all this is a pain in the a**, but woth trying.

---

### Post by jonian_g on 2008-07-15
Maybe you can't change the resolution on your second screen because the model is not recognized. To recognize it try this:

Open a terminal and type

sudo displayconfig-gtk

Click where it says "Model" and at the screen that comes up click add and locate the *.inf file in the cd-rom that came with your monitor. Then select you monitor model and press ok.

Don't set your resolution from here. Better do it from nvidia-settings.

---

