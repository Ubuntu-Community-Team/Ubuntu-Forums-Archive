---
title: "Hard Disk Order"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by hartz on 2006-10-02
Hi,
I am having some problems with Ubuntu (Linux) device tree node creation, particularly hard disks.  I am used to having much control over this process in Solaris, and cannot discover how to do the same in Linux, but I am still learning.

Firstly, if I plug in a USB drive, it appears that Linux just creates a node for it in /dev, eg if I only have an entry for /dev/sda, then the first USB drive becomes /dev/sdb, which is probably jsut the next available entry (What happens if you have more than 26 drives?).

If I plug in a hot-pluggable eSata drive, I see an entry in various logs indicating that a new device has been detected on nv_sata, but nothing gets created in the device tree.  I assume that with a little fidgetting about I could discover the major and minor node numbers and do a mknod or something similar, but I bet this has been automated somewhere already, so let me not re-invent the wheel here.  Manually running mknod would allow me to control what device gets what device name under /dev, but I would rather set up some rules and have it happen automatically .....

0. I am running a 2.16.15-27 386 kernel.
1. My motherboard ([GA-K8NXP-SLI]("http://www.neoseeker.com/Articles/Hardware/Reviews/gak8nxpsli/")) has got two S-ATA controllers.  Linux sees any drives on the nv_sata first, then it recognizes the drives on the SI3114 controller.
2. I have Linux installed on a drive conencted to the SI chip because it supports NCQ, as does the drive.  On a side-note:  how can I check that NCQ is actually being used, and even better, how much of an effect it has got?
3. I have a lot of data on drives set up as non-raid devices.  These drives are currently disconnected for various reasons, which will become clear shortly.
4. Motherboard pseudo-raid Sucks for many reasons, but for me the two most important ones are the fact that I cannot move a raid from one controller type to another (because initializing a drive into a raid destroys the data on that drive (It appears)), and you cannot change raid layout / type, even just to add a mirror, to an existing drive full of data.  (May be different with some controllers).
5. If I configure an extra drive on the SI3114 controller, it becomes the second drive (hd1,0), and everything is fine.  However my drives have a lot of data on them (In the region of 700 GB), and are not set up as any kind of RAID, so I have to use them on the nv_sata controller because I cannot take the SI3114 ports out of raid mode, meaning that I would have to initiate the drives as raid devices (even if only JBOD) to use them on the SI3114 controller, which would cause me to lose the data.
6. If I configure (read: plug in and reboot) a drive on the nv_sata, this drive becomes hd0,0, and the system won't boot up (It does not mount the root file system)
7. This appears to me to be related to the new/extra drive becomming /dev/sda, which is configured in /etc/filesystems as the root disk.

So my question is this: How do I control what device (physical) becomes what entry in /dev/sd.... (alias), in Linux?

Thanx,
  _Hartz

---

### Post by hartz on 2006-10-02
I can't believe I'm having to resort to this, but... BUMP.

---

### Post by hartz on 2006-10-03
Anybody (Bump)

---

### Post by egd on 2006-10-14
> **hartz3 said:**
> Anybody (Bump)

Would love to help you but I'm afraid I don't have the knowledge to.  My experience with these forums is that questions that are not run-of-the-mill often go unanswered - I'm guessing because nobody participating knows the answer.

---

### Post by ScottHW on 2006-10-23
I'm interested in this issue for a slightly different reason.  I sometimes use different external drives (I have Ubuntu booting from one) and I need to get the drives to be constantly identified so I can update my GRUB files.

I found this posting:
[http://www.linuxquestions.org/questions/showthread.php?t=486730](http://www.linuxquestions.org/questions/showthread.php?t=486730)

... which seems to address the same issue, and even suggests a solution based on *udev* although I'm pretty sure I don't understand it at this point.  The *udev* documentation linked from that post says that it is written for those who are familiar with recompiling the kernel, and at this point this is not me.
Maybe someone else here will be able to translate for me/us?

---

### Post by hartz on 2007-01-08
Just an update on this little ongoing saga / battle in my study:

I have read a lot about UDEV and experimented with it.  Initially it did not work for me, but after upgrading to Edgy Eft and builing 2.6.19.1 it is now working.  I admit my understanding of UDEV is still incomplete.  Note: I did not test thoroughly between installing the Edgy Eft upgrade and doing the Kernel build, so it might have worked even before I upgraded my kernel.

I suspect that in Edgy Eft, UDEV has been made part of the initrd image or something, because in the old distribution it seemed that UDEV wasn't working yet by the time my fstab was being read.  

The solution still needs some work.  In particular, if my drives change, I need to manually edit the grub menu, in particular the root (hd0,0) bit becomes root (hd1,0) or hd2,0 or whatever.  Also, I need a UUID for SWAP. ... P.S.  Currently, finding the right parameters to use on the root = (hdX,Z) part is a bit of a guessing game for me... Does anybody know how you can tell the device number change / effect of adding a new device?

This is so frustrating that I suspect I will just get myself an IDE disk to boot from, and let the system mount and run from S-ATA drives once the boot process is completed.  But at least as far as booting in an environment where disk drives change a lot, Edgy EFT is working much better than previous releases.

---

### Post by 4ms on 2008-02-21
Hello,
I didn't find this thread earlier and created a new on with much the same info at
"disk logical name changes on reboot"
[http://ubuntuforums.org/showthread.php?p=4371120](http://ubuntuforums.org/showthread.php?p=4371120)

Does not look like there is a solution, however.  I like your idea of using and ide boot drive.  Did that solve the issue for you?

joseph

---

### Post by hartz on 2008-02-22
Hi 4ms,

It is working, but it remains a work-around and even then not always.  In particular part of the problem lies with grub, which uses the same idea of scanning all the available disks and numbering them (and just to make things confusing, it doesn't use the same naming convention that you find in the /dev tree, i stead it uses names like hd0,0, hd1,0 ... And USB can creep in here too.

I think the boot disk search order in the BIOS also plays a role though I have not yet had time to test this theory.

I must say the process did become more resilient in the past few months, but still far from perfect.  The other day when I did an upgrade on a computer with two drives, the first for MS Windows, the second for Linux, and having left some thumb drive plugged into the USB port while installing, it left me with a very weird situation.

After installing Ubuntu 7.10, the computer could then boot only when a non-bootable disk is in the DVD drive.  How weird is that.  I played around with BIOS boot order settings, checking / not checking the CD ROM for booting, and different settings in grub.  What makes this sad is that this happened while converting a Windows user to Linux, and I did not have time to troubleshoot what was going on there.  Because of boot-up frustrations, and only because of that, the person is now back to running Windows.

I would probably have been able to fix it if I had time to run through the install process again, or even if I could troubleshoot (and learn about grub in the process), but like I said I didn't have the time.

Sigh.

---

