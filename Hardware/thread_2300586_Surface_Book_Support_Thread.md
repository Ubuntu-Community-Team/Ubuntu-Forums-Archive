---
title: "Surface Book Support Thread"
date: 2015-10-26
forum: Hardware
---

### Post by Hugh_Kolias on 2015-10-26
Thought I would kick off a thread for the Surface book. I've tried running 15.10 and the latest LTR 14 and both seem to have quite a few issues. USB, keyboard/trackpad, touchscreen does not work. It appears wifi is working (says it has found networks, but its impossible to verify since there's no way of navigating to connect). You can actually undock the tablet from the keyboard, however when you reconnect it, linux crashes and throws up an error related to PCIE.

Hopefully we can get it up and running soon!

---

### Post by jbfoley1 on 2015-12-01
I was able to get it to install 15.10, but no joy getting grub or anything else to boot to the installation once it's on the hard drive.  I have the sequence correct but it only hangs.  I was going to try rEFIt due to some positive comments I've seen about it on Surface Pro 3, but there does not appear to be a package for it on 15.10 yet.  For next steps I'll either make one or possibly try 15.04.

Some notes:
- Have to disable secure boot from the UEFI BIOS.  Hold volume up button while pressing power button when you power the machine on, then release volume up when you see the Surface splash.  It will go to BIOS after a few seconds.
- GRUB bootloader loads from the USB drive just fine.
- Built-in keyboard, trackpad, and touchscreen don't work booting from the USB, but wifi works perfectly.
- I had no problem with external keyboard and mouse through the USB 3.0 connection on the base of the book.  Since there was only one left after plugging in the USB drive, I had to use a keyboard with a USB hub built in.  I used a Das Keyboard 4, which has a USB3.0 hub in it.  I don't know if that was significant, but it did not appear to be.  I also tried an older hp-branded wireless USB 2.0 keyboard and it worked.  A Microsoft arc mouse and a wired Microsoft comfort mouse 3000 also worked fine either directly plugged or through the Das Keyboard hub.
- I used Gparted to shrink the main Windows partition.  The built-in version and the latest repository version don't detect the NVMe SSD.  I had to install version 0.24 from a 64-bit .deb package that I found here: [http://www.ubuntuupdates.org/package/getdeb_apps/wily/apps/getdeb/gparted](http://www.ubuntuupdates.org/package/getdeb_apps/wily/apps/getdeb/gparted) 
- The disk partition type is GPT, as expected.  Good thing, because Microsoft had already installed 4 primary partitions with recovery tools, etc.  It was no problem at all to install two more primary partitions with this partition type.  (well, maybe that remains to be seen, since I still haven't gotten it to boot to one of them yet.)  The pre-existing partitions were as follows:
 -- nvme0n1p1: EFI system partition Fat32 260.00MiB
 -- nvme0n1p2: Microsoft reserved partition unknown type 128.00MiB
 -- nvme0n1p3: Basic Data Partition/Windows NTFS ~500 GiB or bulk of the drive
 -- nvme0n1p4: Windows RE tools NTFS 830.00MiB
- I had a 512GB SSD, so I shrank the main Windows C drive down to 128GB, created a 256GB NTFS "shared" drive after it as nvme0n1p5, then left the rest ~100GiB unformatted space for the Ubuntu installer.  All of this sat between p3 and p4 on the disk.
- I actually rebooted the USB ubuntu after  to let it run the installer option from the GRUB menu because I've had more success with that method in the past.
- Ran the Ubuntu installer normally, even got 3rd party stuff because wireless was working fine.  I let it automatically install next to window, nothing fancy with the partitions.  It chose to make nvme0n1p6: ~85GiB EXT4 and nvme0n1p7: ~16Gib swap partitions in the un-partitioned space.  There were no error messages or anything like that.
- On next boot, I went to the UEFI bios, "ubuntu" was recognized in the boot list.  I moved it to the top of the order and exited.
- On next boot, it was a bit slow to start, then...  Windows.
- I tried going to the boot menu (hold volume down while booting) and choosing to boot to a device.  Ubuntu showed in that list.  When selected that way, though, it just hangs.
- I also tried efibootmgr from the USB boot.  That sees the same order I'd set from the UEFI bios menu.  I tried re-ordering it with that tool, but same results.

It looks to me like the EFI bootloader/GRUB is not installed properly.  I'm wading through various forums to find alternative methods and instructions.  It seems to be very close, just missing a few things.  Once that's done, we can start worrying about drivers.

I seem to be at the same place as update 5 on this Reddit thread: [https://www.reddit.com/r/SurfaceLinux/comments/3qcqha/ubuntu_on_surface_book/](https://www.reddit.com/r/SurfaceLinux/comments/3qcqha/ubuntu_on_surface_book/)  He got it working in update 7, which is encouraging, but not helpful because he doesn't know how!  It is encouraging to see that he made progress on the keyboard and touchpad drivers.  

If I figure out the boot thing, I'll post it here.

---

### Post by ashok6 on 2015-12-01
As another point of reference, I used a 15.04 Kubuntu LiveCD, not 15.10, and had no problems installing using a similar procedure to you.  I have since updated to 15.10 and still can boot without issue.  I have not yet installed a custom kernel with the keyboard and touchpad drivers.  This is for a non-discrete GPU surface book.

---

### Post by Hugh_Kolias on 2015-12-01
Similar to ashok6, GRUB doesn't seem to install properly on 15.10... I tried it multiple times to no avail. 14.04 worked flawlessly (and it sounds like 15.04 works as well as per ashok6). I haven't been able to find a reasoning.

I started the reddit thread and should probably clean up the wording a little... let me know if you have any issues. Once you install the kernel everything works flawlessly on 14.04.

---

### Post by lejono on 2016-02-12
Sorry, Hugg and Ashok are you saying everything works on 14.04 including keyboard, touchpad, touchscreen, stylus?? 
I had all those issues with the Lenovo Helix, and after upgrading to the mainline kernel and posting a bug request, the kernel-iinput developers were blazingly fast in patching it so that keyboard and touchscreen worked.

---

