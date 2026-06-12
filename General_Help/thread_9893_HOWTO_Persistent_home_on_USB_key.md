---
title: "HOWTO: Persistent home on USB key"
date: 2005-01-02
forum: General Help
---

### Post by eco2geek on 2005-01-02
This HOWTO will tell you how to create a persistent home on a USB key/thumbdrive for use with the Ubuntu Live CD. (It works equally well for the [Gnoppix live CD](http://www.gnoppix.org), which you might want to check out.)

**Note:** This procedure involves reformatting your USB key to a format that Linux understands, and that Windows **doesn't**. This means:[list=a]
[*]If you use your USB key with Windows, and have any data on it you want to save, do it **before** you follow this procedure. After reformatting, all data on your USB key will be lost.
[*]The contents of your USB key will no longer be visible in Windows. If you click on it in Explorer, Windows will ask you if you want to format it. Don't, unless you want to lose your persistent home.[/list]

**How To:**
[list=1][*]Start the Ubuntu Live CD with your USB key attached. It should automatically show up on the desktop, usually as "sda1". (This howto will assume your USB key is mounted on /mnt/sda1. Please be **very** sure you are performing this procedure on your USB key, not your hard drive(s). Do not substitute for sda1, any partitions that start with the letters "hd," as they are your hard drives.)
[*]Pull up a root terminal: "Applications" menu > "System Tools" > "Root Terminal"
[*]Unmount your USB key with the command 
**umount /mnt/sda1**
[*]Format your USB key with the ext3 filesystem with the command
**mke2fs -j /dev/sda1**
[*]Mount your USB key with the command 
**mount -t ext3 /dev/sda1 /mnt/sda1 -o rw**
[*]Create a loopback file on the USB key with the command

**dd of=/mnt/sda1/ubuntu.img if=/dev/zero bs=1M count=100**

This will create a 100MB file for your persistent home. If you want a persistent home of another size, substitute your value for "100". In other words, if you have enough space on your USB key for a 256MB persistent home, use "count=256" instead of "count=100".
[*]Format the loopback file with the command

**mke2fs -j /mnt/sda1/ubuntu.img**

(answer "y" at the prompt).
[*]Now you are ready to reboot and use your persistent home. When Ubuntu's start screen comes up, you'll see a cursor at the bottom of the screen at the end of a long line of text. (You have 5 seconds to start typing.) Type 

**home=/mnt/sda1/ubuntu.img**

and press Enter to boot the CD. (If you want to see the boot messages instead of the Ubuntu splash screen, either press "F2" when the splash screen comes up, or change "splash=silent" to "splash=verbose" in that line of text at the bottom. If you watch carefully, you should see a success message when the live CD finds and mounts your persistent home.)
[*]You can now save files to your persistent home. Any configuration changes you make to Ubuntu's "look and feel" will be saved as well (if you tick the box asking if you want to save your session at exit).[/list]

The next time you start the Ubuntu live CD, make sure your USB key is mounted, and type "home=/mnt/sda1/ubuntu.img" at the prompt at the bottom of the initial screen, and it will restore your persistent home.

**Notes:**
- I tried using a FAT32- and a FAT16-formatted USB key; neither worked.
- I tried using the entire key instead of creating a loopback file; that didn't work either.
- This was tested using "warty-release-live-i386.iso".
- The "live CD" part of the Ubuntu Live CD is based on [Morphix](http://www.morphix.org), which in turn is based upon [Knoppix](http://www.knoppix.com). If you like live CDs and can live with KDE, check out Knoppix.

---

### Post by georgetoon on 2005-01-04
Thank you for this!  I'm going to give it a try at some point. 

It would be cool if this were already included with the Live CD download.  It would certainly open up a lot of possibilities/opportunities for newbies learning Ubuntu.

---

### Post by sohailm01 on 2005-02-01
Question: What should the USB file system be if the LiveCD in question is the PPC LiveCD. Is this even possible with a PPCLiveCD?

---

### Post by wsg on 2005-03-06
> This HOWTO will tell you how to create a persistent home on a USB key/thumbdrive for use with the Ubuntu Live CD

Hi...Will this work with the Ubuntu Linux Live 5.04 (Hoary) i386 BETA 4 CD which I have ?

(Also, is there a way to do this for the PPC version ?)

Many thanks...

---

### Post by groove473 on 2005-03-10
[QUOTE=eco2geek]
The next time you start the Ubuntu live CD, make sure your USB key is mounted, and type "home=/mnt/sda1/ubuntu.img" at the prompt at the bottom of the initial screen, and it will restore your persistent home.
[/QUOTE]

Hi.. 
Thanks again for this nice feature of saving LiveCD sessions. I was able to successfully mount my USB drive and create the image file on it.
But my USB drive was automatically mounted under "/media/usbdisk"  .. is this an anomaly??

Also, I could not find the prompt to type "home=/media/usbdisk/ubuntu.img" to restore my persistent home. The only prompt I see is "boot:" when I insert the LiveCD.
Once I press Enter here.. it then just takes me directly to the desktop.

Btw.. I am using Hoary Live CD (array 6 i believe). Where am I going wrong?

---

### Post by humrickhouse on 2005-03-31
Hmm...
I am not able to create any filesystems on my usb drive.  Even in a root terminal, it says I can't do this because it is a read-only filesystem.  How do I change that?

---

### Post by Testosteron on 2005-12-01
I tried it but it didn't work for me, but fortunately it wasn't necessary to use this method. But now I've got a different problem. I'm using the USB drive on Linux and Windows, so I formatted the drive to the FAT filesystem. But now I have only 54.9MB of space left on my 64MB drive. I tried to change the size back to 64MB with GParted but it stays on 54.9MB.
Does anybody know how I can regain my 'lost' 9MB?

Thanks in advance

---

