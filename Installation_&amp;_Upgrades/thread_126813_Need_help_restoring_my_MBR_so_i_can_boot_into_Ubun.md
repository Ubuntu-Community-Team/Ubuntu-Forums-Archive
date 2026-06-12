---
title: "Need help restoring my MBR so i can boot into Ubuntu"
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by derrick1985 on 2006-02-07
Hey Everyone,

Recently, I got a SATA hard drive and installed it in my PC. the SATA harddrive is now the first HD (should be anyways) and my ubuntu installed is on one of the IDE harddrives. How can I restore the MBR so that I can boot into Ubuntu (on an IDE drive) and Windows too (on SATA) WITHOUT reinstalling. 

Thanks

Derrick

---

### Post by foolosophy on 2006-02-07
You could try making a boot floppy disk of GRUB loader. You can find how to do that in their website (google for it). If I am not mistaken, you had to

format a diskette and then
Code:

```
sudo cd /boot/grub 
sudo dd if=stage1 of=/dev/fd0 bs=512 count=1 
sudo dd if=stage2 of=/dev/fd0 bs=512 seek=1
```

When you boot from this floppie, you have a command line that says "grub>". In order to boot your OS, you need to
Code:

```
root (hd0,6) 
configfile /grub/menu.lst
```

(you can replace "(hd0,6)" for your actual "/boot" partition. Mine is this, maybe yours is hd0,5 or hd0,7)

(to do all this you'll need to access your ubuntu somehow: maybe removing the SATA drive and restoring the IDE HD to where it used to be, or maybe with Knopppix or Ubuntu Live CD.. dunno..)

Once you have your floppy, you should install windows in the SATA drive, and then install GRUB to your MBR, loading to ubuntu from the floppy boot disk and using the command "sudo grub-install /dev/hda"  (instead of hda you should put the one that refers to the SATA drive.. dunno what it is...)

There are some other stuff that I had to find out when I had similar problems.. some of that is in [this thread]("http://www.ubuntuforums.org/showthread.php?t=99085").

I hope you find this helpful.

---

### Post by goatflyer on 2006-02-07
This link describes how to do it depending on your situation.

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

