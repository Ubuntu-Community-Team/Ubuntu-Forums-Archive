---
title: "DELL Inspiron e1405: CANNOT INSTALL!!!"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by dCL on 2007-03-27
Hi. I'm pretty new to Linux in general, so my questions could look a little stupid :)

I have DELL Inspiron e1405 with Mobile Intel 945GM Express integrated video and 14'' WXGA+ 1440x900 display. The problem is simple - The Instalation would not start. I've tried both 6.10 desktop and 7.04beta desktop versions and I get the same error (this is quoted from the 6.10 instalation):

**"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view X server output to diagnose the problem?".**

This is what X server returns:

[B](WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) I810(0): No video BIOS modes for chosen depth.
(EE) Screen(s) found but none have a usable configuration.

Fatal server error:
no screens found[/B]

After that it offers me to view the detailed output and finally informs me that the X server is now disabled and I have to restart GDM when it is configured correctly. And because I don't know anything :) I don't know how to configure it.

Could anyone help please?

Thanx

---

### Post by WetWired on 2007-03-27
Well, configuring it is the easy part. It should drop you to a terminal after a while of sitting, and if not, hit ALT+F1 and it'll give you a terminal. After that, you can do something like sudo vi /etc/X11/xorg.conf. That will open your X configuration file (xorg.conf) in an editor (vi), as root (sudo), kinda. Anyway, once you're in there, you can start your editing.

You should run, in that terminal, the following command.

lspci -v

And find your video card section, and give us that information, it'll help us figure out your problem a little easier.

Once you've done that, we can start trying to find out what's wrong with it. I would hazzard and guess and say that xorg.conf is pointing to the wrong BusID for your video card. Although, I could be wrong. I'm not exactly a linux expert.

---

### Post by dCL on 2007-03-29
Thanx for the reply :)

Here's what my xorg.conf has regarding the video/monitor sections:

[B]Section "Device"
         Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
         Driver          "i810"
         BusID           "PCI:0:2:0"
EndSection

Section  "Monitor" 
         Identifier      "Generic Monitor"
         Option          "DPMS"
EndSection

Section "Screen"
         Identifier      "Default Screen"
         Device          "Intel Corporation Mobile Integrated Graphics Controller"
         Monitor         "Generic Monitor"
         Default Depth   16
         SubSection "Display"
                 Depth           1
                 Modes           "1440x900"
         EndSubSection
         SubSection "Display"
                 Depth           4
                 Modes           "1440x900"
         EndSubSection
         SubSection "Display"
                 Depth           8
                 Modes           "1440x900"
         EndSubSection
         SubSection "Display"
                 Depth           15
                 Modes           "1440x900"
         EndSubSection
         SubSection "Display"
                 Depth           16
                 Modes           "1440x900"
         EndSubSection
         SubSection "Display"
                 Depth           24
                 Modes           "1440x900"
         EndSubSection
EndSection[/B]

And this is what the command lspci -v returns, again, regarding the video/monitor:

[B]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 01d8
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at eff00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at eff8 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at efec0000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Dell Unknown device 01d8
        Flags: bus master, fast devsel, latency 0
        Memory at eff80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>[/B]

If you need something else, please let me know :) Thanx again.

---

### Post by dCL on 2007-03-29
looks like nobody can help :)

---

### Post by Pragmatik on 2007-03-29
I had the same problem on my Dell desktop, but trying 6.06 worked just fine -- even recognized my old Dell multimedia non-usb keyboard.

---

### Post by dCL on 2007-03-29
I tried but unfortunately this is not working for me... Still the same problem.

---

### Post by Pragmatik on 2007-03-30
D'Oh!  I can find guides for other distros and that lappy model, but not Ubuntu.  Sorry:(

---

### Post by dCL on 2007-03-30
thanx anyway :)
Nevermind, I'll try it on my desktop these days.

---

### Post by WetWired on 2007-04-12
Sorry for the delay, I've been moving. Now, I'm not the greatest person to be helping, as I'm not THAT great with Linux yet, but if I had to hazard a guess, I'd say since you've only got one screen resolution listed, it may not be supported unless your video card drivers are installed and working properly. Try adding some more resolutions - common ones like 800x600 and 1024x768. See if that helps. If not, come back, and we'll try some more things.

---

### Post by heynow on 2007-04-18
the problem is the screen resolution all you need to do is when xserver crashes during install on edgy hit ctrl+alt+F2 and takes to you cmd line....now you'll need to be connected directly to the net via an ethernet cable because like most dells the wireless card has a broadcom chipset and those drivers dont come standard(if you run into that issue look at fwcutter) but edit you sources.list file

code:
~$ sudo nano /etc/apt/sources.list 
and uncomment the universe repositories
then overite the file by pressing ctrl+o
and exit with ctrl+x

then install the patch 
code:
~$ sudo apt-get install 915resolution

bingo thats it now just start xserver and continue install
code:
~$ sudo startx

NOTE!!!!!!!!!!!!!!!!!!!

AFTER INSTALL FINISHES AND IT REBOOTS XSERVER WILL CRASH AGAIN 
JUST REPEAT ABOVE PROCESS AND IT WILL WORK FINE

---

### Post by Chjazz on 2007-04-23
I have the same laptop that you have - I am running Ubuntu 6.06 and dual-booting with Windows XP Pro without a problem! 

I am not a Linux expert either, but have been using Ubuntu on my E1405 maybe a little less than 4 months, this computer is 5 months old.

I remember that I had an issue similar to yours when trying to install Ubuntu 5.0 and had quite a few other issues.

A Dell tech support rep clued me into this fact:

I had to re-format my computer to remove the Dell "MediaDirect" feature. 

It may interfere with Ubuntu or any other OS you may want to dual boot with because the computer "thinks" it is already "dual-booting" and will not accept a "third" OS

When I re-formatted Windows I also left 35GB unformatted (about 1/3 of my hard-drive) so Ubuntu would easily find a home

Worked great, no more errors, and does not affect your Dell warrenty!

Hope that helps!

Chjazz

P.S. By the way you may have to call Dell to get a Windows XP disk if you currently have a "restore" disk - they may be two different disks!

I had to call them for this disk....

---

