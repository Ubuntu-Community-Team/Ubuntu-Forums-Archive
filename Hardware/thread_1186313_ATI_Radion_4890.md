---
title: "ATI Radion 4890"
date: 2009-06-13
forum: Hardware
---

### Post by skozzy on 2009-06-13
I have a new computer, and i7 920 with an ATI 4890 video card, is there a way to get this video card working correctly yet ?. I get the enhanced desktop features but I also have an annoying logo on the bottom right of the screen saying AMD Unsupported Hardware.

Im maybe a little to new to linux to install hardware drivers, the result I got now was from the Hardware Drivers in the Admin menu. 

Also if I attempt to load the Display settings the computer slows down so much so that it's barely usable, logging off and on brings it back to full speed but I still have the same problems with the annoying logo and not being able to change my desktop resolutions in the display manager.

---

### Post by Starkofdoom on 2009-06-16
I am actually running into this same issue, did you ever figure it out?

---

### Post by skozzy on 2009-06-16
No, the annoying thing is still there.

---

### Post by wleizero on 2009-07-01
Have you installed the drivers? If yes, and you suspect a different issue, please repost. Use **_uname -m_** if you are unsure of your architecture.


#DRIVERS: x86_64 bit architecture
[http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.36.3.6&contentType=GPU+Download+Detail&ostype=Linux+x86_64&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.36.3.6&contentType=GPU+Download+Detail&ostype=Linux+x86_64&keywords=&items=20)

or

#DRIVERS: x86 32 bit architecture
[http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.36.3.6&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.36.3.6&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20)

---

### Post by skozzy on 2009-07-01
I will give these a go and see what happens.

---

### Post by stanna on 2009-07-06
i had the same issue with the logo. i uninstalled the drivers that ubuntu recommended. then installed the ones from the ati website, everything seemed fine.. but after 30 - 40 mins of use my system would completly crash, i would be left with a blank screen and only option is to reset.. couldnt restart gnome (ctrl-alt-backspace)--(i re enabled it before i installed the drivers). 

also it would seem to crash when i try to playback a movie file (which worked perfectly with the ubuntu drivers). also fullscreen me-tv would result in the same crash (blank screen).

anyone have any ideas?

using the ati drivers did however remove the watermark and enable me to change res. i would get crashes when trying to enable my secondary monitor, but im leaving that alone until i get it to actualy work properly with 1 monitor first.

---

### Post by h2z on 2009-07-06
I'm having the same "watermark" with my 2900GT card. The driver installed by Envy seems to be the most stable. I've also managed to remove (hide it probably) by lowering the resolution but it took about 3 minutes waiting for "display properties" to actually load.

---

### Post by JohnFante on 2009-07-09
Radeon 4890 is not yet supported by the drivers that comes with Ubuntu 9.04. You have to install the drivers from ATI manually. 

It can be rather tricky to get them up an running properly but I have used this guide with success several times:

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers)

Use the section called "Installing the drivers manually". 

The guide also includes instructions on how to update.

Good luck!

---

### Post by khelben1979 on 2009-07-09
Catalyst 9.6 is the latest version right now. Have you tried it?

Also, if the card runs too hot, you will haveto either adjust the fan through software or install more fans in your case to lower the temperature.

Have you been able to test how it works with Windows?

---

### Post by JohnFante on 2009-07-11
I am running 9.6 right now. Works fine.

I have not had any heat problems. When the work load on the card increases the fan speed increases automatically. No problem there.

I am using the card in Windows 7 RC also and there it works fine also. Same fan behaviour. 

The drivers in Windows are clearly better than the Linux drivers thou :-(

---

### Post by khelben1979 on 2009-07-11
> **JohnFante said:**
> The drivers in Windows are clearly better than the Linux drivers thou :-(

I wonder if this is the case if you compare OpenGL graphics (Windows vs Linux) ?

---

### Post by QIII on 2009-07-11
> **JohnFante said:**
> The drivers in Windows are clearly better than the Linux drivers thou :-(

C'mon guys!

Microsoft does not write drivers for video cards.

OEMs do.

They write them to be compliant with Windows.  Windows is not made to be compliant with OEM's drivers.

The actual situation is that the OEMs spend a lot more effort creating Windows compatible drivers than Linux compatible ones.  The open source drivers are either a black box reverse engineering exercise from the outside, or a second rate OEM effort going out the side door.

Until the OEMs care to create better drivers for us, it will be thus.

---

### Post by JohnFante on 2009-07-11
> **QIII said:**
> The actual situation is that the OEMs spend a lot more effort creating Windows compatible drivers than Linux compatible ones.  The open source drivers are either a black box reverse engineering exercise from the outside, or a second rate OEM effort going out the side door.

Until the OEMs care to create better drivers for us, it will be thus.

My point exactly. 

For instances does the 9.5 and 9.6 (at least) drivers not interact very well with WINE. The NVIDIA drivers work much better.

Lets hope ATI shapes up a bit.

---

### Post by fr0g on 2009-08-24
Hey guys, I was having issues installing the drivers..then I followed the previous suggestion to install them manually. Everything went smoothly, installed the ATI Catalyst CP, and then prompted for a restart. Upon restart,I boot into Ubuntu and get a single multi-colored and pixelated bar stretching across my screen, with broken menu labels but none of the hotkeys work. I have no idea what I should do, tried repairing broken packages from recovery mode, nothing. Any suggestions would be greatly appreciated!
Cheers.

---

