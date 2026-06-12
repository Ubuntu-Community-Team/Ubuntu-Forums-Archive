---
title: "Can't use USB hard drive"
date: 2011-02-01
forum: Hardware
---

### Post by lesliek on 2011-02-01
I'm using v 10.04 on a Dell Inspiron 1501.

When I plugged in a USB hard drive in the past, sometimes an icon for it appeared on the desktop, sometimes not. When it didn't appear, I solved the problem by unplugging the drive and replugging it in or by rebooting the computer. Lately, however, the icon's stopped appearing altogether, no matter what I do, and I can't figure out how to access the drive.

When I run dmesg after plugging the drive in, I get:

usb 1-3: new high speed USB device using ehci_hcd and address 3
usb 1-3: configuration #1 chosen from 1 choice

When I run lsusb, I get:

Bus 001 Device 003: ID 0bc2:2000 Seagate RSS LLC Storage Adapter V3 (TPP)

However, not only do I not get an icon for the drive on my desktop, I can't find an icon for it in the "Computer" window.

When I run sudo fdisk -l, all that appears is information about my internal hard drive.

How do I mount the drive so that I can use it? I don't mind doing it manually each time.

Thanks,

Leslie

---

### Post by friv_livs on 2011-02-01
**Manual mount from command line:**

sudo mkdir /temp-drive

sudo mount /dev/sd[letter][#] /temp-drive

replacing [letter] and [#] with that drive's info.

to unmount: sudo umount /dev/sd[letter][#]

**Also:** "sudo fdisk -l, all that appears is information about my internal hard drive."

Have you checked the drive's physical health?

Feel for how it's spinning up and down while being plugged and unplugged.
A cheap stethoscope works wonders for this.

If it doesn't feel or sound smooth, or clicks, screeches, ... the physical aspect is the problem.

---

### Post by lesliek on 2011-02-01
Thanks for replying friv_livs.

Re the physical health of the drive, when I boot up the same computer in Windows and plug the drive in, it works normally, so I'm not worried about the drive's condition.

Re using the mount command, I don't know the correct info for the drive (say sdb1 or whatever). I thought I might get that by using fdisk, but I didn't. Is there some other way to get it or to assign it, say by using the information I got from lsusb?

Thanks again,

Leslie

---

### Post by lesliek on 2011-02-01
Thanks for replying friv_livs.

Re the physical health of the drive, when I boot up the same computer in Windows and plug the drive in, it works normally, so I'm not worried about the drive's condition.

Re using the mount command, I don't know the correct info for the drive (say sdb1 or whatever). I thought I might get that by using fdisk, but I didn't. Is there some other way to get it or to assign it, say by using the information I got from lsusb?

Thanks again,

Leslie

---

### Post by friv_livs on 2011-02-01
You can try gparted from the repos for getting sd[letter][#] information.

If that doesn't work, download and burn a partedmagic disk from here:

[HTML]http://sourceforge.net/projects/partedmagic/[/HTML]

Then see how your external drive plays with that liveCD environment.

partedmagic also has drive testing and recovery tools.

Beyond that, someone else will have to help you.

---

### Post by lesliek on 2011-02-01
Thanks for your further reply.

Your reference to a live CD reminded me of what I should've mentioned before, but forgot to. Before posting originally, I'd burnt a live CD of Knoppix, booted up with it and plugged in the USB hard drive. It was recognised by Knoppix, so it's something about my Ubuntu installation.

I had gparted installed. I tried it on your suggestion but it didn't acknowledge the USB hard drive.

Thanks again,

Leslie

---

