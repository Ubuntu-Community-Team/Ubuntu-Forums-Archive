---
title: "Different kind of dual boot"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by mirach on 2009-11-11
All,

I want leave XP untouched on my primary hard drive and install 9.04 or 9.10 on my second drive.

In BIOS I'll set the boot order to USB first then the XP drive. If the USB is plugged in I want Ubuntu to boot and if not then XP...

How please? What needs to be on the USB drive? GRUB?

Thankyou

I'm still experimenting with which Ubuntu I want so I need a quick way to wipe Ubuntu and start fresh without having to fix the MBR for XP each time.

---

### Post by wilee-nilee on 2009-11-12
> **mirach said:**
> All,

I want leave XP untouched on my primary hard drive and install 9.04 or 9.10 on my second drive.

In BIOS I'll set the boot order to USB first then the XP drive. If the USB is plugged in I want Ubuntu to boot and if not then XP...

How please? What needs to be on the USB drive? GRUB?

Thankyou

I'm still experimenting with which Ubuntu I want so I need a quick way to wipe Ubuntu and start fresh without having to fix the MBR for XP each time.

So you want to use a usb external HD for the Linux it will run slow. You might just consider using a thumb and using the Ubuntu usb creator get a thumb about 8gigs and let it set the persistent to the highest so you can update and add programs. I would use the external HD to back stuff up.

---

### Post by mirach on 2009-11-12
Sorry, my question wasn't clear - My second drive containing Ubuntu is a standard SATA hard drive plugged directly into the motherboard. I just want to use a USB memory stick as kind of a trigger to make the machine boot into Ubuntu instead of XP.

 If I've set my BIOS to boot the USB stick first I want it to encounter boot instructions that tell the machine to boot Ubuntu off the second hard drive. If the stick isn't there I just want XP to boot like normal.

Thanks again.

---

### Post by Ginsu543 on 2009-11-12
If you have Ubuntu on a separate drive, then you should have no problems with Ubuntu messing with your Windows. Just set your second drive as first in boot priority in BIOS and install Ubuntu on it, just making sure to install the bootloader not to (hd0) but to the root partition of the second drive (e.g. /dev/sd1). This way you leave the MBR of your first (Windows) drive intact. You can try out whichever flavor of Ubuntu you want and if you want to get rid of it, just change the boot order and put your Windows drive as first and it should boot into Windows. I've been running my XP/Ubuntu dual-boot setup this way for years and it's worked great for me. I guess all I'm saying is that you don't need the usb drive to act as GRUB for you; let GRUB do that.

---

### Post by mirach on 2009-11-13
Thanks for the reply Ginsu. Putting the bootloader on the Ubuntu disk does indeed keep the Windows MBR intact but I don't have a dual boot system anymore – Selecting XP from the boot screen gives me this error:

[I]	Error 13:
	Invalid or unsupported executable format
	Press any key to continue…[/I]

To boot Windows I have to change the boot order back in BIOS.

Unless I missed something I would still like to know how to set up a USB such that when it's plugged it makes Ubuntu boot off my second hard drive.

Thanks!

---

### Post by darkod on 2009-11-13
You are complicating your life way too much. :)
First of all, even if you let grub install on the MBR of the disk where XP is, no big deal. You will have it as entry in grub and can boot into it even if you have your ubuntu partition deleted. This is not the case if you place grub on the partition itself.
Second, you have two hard disks so you can easy keep the XP disk with XP bootloader in MBR and install grub on the MBR of the other disk. Again, no need to install on the ubuntu partition.
Why involve USB stick just to boot grub from it?

This is very important: are your hard disks different size? If they are it's easy to know which one is which. If not, you will have to figure it out, by the size of the XP partition for example.

1. Keep your XP disk as it is.
2. Boot with Ubuntu CD and select install Ubuntu.
3. When you get to the screen asking where to install and how, select manual partitioning. On this screen you should be able to make a choice between the two hard disks (I have never installed with two drives so don't know where exactly the choice is, but it has to exist. You'll figure it out.). If the size of the disk or the partition plan looks like the XP disk, then you are on the wrong one. Just select the other one. IMPORTANT: Write down whether the disk you want for Ubuntu is called sda or sdb (first or second drive). Create the partitions any way you like, I usually do it manually to control it myself.
4. In the last screen when installing Ubuntu, BEFORE you click Install button, there is Advanced button. Click there and it will offer you choise to select on which disk MBR grub to be installed.
5. If your Ubuntu disk was sda, select either sda or hd0 (if that's the name used). If the disk was sdb, select sdb or hd1.

That's it. Grub will be on the MBR of the Ubuntu disk. Your XP disk is not touched.

In your BIOS, usualy there is setting first boot device to be HDD and then there is another setting which of the hard drives to be first choice. In this second setting you want to select one drive for XP or the other for Ubuntu.

Much better then complications with USB and having a USB stick dedicated to just grub. My personal opinion. :)

---

### Post by mirach on 2009-11-13
Thank you Darkod for the detailed instructions - I intend to try them this evening.

Right now I believe I have Grub and Ubuntu on a single partition on my second hard drive (1st in the boot sequence). XP is on my other hard drive.

It sounds like the main difference between your suggestion and what I've got now is that you suggest putting Grub in its own partition on my second hard drive. Will that really get rid of the Error 13? What is Error 13?

Thanks

---

### Post by Ginsu543 on 2009-11-13
Do you have the right entry for Windows XP in your /boot/grub/menu.lst file (I'm assuming you are talking about grub-legacy which comes with 9.04, not grub 2 which comes with 9.10)? It should look something like:

title                 Windows NT/2000/XP
rootnoverify     (hd1,0)
map                (hd0)  (hd1)
map                (hd1)  (hd0)
makeactive
chainloader      +1

The whole "map" business is to make Windows think it's first in boot order when in fact it's not (because the Ubuntu drive is). Depending on how many drives you have, you may have to adjust the (hdX) designation. For example, in my system with four SATA drives, my Windows drive would be (hd2).

---

### Post by mirach on 2009-11-13
It worked!

Here is my original menu.lst created during the Ubuntu (9.04) install:

# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
chainloader	+1


And here is the one that fixed it.

# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

Thank you all very much for your help.

---

### Post by mirach on 2009-11-13
How do I mark this resolved?

---

### Post by Ginsu543 on 2009-11-13
I'm glad you got your problem resolved! Can you mark the thread resolved by editing your original post?

---

