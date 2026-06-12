---
title: "Acer and Radeon graphics issues; jumbled display and unable to detect monitor"
date: 2009-10-27
forum: Hardware
---

### Post by WarriorIng64 on 2009-10-27
I am completely new to Linux, and I have Ubuntu 9.04 installed on some older hardware. This desktop computer initially only ran Windows XP SP2, but as it is getting aggravatingly slow, I got a LiveCD and help from some friends in installing Ubuntu to a partition on my second hard drive and turning this into a dual-boot system.

I was pleased to see that Ubuntu boots and seems to run much more quickly than XP does now, but I have been having ongoing problems related to graphics. Before I go any further, I'll list a couple hardware specs below:

AMD Athlon 1.3GHz processor
512MB RAM
ATI Radeon 9200 SE graphics card
Acer X203w monitor

The display initially worked fine, except it was displaying at 1024x768 instead of my monitor's native resolution of 1680x1050. I was also unable to find my monitor under the Display options. My friend, who is much more knowledgeable about Linux than me, suggested that the sluggish graphics performance could be improved by getting better drivers.

I went through a big mess in trying to get graphics drivers installed on this computer. I now know that I cannot use ATI's fglrx drivers, since they cause Ubuntu to not load at all (I just get the Ubuntu loading picture shown twice onscreen in strange colors, surrounded by a large pattern of random bars). I corrected this once by reinstalling from the LiveCD, and my friend helped me avoid the reinstall the second time by showing me how to open the terminal from Recovery Mode and remove the drivers from there. With some of his help, I was able to locate the open-source Radeon drivers ([https://help.ubuntu.com/community/RadeonDriver#Configuring%20X.org](https://help.ubuntu.com/community/RadeonDriver#Configuring%20X.org)) ([https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI);]("https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI%29;") the pages do not seem to have been kept up-to-date along with the files, but I followed whatever steps I could. I mostly tried to stick only with the required steps and follow whatever defaults were given, except where I'd obviously have to use my own information.

We compiled the packages and installed the drivers, then rebooted. Nothing different happened until I went into xorg.conf and modified it to this (the computer was rebooted again afterwards):
```

Section "Device"[INDENT]Identifier "Configured Video Device"
Driver "ati"
BusID "PCI:2:0:0"
Option "XAANoOffscreenPixmaps"
[/INDENT]EndSection

Section "Monitor"[INDENT]Identifier "Configured Monitor"
Option "DPMS"
[/INDENT]EndSection

Section "Screen"[INDENT]Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"[INDENT]Depth 24
Modes "1680x1050" "1024x768"
[/INDENT]EndSubSection
[/INDENT]EndSection

Section "DRI"[INDENT]Mode 0666
[/INDENT]EndSection

Section "Extensions"[INDENT]Option "Composite" "Enable"
[/INDENT]EndSection

Section "ServerLayout"[INDENT]Identifier "Default Layout"
Screen "Default Screen"
[/INDENT]EndSection
```Now I can boot Ubuntu, and the mouse and waiting image for it appear as they should (smaller and correctly-proportioned), but everything else has a severe random flickering/tearing appearance to it. You can see that Ubuntu itself still works just fine behind the mess, and you can very vaguely make out window locations and the desktop background. You can even drag the windows around with the mouse, after correctly guessing their position. However, I can't really do or read anything in Linux if the display is this terrible, and I have only been able to do things from the root terminal in Restore Mode.

I have tried switching the two resolutions listed above to make the 1024x768 one the default again, but I still get the tearing problems while the mouse still appears unaffected by this (but appearing again as it did before the drivers were installed).

I am used to using Windows XP and Windows Vista, and I'm still learning much about Linux while trying to solve these problems, where almost everything is brand-new to me. So far, I have only spent a few days working with this operating system, and I would appreciate any help on how to correct these problems.

---

