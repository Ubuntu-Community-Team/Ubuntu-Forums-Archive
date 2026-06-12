---
title: "How to fix USB after pulling without unmounting?"
date: 2021-08-18
forum: Hardware
---

### Post by nate5 on 2021-08-18
I'm currently running 21.04.  I've noticed that if I pull a USB flash drive from the machine without unmounting it first, it corrupts something, and I'm unable to mount that USB drive again, gives me permissions errors.  At one point I could still see the device, and tried running fsck on it, but that didn't really fix anything.  Now when I do it, I simply can't see the device (other than in dmseg), and I definitely can't mount it.  Generally, I will make sure to unmount it first, but how can I recover from this if it does it again?  The last time it did this, I even formatted the USB on another machine, and it still won't mount, auto or otherwise.  Obviously an OS reinstall fixes the issue. (I'm still in the experimenting phases of this server, so reinstalling the OS is no big deal at the moment, not to mention I have a decent post install script that makes setup easy.  The fact that it won't work even after reformatting the USB device makes me think something in the OS is messed up, but what?  Any ideas?

---

### Post by TheFu on 2021-08-18
Format it. Don't use a "quick format", do a full format.  Also, choose a good file system for flash.  That would be either f2fs or exFAT.  On most versions of Ubuntu, using those file systems requires installing extra tools.

The OS wouldn't need to be reinstalled. You've lost me there.  The flash drive is just data, right?  BTW, lay down a partition table before creating 1 or more partitions, then format the partitions with the file system you choose.

Don't unplug mounted file systems - EVER.

There are some OSes that run completely from RAM.  Perhaps that would be a better choice if you can't help yourself from pulling the flash drive that has an OS on it?

---

### Post by nate5 on 2021-08-18
> **TheFu said:**
> Format it. Don't use a "quick format", do a full format.  Also, choose a good file system for flash.  That would be either f2fs or exFAT.  On most versions of Ubuntu, using those file systems requires installing extra tools.

The OS wouldn't need to be reinstalled. You've lost me there.  The flash drive is just data, right?  BTW, lay down a partition table before creating 1 or more partitions, then format the partitions with the file system you choose.

Don't unplug mounted file systems - EVER.

There are some OSes that run completely from RAM.  Perhaps that would be a better choice if you can't help yourself from pulling the flash drive that has an OS on it?
Sorry I wasn't clear and should have given more info.  I'm not running this OS from the flash drive.  On a Windows system, I use Rufus to create the bootable ubuntu image.  I also copied my post-install scripts to the usb stick so I can access them after the system is installed.  Then I use the USB stick to install the image to the ssd on my machine.  

Only reason I mentioned reinstalling the OS was because in my testing I was reinstalling the OS anyway for other reasons, and found that the USB mounted fine after that.  I think rufus was formatting the drive FAT32 but I can't remember off the top of my head, I'll take a look at that in a bit.  I even just tested again, I unmounted the drive manually before pulling it out.  Waited a while to put it back in.  Now it simply won't automount like it did the first time.  I'm able to mount it up with sudo, but not sure why automount isn't picking it up.

I think the reason i couldn't mount it before was because I pulled it while it was busy.  But now that I made sure to unmount it while it wasn't busy, it seems to mount ok manually, just not automounting.

---

### Post by TheFu on 2021-08-18
Rufus copies the ISO file over. The ISO includes a hybrid MSDOS/MacOS partition table.  Then, if an outside "data partition" is requested, another partition will be created and formatted.  I haven't used rufus in some time, but **mkusb** supports ntfs or ext4 data partitions.  The core ISO area will be an ISO file system with some extensions.  If a persistent area for OS updates is included, then that will be an overly file system that gets loaded over the base ISO so that **apt upgrade** updates are persistent between boots.

You can see all of this by running the 'mount' command (no options) on the running *Live Ubuntu* environment.  The output will show all the mounts, mount options and file systems used. I promise it will open your eyes so see all the different file systems involved.

The term "automounting" means something very specific. To learn more about automounting, there is a manpage for it.  **man automount** to see it.  Automount and autofs provide manual control and the performance of native file systems with the end-user convenience.

---

### Post by nate5 on 2021-08-18
> **TheFu said:**
> Rufus copies the ISO file over. The ISO includes a hybrid MSDOS/MacOS partition table.  Then, if an outside "data partition" is requested, another partition will be created and formatted.  I haven't used rufus in some time, but **mkusb** supports ntfs or ext4 data partitions.  The core ISO area will be an ISO file system with some extensions.  If a persistent area for OS updates is included, then that will be an overly file system that gets loaded over the base ISO so that **apt upgrade** updates are persistent between boots.

You can see all of this by running the 'mount' command (no options) on the running *Live Ubuntu* environment.  The output will show all the mounts, mount options and file systems used. I promise it will open your eyes so see all the different file systems involved.

The term "automounting" means something very specific. To learn more about automounting, there is a manpage for it.  **man automount** to see it.  Automount and autofs provide manual control and the performance of native file systems with the end-user convenience.
Thanks, I'll look that stuff over.  I'm familiar with autofs, just hadn't looked into it here.  I was just wondering why the out-of-the-box automount only seems to work the first time I plug this drive in, then from then on it stops.  Thanks for the info.

---

### Post by TheFu on 2021-08-18
> **nate5 said:**
> Thanks, I'll look that stuff over.  I'm familiar with autofs, just hadn't looked into it here.  I was just wondering why the out-of-the-box automount only seems to work the first time I plug this drive in, then from then on it stops.  Thanks for the info.

If plugging in a USB device makes that storage accessible and you haven't manually setup autofs, then it is NOT automounting.  It is using udev and either gvfs, gio or udisks to mount.  I've never seen this second method provide the necessary options for good performance for non-linux-native file systems. Not once. Usually there is at least a 30% performance hit.

---

### Post by nate5 on 2021-08-18
> **TheFu said:**
> If plugging in a USB device makes that storage accessible and you haven't manually setup autofs, then it is NOT automounting.  It is using udev and either gvfs, gio or udisks to mount.  I've never seen this second method provide the necessary options for good performance for non-linux-native file systems. Not once. Usually there is at least a 30% performance hit.
Ok thanks.

---

