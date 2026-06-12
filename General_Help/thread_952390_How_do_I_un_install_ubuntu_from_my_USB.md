---
title: "How do I un install ubuntu from my USB?"
date: 2008-10-19
forum: General Help
---

### Post by Refuge on 2008-10-19
Hello everyone.

I recently installed Ubuntu onto my 2GB USB, however, when I go to boot my computer from the USB drive, it stays on a blank screen with a white blinking "-" at the bottom left hand corner.

Is this mean to happen? Or is there something wrong? if there is, how do I un install it from my USB so I can re install it? Because I go onto my main OS, Windows XP, and I can't access the USB anymore to remove the Ubuntu files, since formatting it as FAT32, it wants me to re-format before I can enter it.

Any help is appreciated

---

### Post by Refuge on 2008-10-19
Anybody?

---

### Post by woodenbrick on 2008-10-19
What method did you use to install Ubuntu to the USB?
I would recommend using [UNetBootin]("http://unetbootin.sourceforge.net/"), since it will automate everything.  There is a windows version.

BTW, just let Windows format the drive, since its not working in its current form. I've heard that FAT16 is recommended, though FAT32 should have worked too.

---

### Post by Refuge on 2008-10-19
I burned the ISO file onto a data disk through InfraRecorder or something.

Than I booted up via the CD and installed and chose my USB.

I formatted to FAT36, I also get an error message before installing. Something about making a partion larger. But I don't know how to do that.

I have UNetBootin but I don't know what to do with it, because it copies the ISO files onto my USB, or does it install it?

---

### Post by Refuge on 2008-10-19
Also, my computer doesn't format to FAT16, only to FAT and FAT32

---

### Post by Sycron on 2008-10-19
FAT means FAT16

---

### Post by Refuge on 2008-10-19
It does?

I feel like an idiot >.>.

I'll try and format to FAT16 and redo the installation. btw, anbody know how much room ubuntu takes up as newly installed, without extra things put on it?

---

### Post by az on 2008-10-19
> **Refuge said:**
> It does?

I feel like an idiot >.>.

I'll try and format to FAT16 and redo the installation. btw, anbody know how much room ubuntu takes up as newly installed, without extra things put on it?

FAT filesystems do not support the filesystem permissions you need to run GNU/Linux.  You need to let it format the partition to ext3.

Perhaps that's your problem.

The install takes about 1.5 gigs.  2 gigs is pretty small, but it should work.

---

### Post by Refuge on 2008-10-19
So, if I format it to FAT on windows, run the CD with Ubuntu on it, it formats it to ext3 it should be fine?

What about the error code I am receiving? Something about making a partion file larger or something before it starts the install? I just click continue and ignore it, maybe that is the problem?

---

### Post by woodenbrick on 2008-10-19
UNetBootin will basically create a liveCD on a USB, is that what you wanted? Otherwise, if you wanted to create an ubuntu usb drive to boot off and save changes back to it, there is a walkthrough tutorial here:
[http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/]("http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/")

---

### Post by C.S.Cameron on 2008-10-19
You seem to be doing things right for a  full Flash drive install except the formatting should be ext3.
Installer should choose this automatically.
2G is too small to be useful for a full install.
Unetbootin, liveusb and usb-creator will install to under 700M, but will basically be Live USB images.
Liveusb and usb-creator can be made persistent, settings and stuff are saved to folders or partitions called home-rw and casper-rw.
4G Flash drives seem to be going for $10 CD.
A 4G Flash drive gets filled pretty quick. 
Once filled it will not boot GUI until something is removed.

---

### Post by Refuge on 2008-10-19
Wooden Brick - Terminal? I don't know how to open a terminal window whilst booting from my Live CD, I don't think windows allows me to do that.

---

### Post by woodenbrick on 2008-10-20
Are you using the pendrivelinux.com tutorial? Your terminal will be in applications -> accessories -> terminal.  I don't understand why you are mentioning windows since you don't need to use it for this process.

---

