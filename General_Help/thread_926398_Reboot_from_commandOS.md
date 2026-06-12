---
title: "Reboot from commandOS"
date: 2008-09-21
forum: General Help
---

### Post by Gizkaguy on 2008-09-21
Hello! I am a medium - skilled computer user, and would like to know if there is a nice command line utility for rebooting into a different OS.

I have Slackware 12.1 and Ubuntu 8.04 dual booting, with Ubuntu installed second and default for booting.

I would like to know how to, from the command line and running Ubuntu, reboot and have Slackware load (for SSH), and vice versa.

I have looked at grub-reboot, but it does not seem to work for me - it always boots into Ubuntu. If someone could explain to me how the grub numbering system works, that would be awesome.

Thanks! :)

---

### Post by Gizkaguy on 2008-09-21
Sorry ... that post seemed a bit deranged.

I edited it to be clearer ... anyone get it now? :D

---

### Post by lisati on 2008-09-21
The command "shutdown" has a "restart" option (-r), but I'm not sure how to work the automatic choice of OS beyond grub's default into the picture.

---

### Post by pieoncar on 2008-09-21
If you look at /boot/grub/menu.lst, there should be a line saying "default 0", meaning the first entry in grub will be the one that gets booted if you don't press a button.  You might be able to set up a shell script to change that to "default 1" to boot from the second entry...  

That would be a nice little sed or perl exercise :)

You might be able to just do an "echo default 1 >> /boot/grub/menu.lst" and grub MIGHT only look at the latest declaration of default in the file, but that's pretty messy.

---

### Post by niteshifter on 2008-09-22
Hi,

From:
```
man grub-reboot
```


> NAME
       grub-reboot - manual page for grub-reboot 0.01

SYNOPSIS
       grub-reboot entry [options to grub]

DESCRIPTION
       grub-reboot

       Reboots into the specified OS entry in menu.lst

              (where "entry" is the entry number in menu.lst)


---

### Post by Gizkaguy on 2008-09-22
Aha! I was looking at my system, and I discovered that there were not 4 Ubuntu entries, for various variations of the kernel and recovery modes, as I had thought, but 5, with one hidden for some reason, but booting to normal ubuntu, outlined like this:

0 = Ubuntu kernel-something-or-other
1 = Ubuntu kernel-something-or-other recovery
2 = Ubuntu kernel-something-or-else
3 = Ubuntu kernel-something-or-else recovery
4 = Ubuntu memtest86+
5 = Other Operating Systems (there as normal menu text)
6 = Slackware

This, as far as I know, was the default. So, I was not counting "Other Operating Systems" as a menu entry, and #4 was hidden. I thought it went like this:

0 = Ubuntu
1 = Ubuntu recovery
2 = Ubuntu 2
3 = Ubuntu 2 recovery
4 = Slackware

So I did get grub-reboot right, in a way, but it booted Ubuntu, not Slackware. Now, I think I have it. Thanks everyone for helping!

---

