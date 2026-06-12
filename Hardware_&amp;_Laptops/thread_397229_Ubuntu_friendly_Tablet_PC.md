---
title: "Ubuntu friendly Tablet PC?"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by Gentist on 2007-03-30
I'm planning on getting a Tablet PC, but would like to remain Windows free. In other words, it has to play nice with Ubuntu (or other Linux distro).

This is what I have in mind:

Min specification: 12" screen, 512MB RAM (preferably 1GB or more), dual core CPU (don't really care whether it's AMD or Intel), DVD-drive/burner OR USB-boot support. Graphics card with proper 3D acceleration.

The following has to work:
3D acceleration (Beryl, Blender, etc... Doesn't have to be that powerful but should have proper drivers), Pen (fully functional, touch sensitivity, etc...), audio, everything else which should be expected to work (USB, firewire, etc...).

I'd like the following to work (though doesn't necessarily have to):
WiFi, preferably with encryption support (I can always get an external card if I have to). Suspend to RAM and Hibernation would be nice, but I can live without it. Touchpad (when I don't want to use the pen). Proper battery support (ACPI; reporting and mode changes depending on battery power-level), screen dimming, etc... A few hours of battery life would be nice too.

Everything else is pretty much a bonus. Price has to be below ~$2500.

If anyone has any experience with a Tablet PC that matches the above description, I'd love to hear about it.

---

### Post by MrMunkily on 2007-05-01
I'm similarly inclined:

I'm less sensitive to power but more sensitive to price - I'm willing to go back a  generation to save money.

For me, slate is better than laptop conversion. Also, I need a wired ethernet port since my network won't support non-windows wireless (IT prejudice) and I need at least a letter sized (8.5x11) screen.

---

### Post by sirlancelot on 2007-05-01
I too will be purchasing a tablet PC (convertable, no slate for me), I've bookmarked a couple threads that might help me get the stylus working, which is really the only feature on your list that is 'sketchy' in Ubuntu (no pun intended).

[Wacom Tablet Working linuxwacom]("http://www.ubuntuforums.org/showthread.php?t=303555")
[Enable your Wacom Tablet with Pressure Sensitivity]("http://ubuntuforums.org/showthread.php?t=25151")

I'm going to guess and say that if you get a "Powered by Wacom" tablet PC then you can most likely get the stylus working via one of those threads. I know Toshiba uses "Wacom-enabled" convertable Tablet PCs.

Hope this info helps!

---

### Post by Lady Owl on 2007-05-01
I just made an offer for a used Flybook... Don't know about that 3D-accelerator, but at least the other requirements are fulfilled, I think. Well, no touchpad, though, but I get it with a wireless mouse, and and external dvd writer.

I found Flybook recommended in one chain here, so I dared to offer (it's not mentioned in [https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops) in good or bad). If I get it, I'll post here my Ubuntu installation experiences.

Edit. Unfortunately I did not get it after all...

---

### Post by jjordan on 2007-05-03
I am using a Fujitsu P1510 convertable.  Frankly, pen based Linux is not quite ready for prime-time. but neither is Pen Based Windows. 

There is no effective handwriting recognition under Linux.  There are a couple of character recognizers that work but writing things 1 letter at a time with about an 80% recognition rate is a quick road to insanity.  OneStroke is probably the best but you must create your own stroke file.  The most mature and usable general notetaker is Jarnal, it is a Java program so it takes a little work to get it going but it works pretty well once it is running.  It also is slow to start.  If you need primarily sketches and unrecognized handwriting it will work.  Jarnal includes character recognition so you can do some text input and will probably eventually be quite usable.  

On screen keyboards work.

Touchscreen drivers are problematic but doable in most cases.

Here in Italy HP has an awsome looking convertible, I don't know the state of Linux support on it.

Emperor Linux offers a couple of pre-configured models that look good but pricey.

[http://www.emperorlinux.com/systems/tablet/](http://www.emperorlinux.com/systems/tablet/)


I would highly recommend a convertable!

-j

---

### Post by TabletGuy on 2007-05-18
I've been a tablet PC user since they came out and have been using Ubuntu on them since H. Hedgehog.

Here's my take:
Tablet PCs owned:
HP TC1000
Motion Computing M1200
Motion Computing M1400
and I take delivery of a p1610 as soon as it clears customs over here.

If I was looking to buy a 12'' model today I would buy a X60 from IBM (Lenovo).

Why the x60?
Because Tablet PCs need to be able to stand up to a lot of wear and the ThinkPads are built tough.
I have literally worn out both my m1200 and my m1400 machine in about 18 months for each computer.
I take my tablet everywhere, to every meeting and to most events. I use it for:
A) as my primary desktop
B) as my ebook reader (I live in Africa so being able to download books is essential)
C) as my music and video library
D) as my notepad
E) as my primary productivity machine (word, excel, LAMP programming, some C# Windows forms stuff).
F) as my phone (skype), email, and fax machine.
So I use my Tablet at least 14 hours a day.

I will never buy Motion Computing again, they don't keep up. USB ports and power ports have failed on both machines within 12 months.

Also, the Thinkpads have usually enjoyed very good linux support.

Other general lessons:
- Configuration never works 100% out of the box for Linux - but almost everything can be set up if you are patient enough. For me screen rotation is the most important tablet feature which has been hardest to get going. This is a lot easier in 7.04. In the early days the Wacom tablet was challenging as well but its pretty much ok out of the box now (at least for the M1400).

- RAM is essential - which is the same as most computers but if you are going to be reading ebooks you are probably going to be running a VMware virtual machine for the DRMed Adobe Reader. It sucks but its true (although I haven't tried the Windows reader under wine for about a year now so it might be improved).

- Having used pure slate models from 03 - 07 I am going back to a model with built in keyboard for my next tablet. It is really convenient to just flick the computer around and start using the keyboard. This isn't such a factor in Windows where MS has built in the on-screen keyboard for almost everything but quite often in Ubuntu you need to use the keyboard (like each time you change the system settings and up pops gksudo). There are work arounds using the command prompt but these involve typing. Tapping away on an onscreen keyboard one key at a time gets olds real quick.

It also sucks when the built in USB ports fail (due to almost constant use for a keyboard) after only 8 months of use!!!! Did I mention that I won't buy a Motion Computing machine again!! 

- When you are using a pen it is really cool to do things with as few a taps as possible. A good mouse gesture or application launcher is essential.  I have yet to find a Linux equivalent to strokeIT which allows you to completely script gestures to control windows. This is really handy for cutting and pasting or other basic windows stuff.

- The only reason I gone with the p1610 over the X60 for my next machine is weight. I travel a lot for the work I do here and every kilo counts. I also prefer a smaller form factor for the lifestyle applications like reading ebooks.

- I have never consistently used the Handwriting recognition built into windows. It works ok but a keyboard is much faster. I think its just a gimmick and so couldn't care less that it isn't around using Ubuntu.
If you have a lot of typing to do you will be using the keyboard because the handwriting recognition is painful. If you are entering a password or something in slate mode then you will be using the onscreen keyboard and not handwriting because it is more accurate.

- The only thing I can't do in Ubuntu easily that is really cool to do with a tablet PC is write comments directly on Word document and Powerpoint presentations - openoffice doesn't have this functionality/
That's it though, for me everything else is doable equally well with Linux. 

-Ubuntu is waaaaay faster than the Tablet PC edition of Windows.

Good luck, don't look past the x60.

---

### Post by freund on 2007-06-04
With fiesty I have had great experience on the lenovo X60 tablet. Almost everything works out of the box with minor tweeks on screen rotation and new driver for the ethermnet card. 

Its all posted on this form how to tweek it.

I would recommend the x60

al

---

### Post by michaelslarsen on 2007-07-01
I have a Lenovo X60 Tablet PC, and have just installed Ubuntu 7.04 Fiesty Fawn, but have been unable to get ANY of the tablet PC stuff working.  How do I get the touch-pen working?  And is there a way to get the screen to to rotate?   Any info would be greatly appreciated.  I must admit that after using Vista on this machine, Ubuntu  is twice as fast as Vista- very nice.

Cheers


Larsne

---

### Post by freund on 2007-07-06
The best place for configuring the X60 is at [http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_X60_Tablet](http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_X60_Tablet)
which points to
[http://luke.no-ip.org/x60tablet/](http://luke.no-ip.org/x60tablet/)
but will soon be transfered to the first site.

It has everything about configuring buttons/screen rotation/pens ...etc

with some ubuntu specific stuff by searching x60 tablet here at this forum
good luck
al

---

