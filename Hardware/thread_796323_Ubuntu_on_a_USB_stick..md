---
title: "Ubuntu on a USB stick."
date: 2008-05-16
forum: Hardware
---

### Post by BoomAM on 2008-05-16
Hi.
Im looking at installing Ubuntu on a USB stick.
Whilst im aware that theres hundreds of guides around to do this, im looking for a guide that'll show me how to install Ubuntu on a stick that can be used with ANY system, and that will minimise the numbers of writes it does to the stick.

Any suggestions?

Thanks in advance all. :).

---

### Post by cendant on 2008-05-16
[http://ubuntuforums.org/showthread.php?p=4972589&posted=1#post4972589](http://ubuntuforums.org/showthread.php?p=4972589&posted=1#post4972589)

---

### Post by issih on 2008-05-16
Have a look at [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) lots of easy to follow guides there for various distributions. If you want ubuntu you are looking for the "persistent" installs to end up with what is basically a live cd writing data back to the usb. That gives you a stick that will probe the system it is plugged into and do its best to adapt to the new hardware (like a live cd) but gives you storage capability... It works pretty well, its just a smidge slower (although that probably depends on the usb stick IO speeds).

---

### Post by cendant on 2008-05-16
I personally prefer IsoToStick method - saves time

---

### Post by picopir8 on 2008-05-16
Most (all?) of these solutions simply put the liveCD on a flash card.  You can customize some packages but the overall install is a bit bloated.

If you prefer to take and existing install which is customized to only have the packages you want, then you can follow this tutorial to get it to run off a flash card.
[http://oopsilon.com/Booting-Linux-from-Flash](http://oopsilon.com/Booting-Linux-from-Flash)

I tried it a few weeks back and it worked well though a few steps needed to be tweaked because the tutorial is a little dated since it was written back before gutsy came out.


The one problem though is that as this tutorial is written, it may not work on every system.
To get around that, use the initrd.gz file from a liveCD, extract it as follows:

```

mkdir /tmp/initrd/
cd /tmp/initrd
gzip -dc REPLACE_ME_WITH_PATH_TO_LIVECD_INITRD | cpio -id

rm -rf /tmp/initrd/lib/modules/REPLACE_ME_WITH_YOUR_KERNEL_VERSION
rm -rf /tmp/initrd/lib/firmware/REPLACE_ME_WITH_YOUR_KERNEL_VERSION

cp -a /lib/modules/* /tmp/initrd/lib/modules/
cp -a /lib/firmware/* /tmp/initrd/lib/firmware/

find . | cpio --quiet --dereference -o -H newc | gzip -9 > /root/initrd.gz

```

Use this initrd.gz instead of the one from the tutorial.  Also make sure your squashfs image from the tutorial is named "filesystem.squashfs" and placed in a directory on the flash card named "casper".  If you follow this procedure using a 32 bit x86 kernel, then it should work on any x86  computer.

---

### Post by issih on 2008-05-16
From the quick look I just did (and I admit it was quick) isotostick is about getting a live cd image onto the usb stick as is:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

That is not what is wanted, the original poster wants a live style install that he can still store data on, hence he needs to set up a persistent style install. If isotostick can do this then all well and good, just point him in the right direction :)

the fact that you need a specific partition structure, a patched initrd file and need to specify the persistent kernel boot option in the boot loader, to achieve a persistent install, makes me doubt isotostick will cope all on its own, but feel free to prove me wrong

---

### Post by az on 2008-05-16
How to set up a live usb stick with ubuntu with persistent home:
Partition the usb drive to have two partitions.  One should be 700 Megs large, bootable and fat16.  The second should be ext3 and labeled casper-rw.

Next, mount the ubuntu iso image and copy all files to the fat16 filesystem.  Move all the files from the isolinux folder to the folder beneath it (the root folder of the fat16 filesystem).  

Change the file named isolinux.cfg to syslinux.cfg.  Edit the file so that the word persistent appears in the default stanza:
example:
*append  file=/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.gz quiet splash --*

Install syslinux and run

sudo syslinux /dev/"whatever"  (Use the correct name for your device and partition: Ex sdc1)

Install an mbr onto the device. 

sudo apt-get install mbr

sudo mbr-install /dev/"whatever"  (Use the correct name for your device. In this case, ot would be the device, not the partition: Ex sdc)

Boot the device.


see
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by BoomAM on 2008-05-17
The persistant LiveCD appears to an attractive option, but purely because it'll scan for HW on each boot.
But it cant be updated, or programs added to it unfortunatelly. :(.

Is there not a way to have an installation on USB stick that *can* be updated, but not have it so it writes so often it kills the stick?

---

### Post by ASULutzy on 2008-05-17
2 GB USB sticks are like 10 bucks on newegg now a days, I wouldn't be that concerned with the number of read/write cycles you're using on it.

I will say that having a persistent mode boot has been very very useful for me, as Ubuntu will not setup my wireless out of the box, so I've copied over my wireless drivers as well as the ndiswrapper package to the persistent part of the live-cd. Very useful, and I wish I would have seen this thread before I already made mine, as the tutorials here were very concise! Kudos

---

### Post by az on 2008-05-19
> **BoomAM said:**
> The persistant LiveCD appears to an attractive option, but purely because it'll scan for HW on each boot.
But it cant be updated, or programs added to it unfortunatelly. :(.

Is there not a way to have an installation on USB stick that *can* be updated, but not have it so it writes so often it kills the stick?

You can install packages in a live session.  They take up a lot of room in your persistent home, but it can be done. 

I wouldn't do an update, but I would carry around  a persistent home with a few extra packages.

---

### Post by BoomAM on 2008-05-22
Right, so ive finally got a bit of time here at work:

What i want to do is have a version of Ubuntu that i can run off a USB stick, that auto detects the hardware on each boot, and where i can install programs/updates and save data.

So what i need is a persistant install?

---

### Post by probono on 2008-05-22
You could make a bootable >= 2GB USB stick, e.g., using the [tool]("http://klik.atekon.de/liveusb/") I am developing. Initially, this is just the same as a Live CD, and you can change things and install applications into the Live system.

Now, to make these changes permanent, you need to re-create the main squashfs file using mksquashfs (depending on the speed of your USB sticks, this can take about 3-5 minutes), and replace /cdrom/casper/filesystem.squashfs with your new one. 

Then you have a "remastered" Live USB system that includes your new applications.

This method has the advantage that usually nothing is written to the USB stick, only when you explicitly want it.

---

### Post by BoomAM on 2008-05-22
What would following this guide give me:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Apart from, im asuming, the ability to boot on any hardware and a partition for storing data?

---

