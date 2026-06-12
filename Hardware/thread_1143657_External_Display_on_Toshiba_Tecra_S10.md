---
title: "External Display on Toshiba Tecra S10"
date: 2009-04-30
forum: Hardware
---

### Post by DougZ on 2009-04-30
Just got a new laptop in at work I had to set up and they just released Jaunty, so thought I'd give it another go at getting Ubuntu to work...

This is a Toshiba Tecra S10 with a docking station hooked to an external display via a usb DVI kvm switch.  The pre-installed Vista worked seamlessly with this setup.

Booting off the Live Cd the Ubuntu logo appears on the external display with a progress bar.  As it gets all the way to the end an error message appears (very) briefly about usb and failed address. At this point the screen goes blank and we're done.

Tried tweaking the BIOS settings and the error message went away but it still locks up at the same point.

Whatever its doing nukes the kvm switch.  I have to pull the power on it to get it back.  After reseting the switch the screen is stil blank when switching to the laptop.  The Fn keys to switch displays also do not work.

Booting out of the docking station works fine.  Docking the machine at that point I get mouse and keyboard but cannot get it to detect the external display.

Just for giggles I plugged the display directly to the docking station.  Same effect.  I then switched to vga cable plugged directly to the laptop.  Same effect.

8.10 (forgot the name) does not have this problem EXCEPT after switching back and forth a few times the keyboard goes to hell: The keys stick like mad and the machine is unusable.

Not directly related, but of note to anyone with this laptop:  I did do an install briefly before restoring back off a backup. No sound after install, and running updates breaks the network card.  Fun!

---

### Post by gnwiii on 2009-08-15
Just got an S10, installed ubuntu 9.04.  Previously I was using a Thinkpad
X60, but the Tecra was initially configured with Windows XP and was getting BSOD's.  The TP could not be trusted to connect to a projector -- not ideal for a portable, but I havn't had the Tecra long enough to know how it will perform.

I'm using a PS2 KVM with a PS2 to USB converter and analog monitor at home, no KVM at work, but external display on the docking station's DVI connector 

At work the screen goes blank, so I can only use Ubuntu with the internal display.  At home dual display works well.

There is no sound using the internal hardware, but an external USB dongle works (using OSS):

Bus 003 Device 003: ID 0d8c:0103 C-Media Electronics, Inc. Turtle Beach Audio Advantage Micro

---

