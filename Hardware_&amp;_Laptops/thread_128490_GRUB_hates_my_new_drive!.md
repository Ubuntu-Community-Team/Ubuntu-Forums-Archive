---
title: "GRUB hates my new drive!"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by atomicbob on 2006-02-11
Here's the scoop:

I bought myself a snazzy new 250GB SATA drive for music and movies and such.  I already have two identical 80GB SATAs for my Ubuntu-XP dual boot setup. and everything works wonderfully.  However, when I plug in my new 250GB drive and boot to Ubuntu, I get the following error after GRUB loads...


Loading, please wait... 
FATAL: module unknown not found. 
mount: Mounting /dev/hdb1 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init 

BusyBox v1.00-pre10 (Debain 20040623-1ubuntu22) Built-in shell (ash) Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off

If I select XP from the GRUB menu, XP boots just fine and I can see my new drive.  The new drive is set to tertiary in the BIOS, with ubuntu and XP primary and secondary, respectively.

It seems that GRUB is not passing the correct drive info to the kernel, but I'm a newb and I don't know where to go from here.  

HELP!!

---

### Post by Derek Djons on 2006-02-11
Have you checked the boot sequence in your BIOS?

---

### Post by atomicbob on 2006-02-11
Yup.

BIOS reports the 2 80's as drives 1 & 2 (the ones holding ubuntu and XP respectively) and the 250GB as drive 3.

On edit:

I am using the ubuntu-XP dual boot script for GRUB that is described in these forums.  I'm a little hesitant to play around with the GRUB command line at boot since the last time I tried it, I ended up hosing my Ubuntu drive, requiring a full re-install (I ended up being unable to re-install GRUB but that's another, unrelated issue).

I've been fooling around with this for a few weeks now and I haven't had much success.  I'm assuming that I need to edit /boot/grub/menu.lst but I don't want to try things blindly lest I render Ubuntu unbootable.

---

### Post by cabber on 2006-03-03
[QUOTE=atomicbob]Yup.

BIOS reports the 2 80's as drives 1 & 2 (the ones holding ubuntu and XP respectively) and the 250GB as drive 3.

On edit:

I am using the ubuntu-XP dual boot script for GRUB that is described in these forums.  I'm a little hesitant to play around with the GRUB command line at boot since the last time I tried it, I ended up hosing my Ubuntu drive, requiring a full re-install (I ended up being unable to re-install GRUB but that's another, unrelated issue).

I've been fooling around with this for a few weeks now and I haven't had much success.  I'm assuming that I need to edit /boot/grub/menu.lst but I don't want to try things blindly lest I render Ubuntu unbootable.[/QUOTE]


I am having the exact same problem.  I placed a new SATA drive in and cannot boot into Ubuntu with the same errors above.

---

### Post by atomicbob on 2006-05-01
Well, I fixed it.  Ubuntu gave me some love.  Or something. 8) 

Anyway...

To fix this "feature" you'll have to hack both /boot/grub/menu.lst **_AND_** /etc/fstab.

I changed /boot/grub/menu.lst from:

title           Ubuntu, kernel 2.6.12-10-amd64-generic Default
root            (hd0,0)
kernel         /boot/vmlinuz root=/dev/**sda1** ro quiet splash
initrd           /boot/initrd.img
savedefault
boot

to:

title           Ubuntu, kernel 2.6.12-10-amd64-generic Default
root           (hd0,0)
kernel        /boot/vmlinuz root=/dev/**sdb1** ro quiet splash
initrd          /boot/initrd.img
savedefault
boot

Note that this directs grub to look at sdb1 for the root directory.  Ubuntu seems to always place the new drive as 'sda' so telling grub to look at the next drive is the most likely option.  Obviously you'll have to change this if your Ubuntu partition is different.  You can make these changes from the grub command line or you can do it from a terminal window and then reboot.  You may get some errors when everything tries to load though and might be dumped to a root shell since the drive integrity can't be verified.  That's OK.

Next step, which can be done from the root shell, is to edit /etc/fstab to include the new drive.

I added changed /etc/fstab from:
/dev/**sda1**       /               ext2    defaults,errors=remount-ro 0       1
/dev/**sda4**       /home           ext2    defaults        0       2
/dev/**sda3**       /tmp            ext2    defaults        0       2
/dev/**sda2**       none            swap    sw              0       0

to:

/dev/**sdb1**       /               ext2    defaults,errors=remount-ro 0       1
/dev/**sdb4**       /home           ext2    defaults        0       2
/dev/**sdb3**       /tmp            ext2    defaults        0       2
/dev/**sdb2**       none            swap    sw              0       0

I also added the new drive's mount point at the same time:

[B]/dev/sda1       /media/Multimedia       ext2    defaults        0       2
[/B]

Reboot and you should be good to go.  I hope this is accurate since I'm doing it from memory.  PM me if you have questions and I should be able to help.  It's like surgery; see one, do one, teach one.  Only I guess I never saw one first...:confused: 

Good luck.  Make backups! ;)

---

