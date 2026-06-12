---
title: "Video driver not working Ubuntu 12.04 32bit Desktop"
date: 2013-04-22
forum: Hardware
---

### Post by SteffJay on 2013-04-22
Hello all. I have installed the above distro. However, when booting, all i have is a flashing screen !!! The processor is an AMD Athlon LE-1640 and SiS Mirage Graphics Driver.

First question: How do i stop from booting into the desktop environment to get the command line?

Second: What syntax do i use to drop the resolution to a lower one?

Third: If that is not possible; can i SSL into the OS from another pc to correct the problem as root?

Thanks in advance.

---

### Post by mörgæs on 2013-04-23
If there is nothing of value in the system I would erase it all and do a fresh install of Lubuntu 13.04. Ubuntu is too heavy for a SIS Mirage.

---

### Post by SteffJay on 2013-04-23
Thanks for your reply  mörgæs. I will do as suggested. Can i still use LAMP on this system? As i would like to do video streaming if at all possible. Thanks in advance.

---

### Post by mörgæs on 2013-04-23
You can use all the normal applications including LAMP. 

Best is to test Lubuntu in a live boot before installing, as not all SIS cards play nice with Buntu.

---

### Post by SteffJay on 2013-04-23
Unfortunately, this is doing the exact same thing as 12.04 and 12.10 :(

Thanks for your help anyway.

---

### Post by mörgæs on 2013-04-23
Can you access the system through recovery mode?

---

### Post by Yellow Pasque on 2013-04-23
You're hitting this bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464)
> The best thing for SiS users right now is to install Ubuntu 12.04.1 LTS: [http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)
Once you have 12.04.1 installed, make sure you DON'T install the xserver-xorg-lts-quantal package, or you'll hit this bug again. You need to stick with xserver-xorg-lts-precise.

Press Ctrl+Alt+F1 to see if you can get to terminal or try recovery mode as mörgæs suggested. If you can't get to a terminal, then a fresh install of 12.04.1 is probably the best route
Once you get to the terminal, create/modify your /etc/X11/xorg.conf to look like:
```
Section "Device"
        Identifier      "Configured Video Device"
	Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Alternatively, you could keep the SiS driver to do modesetting, but you have to turn off the 2D acceleration to stop X from crashing.
```
Section "Device"
        Identifier      "Configured Video Device"
	Option         "NoAccel" "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by SteffJay on 2013-04-23
> **mörgæs said:**
> Can you access the system through recovery mode?

Thanks for your reply. No mörgæs, I could not do anything as the screen was flashing on and off (mainly off), so I could not even get a command line in a terminal.

---

### Post by SteffJay on 2013-04-23
> **Temüjin said:**
> You're hitting this bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464)


Press Ctrl+Alt+F1 to see if you can get to terminal or try recovery mode as mörgæs suggested. If you can't get to a terminal, then a fresh install of 12.04.1 is probably the best route
Once you get to the terminal, create/modify your /etc/X11/xorg.conf to look like:
```
Section "Device"
        Identifier      "Configured Video Device"
	Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Alternatively, you could keep the SiS driver to do modesetting, but you have to turn off the 2D acceleration to stop X from crashing.
```
Section "Device"
        Identifier      "Configured Video Device"
	Option         "NoAccel" "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

**Temüjin** you are a diamond !!! :P Thank you very much. It is running perfectly now !!!

---

