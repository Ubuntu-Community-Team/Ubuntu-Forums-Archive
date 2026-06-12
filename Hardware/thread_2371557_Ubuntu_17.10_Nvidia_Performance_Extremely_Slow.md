---
title: "Ubuntu 17.10 Nvidia Performance Extremely Slow"
date: 2017-09-15
forum: Hardware
---

### Post by lakerssuperman2 on 2017-09-15
I'm running Ubuntu 17.10 on my Intel graphics laptop and my Radeon rigs with great success, but on my main desktop with Nvidia graphics Gnome runs terribly.  Gnome 3.26 seems faster than Gnome 3.24 and 3.24 used to run ok ish on this rig but now not so.  Is anyone else experiencing sluggishness and major stuttering with animations on Nvidia graphics?  Thanks.

---

### Post by Frogs Hair on 2017-09-15
Hello and Welcome

Post the output of the command below in code tags. Highlight the terminal text after pasting in the reply window and select the # symbol from the tools for code tags. I can tell you that my Nvidia card requires a proprietary driver on all versions after 16.04.

```
lspci 
```

---

### Post by lakerssuperman2 on 2017-09-15
I should have mentioned that I'm running with the proprietary drivers on a GTX 660Ti.  All is running correctly up to and including 3d games.  Just the DE is slow.

---

### Post by mc4man on 2017-09-15
Are you using a Wayland or xorg session & at the login screen are both or just one available?

---

### Post by dino99 on 2017-09-15
is the hardware acceleration used ? Should be usefull to get informations from htop and/or system monitor applet

---

### Post by ventrical on 2017-09-16
Could have jockeyed to llvm-pipe.

I had the problem a while back when I installed Dash2Dock. It affected the unity7 DE. Removing Dahs2Dock did not fix problem.

Regards..

---

### Post by brandex007 on 2017-10-02
Same here, I have a GTX 660. Since upgrading to Ubuntu 17.10, it's been sluggish.

---

### Post by markackerman8@gmail.com on 2017-10-05
10 years with Ubuntu/variations, been loving Ubuntu-Gnome for 2 years, and now this may well be fixed as its' only beta 
BUT ...

BUT ... It is ridiculously slow
Slow to boot
Slow to log in
Slow to Log out
Slow to launch ANY APP
Download speed is fine (wait going to check - nope Super Fast as it should be)
Suspend not working properly
Extensions not working well
Wayland not working at all
Display not remembering its Previous Settings

That's all I can think of for now
2 weeks to go (they'll probably fix it all - I HOPE)

---

### Post by evdbovenkamp on 2017-10-23
Also the same performance (video) problems here. Worked fine up to 17.04, but now upgraded to 17.10 and the video performance is really horrible.
I will try to remove Unity 8 and try to install Unity 7.4 instead to experience if the performance is back again.
Keep you updated!

Below my lspci
---------------------

```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JD (ICH10D) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02)
30:00.0 USB controller: VIA Technologies, Inc. VL80x xHCI USB 3.0 Controller (rev 03)
```

---

### Post by Chanath on 2017-10-23
Are we still talking about 17.10 here?

---

### Post by egy-kid1 on 2017-10-23
i had the same problem so i disabled the nvidia drivers and im using ubuntu in xorg

---

### Post by MasterCATZ on 2017-10-27
its not just Nvidia , I have an AMD system , sluggish as anything 

Missing Unity greatly already 


 AMD A10-5800K APU with Radeon(tm) HD Graphics

 OpenGL Information
    GL_VENDOR:     X.Org
    GL_RENDERER:   AMD ARUBA (DRM 2.50.0 / 4.13.4-041304-generic, LLVM 6.0.0)
    GL_VERSION:    3.0 Mesa 17.3.0-devel - padoka PPA

---

### Post by fredwntr1 on 2017-10-29
I'm more curious as to how you got the padoka ppa working in 17.10 I tried twice and each time i had to reinstall the os  because I couldn't upgrade mesa nor could I remove the mesa-git packages when they were on my system

---

### Post by gregconquest2 on 2018-03-25
I just updated an Inspiron 1545 (P T4200 2GHz, Mobile Intel GM45 Express chipset, 3GB RAM, Intel GMA 4500MHD graphics) to UbuntuStudio 17.10, and it has slowed immensely. It is like there is always something heavy going on in the background. Just moving the mouse shows a cursor about 7 frames per second. The only proprietary driver I'm using is a Broadcom wireless.

Is this just an UbuntuStudio problem? I'll have to go back to a prior version as this is just crazy slow.

This problem may be the same as here: [https://askubuntu.com/questions/968938/ubuntu-17-10-works-very-slowly](https://askubuntu.com/questions/968938/ubuntu-17-10-works-very-slowly)  I cannot post a link to this thread there as I have only 31 of the 50 reputation points needed to comment.

---

