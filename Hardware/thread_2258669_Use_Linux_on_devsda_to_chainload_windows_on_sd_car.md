---
title: "Use Linux on /dev/sda to chainload windows on sd card"
date: 2014-12-29
forum: Hardware
---

### Post by Thomas_Wesolowski on 2014-12-29
I am trying to load windows XP from a SD Card in the internal SD Card slot on my Toughbook CF-18. The bios does not natively support booting from the sd card, and the card is not recognized until I boot into linux on /dev/sda, the internal harddrive.
I attempted to follow the directions from this thread [http://ubuntuforums.org/showthread.php?t=986126&page=3](http://ubuntuforums.org/showthread.php?t=986126&page=3) however i need to modify these so that I can load a windows installation from the SD Card as opposed to a linux installation. I was curious as to how this can be done.

Drives:
/dev/sda - Ubuntu 14.10
/dev/mmcblk0 Windows XP Pro

---

### Post by weatherman2 on 2014-12-29
Are you trying to *install* Windows XP on the SD card?  If so, you are wasting your time.  A Windows installation cannot easily run off of a USB or SD card like Linux can, even if you can get the boot part to work.

It is possible boot a Windows boot disk from USB (and presumably SD), but that's something very different.

You have a better shot at installing XP in a virtual machine in Linux assuming you have Linux on the hard drive now.

---

### Post by Thomas_Wesolowski on 2014-12-29
Was looking to run XP installation from the SD Card for the durability as its much less damage-prone than the old ide hard drive, though it will eventually kill the card. XP is installed to the first partition on the card, I just cant boot it as the bios has no native support for booting from the SD slot.

---

### Post by weatherman2 on 2014-12-29
Have you booted this XP installation on SD card on some other computer?  So you know it works that way?  I would be surprised.  Even if you could, I'd guess it would be painfully slow. 

If you installed XP in a virtual machine, you could store the virtual machine files on the SD card, I guess, and that would avoid the wear-and-tear on the hard drive you are worried about.

In theory the Grub updater should detect the installation automatically if you run the command "sudo update-grub" in a terminal, if it can truly detect a working Windows installation there.  That's how it deals with Windows installed on hard drives.  The guide you linked to above would work for Windows if you could get it to work for Linux with your SD card reader, if it is not automatically detected by Grub.

---

### Post by yancek on 2014-12-29
Have you tried a chainload entry such as the one below.  If so, what happens?  You would need to change the (hd1,2) entry to suit your needs.  More info on what you tried and the results might lead to other suggestions.

> menuentry 'Windows xp' {
insmod ntfs
set root=(hd1,2)
chainloader +1
}

---

### Post by oldfred on 2014-12-30
Windows has always had built in checks to only boot from internal hard drives. That is because it is licensed to only one system so you cannot use a removeable device.

Only if your system sees card as a hard drive may it work. But XP is now so old and not support as it really is not worth the effort. It is just about to the point of being dangerous to run if you at all connect to Internet.

---

### Post by 4-null-nan on 2014-12-30
if solid state drive is what you referred to as reliable, it's not so hard to replace the hard drive with a solid state drive.
As other pointed out, it would be very hard to run it on a non "C" drive.  So install is hard, and run it even harder.
For installation, it is possible by installing into a regular hard drive, and possibly copy it over, and then you fix the boot loader later, but that's only if you can boot off from the SD card running Windows, is probably is almost impossible, unless, you run somekind of virtual "thin" machine (type 1 hypervisor) to fake it somehow.  A regular "thick" virtual machine can easily do that, so no need to discuss here.

---

