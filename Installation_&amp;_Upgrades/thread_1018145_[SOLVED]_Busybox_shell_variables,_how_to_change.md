---
title: "[SOLVED] Busybox shell variables, how to change"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by Omega Xi on 2008-12-21
Ok, first off, let me try and explain the situation I've landed myself in.  I installed ubuntu on a computer which already had gentoo on it by chrooting into an install made using debootstrap. Everything went pretty well except one horrific snag (which I will admit, is entirely my own fault).  While I wan in the chrooted enviroment, I copied my /etc/fstab from the gentoo install to the ubuntu one, edited a few things so it would all mount correctly, added ubuntu to grub and then rebooted.

The first problem I noticed was that I had accidentally set grub to have a timeout of '0'. The second problem was that ubuntu names my hard drive /dev/sda where gentoo called it /dev/hda.

The upshot of all this is that I cannot currently boot either OS because grub flashes on the screen for  a fraction of a second and defaults to ubuntu which then presents me with busy box which  complains because it can't find /dev/hda4 (the partition with ubuntu, on it a.k.a. /dev/sda4 ^^; ).  This wouldn't be much of a problem if I could access grub as I could simply change ubuntu's entry in grub.conf to root=/dev/sda4 then boot into gentoo and change the 'h's in ubuntu's /etc/fstab to 's's.  however at the moment this doesn't seem to be an option.

One odd thing is that busy box even tells me that I should change $ROOT to /dev/sda4 however whenever I set the value of the $ROOT variable, it is reset whenever I try to exit busybox.

Also, just to make things even more fun ^^; Using any kind of alternative boot devices (USB, CD, floppy) isn't  possible as the computer has no working optical drive, no floppy drive and cannot boot from USB drives.

Any ideas? ^^;

---

### Post by Omega Xi on 2008-12-21
Okay no-one was biting so I had to fix it on my own, in case anyone ever runs into the same problem though here is a possible solution.

While busybox seems to be totally castrated (you can use tools like cat and more but there is no text editor such as vi for some bizzare reason) you can use it to chroot into another environment, mount works in pretty much the same way in busybox as it does anywhere else, so you can mount another filesystem and chroot to the installed environment on that file system.

For example:

```
#mkdir ubuntu
#mount /dev/sda2 /ubuntu -t ext3
#chroot /ubuntu
#vi /boot/grub/grub.conf 
```

Also you might find this useful:
[http://manpages.ubuntu.com/manpages/hardy/man1/busybox.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/busybox.1.html)

If you're ever stuck in the same situation, I hope this helps somewhat ^_^

---

