---
title: "broken display, crashes before logon screen"
date: 2009-07-30
forum: Hardware
---

### Post by dirkvic on 2009-07-30
I have a IBM thinkpad t40p. It was working well for the past year. Recently I upgraded to 9.04 and got everything to work. That is except the 3d drivers.

So I did something to break the displaydrivers, probably.

I think I did the following; Activated desktop effects, and manually edited /etc/X11/xorg.conf with ati drivers and added some extra options to the display device.

Once I rebooted the system crashes before it gets to the logon screen. First some flickering on the screen and then completely freeze.

I have tried recovery boot with repair broken packages, update bootloader, try to autorepair graphic problems. I have also tried dpkg-reconfigure -phigh xserver-xorg as the file says. I have also tried making an alternate install cd to repair a broken system.

I am all out of ideas, can someone come to the rescue? Pretty please...

---

### Post by dirkvic on 2009-07-30
My hardware in the t40p is ati mobility radeon firegl 9000.

---

### Post by dirkvic on 2009-07-31
Is it possible that desktop effects is active with non-valid display drivers? How would I go about to disable it?

---

### Post by dirkvic on 2009-08-02
Would it be possible to completely reinstall the GUI, and that way get a "deeper" reset of the display drivers and settings? Anyone... ?

---

### Post by Den-den on 2009-08-02
That's happened to me, and here is what I did:
boot your ubuntu in recovery mode, and enter root.

You need to uninstall your graphics drivers, and install basic ones. This should reset your setting and bring the system back to normal.

$ apt-get uninstall xserver-xorg-video-ati xserver-xorg-video-radeon xorg-driver-fglrx
$ apt get install xorg-driver-fglrx

You may need the install CD in the tray and / or the Internet connection (make sure you choose root with networking from recovery menu)

Good luck!

---

### Post by dirkvic on 2009-08-02
Thankyou for your input, den-den. But it didn't change anything for me. uninstall command was not recognized, but I tried both remove and purge commands. Still, no change.

However I got a working logon-screen by manually editing /etc/X11/xorg.conf from this:

Section Device
identifier "configured device"
endsection

to:

section device
identifier "ati"
driver "fglrx"
busid "pci:1:0:0"
endsection

This produced an errordialog at startup which in turn did reset graphics. I have still not managed to get the system 100% back up, but will dig in some more and post results here.

---

