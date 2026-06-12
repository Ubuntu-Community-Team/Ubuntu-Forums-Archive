---
title: "ThinkPad T60 - Kubuntu 8.10 - ATi driver problem"
date: 2008-11-03
forum: Hardware
---

### Post by aktorun on 2008-11-03
Has anybody succeed to install ATI drivers correctly on T60?

My Laptop is T60 with X1300 (mobility) graphic card

I am using Kubuntu 8.10 with KDE 4.1.2

Everything works fine except my graphic card. I cannot use 3d graphic accelaration.

I have tried to install "proprietary drivers" but the system did not boot after the restart.

I had to open the system in recovery mode and reconfigure the XCONF to start it up again in KDE.

Anybody succeed to install ATI drivers correctly and able to use tools like COMPIZ with 3d HW accelaration?

Thanks in advance
aktorun

---

### Post by aktorun on 2008-11-04
Let me change my question :

Has anybody succeed to install "one of the latest ATI driver" for "ATI Mobility Radeon X1300" graphic card.

I am using Kubuntu 8.10

My laptop has below specs :
# Processor: Intel Core Duo processor T2400, 1.83GHz, 667MHz FSB, 2MB L2 cache (Mobile Intel 945PM Express chipset)

# Graphics: ATI Mobility Radeon X1300, 64MB DDR2 SDRAM, 16 million colors, max 2048x1536, simultaneous external display

---

### Post by ramnarayan on 2008-11-10
Am using Ubuntu 8.10 on my Thinkpad T60. Installed the ATI drivers through the install proprietory driver interface - and somehow (meaning i don't know when) the ATI Catalyst Control Center also got installed.

That said the problem i am having is with playback of video files - i get constant flickering in the video - with both the graphics card on and off.

ram

---

### Post by zexdout on 2008-11-18
I am in the same boat as you guys, everything good except for no 3d acceleration and if I run "sudo rovclock -i" in terminal I found that it isn't detecting how much Video RAM I have and it says it is running at 0.0 MHz when it is rated at 200 MHz.  I have searched hours upon hours trying to get it to work!

---

### Post by Santala on 2008-12-04
Hi!

I have an ATI X1400 on my T60 and the same problem.  I think that we are stuck with 2D, which is fine as long as you do not care for wobbly windows...  Pity, though.  It would have been nice to try out.  The T60 is otherwise great with 8.10.

---

### Post by korpenkraxar on 2008-12-04
> **aktorun said:**
> Let me change my question :

Has anybody succeed to install "one of the latest ATI driver" for "ATI Mobility Radeon X1300" graphic card.

I am using Kubuntu 8.10

My laptop has below specs :
# Processor: Intel Core Duo processor T2400, 1.83GHz, 667MHz FSB, 2MB L2 cache (Mobile Intel 945PM Express chipset)


Weird...

T2400 - that is 32-bit right? I had ATI's fglrx working just fine with 3D on my Thinkpad Z61m running Ubuntu 8.10 32-bit version and an ATI X1400 up until yesterday when I reinstalled and switched to 64-bit instead. I have not tried fglrx since but it should definitely work for you guys as well. 

A word of caution though, expect some trouble even if you *do* get that driver going. It is not yet very mature (as many of you might already know) when it comes to combining compiz, video and other 3D apps. You will need to use something like fusion-icon to easily switch compiz off to be able use xv for good video playback and OpenGL for 3D in other programs. :-&

Unless you need to squeeze the final drops of performance out of your cards you are probably better off with the default open source "radeon" driver which indeed does do 3D, compiz and video all at once and which also works just fine on this Thinkpad. Are you saying that you only have 2D with this driver as well?

If "radeon" does work and you stick with that one I recommend putting the line:

```
Option "AccelMethod" "EXA"
```

in your /etc/X11/xorg.conf, like this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Option "AccelMethod" "EXA"
EndSection
```

which gives better performance and removes the artifacts that are otherwise produced by windowed 3D apps such as glxgears.

Moreover if you continue having problems with your ATI cards and are not able to solve them here at the Ubuntu Forums, try searching and posting over at the Phoronix Forums at [http://www.phoronix.com/forums/](http://www.phoronix.com/forums/) where people are always very up-to-date with the latest news and quirks in graphics and drivers on Linux.

---

