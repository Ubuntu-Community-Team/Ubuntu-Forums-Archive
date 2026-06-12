---
title: "unable to install"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by dan1982 on 2009-08-24
Hi everyone

Sorry if this sounds naive, but I'm new to this

I have an asus eee 901, which came with XP installed
windows has got to go.
I'm trying to install UNR from a usb, and nothing happens.
 downloaded the .img
 used disk imager to write the usb
 when i try to install an hourglass appears, then: nothing.
not a sausage.

What am I doing wrong?

---

### Post by starcraft.man on 2009-08-24
Hmmm, you sure ya did it right? See here for a[ wiki doc]("https://help.ubuntu.com/community/Installation/FromUSBStick") on how to install from USB.

Ya don't just burn it to the usb. Also where did you get the .img file, I thought that Ubuntu distributed all the copies as ISO.

---

### Post by eltoozero on 2009-08-26
Hey dan1982, an excellent decision, the current release 9.04 works great and the upcoming 9.10 will be even better.

There's nothing "special" about installing on the 901 except for how you actually boot to the usb after it's written, but first you've got to write that thumb drive correctly.

I would suggest unetbootin in windows or linux located [here]("http://unetbootin.sourceforge.net/").

Download the 9.04 Netbook Remix ISO (it sounds like you've already done that).

Use the instructions on the [wiki]("https://help.ubuntu.com/community/Installation/FromUSBStick") as linked in the previous post for specifics, and mind this part:

> If you need to activate the original Ubuntu livecd boot menu...[snip]...make these changes to your USB drive after your UNetbootin installation is completed:

1) Delete the SYSLINUX.CFG file or rename it to be SYSLINUX.OLD

2) Enter the ISOLINUX folder and rename the ISOLINUX.CFG file to be SYSLINUX.CFG

3) Move up to the top level and rename the ISOLINUX folder to be SYSLINUX 

To boot from the usb thumb drive on the 901 without changing any settings in the BIOS just hit ESC during POST to load a one-time boot selection screen.  If you have trouble hit F2, then ESC, when the BIOS loads, hit ESC to exit without saving changes, you will then see the boot device selection screen without hard coding it in the BIOS.

Good luck!

---

