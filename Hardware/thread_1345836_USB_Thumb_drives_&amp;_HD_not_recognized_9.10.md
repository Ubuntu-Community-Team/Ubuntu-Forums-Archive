---
title: "USB Thumb drives &amp; HD not recognized 9.10"
date: 2009-12-04
forum: Hardware
---

### Post by francsal on 2009-12-04
I´ll go by parts. First, I tried to install Ubuntu Karmic on this T40 Thinkpad, via a USB thumbdrive, with the desktop image on it. It started to boot, but, after a few moments, the light on the thumb USB drive would go off (it´s a 8GB Cruzer SanDisk), so I had to install via the CD. Installation went relatively well (had to adjust somethings because of a bug in grub during startup, corrected in the first upgrade I did on the computer)

After that, the computer worked very well, but there´s this problem with USB storage devices. Every time I plug the USB thumb disk, it doesn´t get recognized. It doesn´t show on lsusb. It´s not shown on gparted. And the behavior is the same, when I plug it, the light on the USB stick turns on for a second, then turns off.

dmesg show the message of "Unable to enumerate device on USB port 4",as reported in other threads. Tried to add the usb_mount (or was it usb_automount) into a config file  in /etc/modules (sorry for my fish memory, can´t quite remember if it was exactly there where I added the line) and it didn´t worked out.

The stick is fine, since it gets recognized in my netbook (ubuntu & kubuntu karmic as well) with no problem, and on a windows desktop as well. Also, the ports are ok, since the usb mouse works without a problem in both of them, and the memory stick was recognized instantly when it had WinXP.

Also, the usb stick is not the only one not working. I also have a ZTE 3G Modem, that, when installed first gets recognized as a CD drive, and it doesnt show either, nor in nautilus, nor in gparted, nor in lsusb. And also, a WD external HD isn´t recognized either.

If I try to boot the computer with the usb stick plugged in, it gives me the "unable to enumerate" message during startup. And, if I try to reboot or shut it down with the USB stick plugged, it  gives the message again. If I start or shutdown the computer without it, no error message at all.

Checked on launchpad, and found no solution, either. I´m feeling kind of desperate about this. I have huge amounts of data to transfer to that computer, and now it seems that there´s no chance to do it with the external HD or memory stick. Any tip would be highly appreciated!

Thanks in advance. 

Cheers.

Frank.

---

### Post by francsal on 2009-12-04
Bump.... :S

---

### Post by wilee-nilee on 2009-12-04
Have you looked in bios to see if the usb is turned off

---

### Post by francsal on 2009-12-05
Yep it is on. Thinking back, when I had a dual boot (win XP with Ubuntu installed via wubi) sometimes it worked....

---

### Post by Metteke on 2009-12-05
Same here.

It used to work, but all of a sudden USB disks recognising stopped.
On the same laptop on XP or OSX it works ok.

Maybe strange, it was just after Skype crashed an killed ths Bison webcam (also internal usb). A new install (from within windows, netbook remix version) to a HD install did not solve. Bios seems ok, but I cannot see the camera??

Laptop is a Medion Akoy E1210 netbook

thx!

---

