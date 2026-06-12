---
title: "HDMI resolution problems"
date: 2012-08-28
forum: Hardware
---

### Post by Odin Overland on 2012-08-28
Hello,
First let me say that I have been researching this problem for days.  I've found only one other person having a similar issue on an obscure website, and no one has been able to help them either.

I have a Toshiba laptop that I have hooked up to our Sony TV.  What I am trying to achieve is a HDMI output of 1920x1080.

A few notes here:

1) The Sony is 42" - but Ubuntu recognizes it as a 72" Sony

2) My wife's work laptop running Windows can put a 1920x1080 HDMI output on this same TV no problem

3)  My Toshiba can put out a 1920x1080 resolution via VGA to this same TV.

4)  Sound works no problem via HDMI

5)  No additional proprietary drivers are showing as available

6)  The output for my graphics card using "lspci -v"  is:

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])

7)  My installed OS is Ubuntu 12.04 amd64

So my first step was:

*cvt 1920 1080*

The output of which was:

[I]# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync[/I]

Next step:

*xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync*

Next:

*xrandr --addmode HDMI1 1920x1080_60.00*

This then showed the new resolution option in the settings, but once tried my TV had only a black screen and stated "Invalid Format"

I tried 59.96 Hz, 59.00Hz, and other reasonable numbers - all without success.  I have tried making all possible adjustments on the TV itself with no additional success.

The HDMI output works much better than the VGA, but the only workable HDMI resolution of 1280x720 defeats the whole purpose of it being hooked up to the TV.  I would really appreciate any help or suggestions.  Thanks.

---

### Post by Odin Overland on 2012-09-04
Well - anyone at least have any suggestions on how to fill out a bug report for this?  I've never filled one out dealing with displays before - not sure what they are looking for.

---

### Post by ambroseangle on 2012-09-05
I am currently using the HDMI cables for my desktop PC, They are digital ones and I am using these cables since last year. No problem existed from then to now and the quality is also fine. The Cable that we are choosing should be able to provide us the better quality picture with total clarity and with fine volume. I used to download movies and games frequently and works more than eight hours daily. There is no problem and  data loss existed. Could you please provide some more attachments about the best cables?



[hdmi cables]("http://www.cmple.com/c-7-HDMI-cables.aspx")

---

### Post by Incarnadine on 2012-09-06
I had this very same problem as you, but after installing the propietary drivers for my video card everything was solved. Do you have the propietary drivers installed for your video card?

Not being able to put out a resolution of 1920x1080 with your HDMI output is really a shame. I wouldn't even try to use my VGA port and focus on getting the HDMI output to work properly.

---

### Post by Odin Overland on 2012-09-08
As fa as I can tell the proprietary drivers for this integrated graphics are supposed to be included in the installed with the included package "xserver-xorg-video-intel" - which is definitely installed.  I installed "mesa-utils" as some other forums suggested, and my system now reports to be using the driver: "Intel® Sandybridge Mobile"  I turned on proposed updates and installed Kernel 3.2.0-31-generic, and upgrade xorg, and still no fix.  No proprietary drivers are being reported still either.  Still really trying to figure this one out.

---

### Post by Odin Overland on 2012-09-10
Well I read somewhere else (and I can't find it now to site my source - sorry), that all of the Intel Drivers were fixed in the newest 3.5 Linux Kernel.  So I wiped Ubuntu and installed Fedora 17.  HDMI is working perfectly (although the integrated graphics card obviously leaves a lot to be desired - but I got this thing for free... beggars can't be choosers).  Anyway, anyone having the same issue will have to wait for an Ubuntu release with the fixed Kernel, find a way to install the newest Kernel on their own, or just be like me and go to a different OS.  I switched off of Fedora because I didn't want to be constantly updating things such as the Kernel, but now it doesn't seem so bad :D

---

