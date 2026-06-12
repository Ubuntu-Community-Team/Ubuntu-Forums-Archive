---
title: "Dual Booting and GRUB issues"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by fsenzeru on 2009-01-30
My girlfriend and I have been trying to set up her computer to dual-boot Ubuntu 8.10 with an existing Windows XP installation, and we are having many many problems that we have not been able to solve yet.

We started with a full windows partition, which the ubuntu installer obligingly turned into windows, ext3, and swap for us on the first try of installation. Everything seemed to be going well, but when we rebooted the machine, we got a GRUB Error 18.  Some research told us that this typically occurs because the BIOS can't read far enough on the hard disk to find the boot-loader, or something to that effect.  The suggested solution was to create a small partition (~32M) at the beginning of the disk and boot from that.  So, we fired up gparted and created the partition, then did the ubuntu install again, using the small ext2 partition for /boot.

This got us to a point where we could actually boot the computer - ubuntu and windows both loaded fine.  However, ubuntu had some issues installing updates: it had eaten up all of the space on the /boot partition and apparently needed to put some more stuff there.  Finding the source of this error on the internet, it seems that 32M is not large enough for /boot - one person suggested it would need to be as big as 500M, and these people also seem to think there is no reason to have /boot on a different partition from /.

This led me to believe that perhaps I'd been mistaken in my understanding of what the small partition was to be used for, so we moved the files off of the partition, unmounted it (and edited the corresponding line in /etc/fstab), and then moved the copied files into a normal /boot folder.  I then ran through the grub restore steps found here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) (though I didn't do it from a live cd), with the hope that this would put the necessary bits of grub at the beginning of the disk.  We rebooted the computer, and are now staring once again at GRUB Error 18.

I'm pretty much out of ideas, except to size up the boot partition to 500M or larger, but this is not ideal, since that will require moving the windows partition again which, among other things, takes a long time.  Does anyone else have any ideas what the problem might actually be, and how to fix it?

Many Thanks,
fsenzeru

---

### Post by utnubuuser on 2009-01-30
There's nothing wrong with having a seperate /boot partition.  If that's what it takes, than by all means.
Is your hdd too small to afford the 500megs of space?

---

### Post by caljohnsmith on 2009-01-30
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what might be the best solution for your Grub error 18.

---

### Post by fsenzeru on 2009-01-30
She's decided that she just wants to increase the size of the boot partition at the beginning... since it did in fact boot when we were running things from there, and just needed more space, this should be a viable solution.

Thanks for the ideas, hopefully this will work.

---

### Post by dstew on 2009-01-30
You don't need to increase the size of the /boot partition, just remove the oldest kernels using Synaptic. That will free up space.

---

