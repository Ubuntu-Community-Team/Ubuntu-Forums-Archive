---
title: "probs with CD-less install"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by dcottingham on 2009-01-30
I am attempting a CD-less install of kubuntu 8.10 desktop on an old machine. Following [ "Installation from hard drive with floppies"]("https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies") I format a partition and copy vmlinuz and initrd.gz from the iso (both were in /casper on the iso). Then I stick in a grub floppy and attempt to boot.  The boot params the cited page recommends are:

kernel /vmlinuz append vga=normal initrd=/initrd.gz ramdisk_size=16384 root=/dev/rd/0 rw --

After a lot of booting chitchat it complains about the nonexistence of /dev/rd/0.  Tried again with root=/dev/ram0, same results.  Tried omitting root=, still no joy. Anybody got a suggestion what boot params will work?

---

### Post by dstew on 2009-01-30
That HowTo is pretty old (written for 5.10). A note at the bottom says to boot 6.10, just use```
root (hd0,1)
kernel /vmlinuz
initrd /initrd.gz
boot
```You might need to change the argument of the root statement to match your root partition. If it is /dev/hda1, then the root statement would be```
root (hd0,0)
```
Maybe that will work for a later version of Ubuntu like you are using.

---

### Post by dcottingham on 2009-01-30
Yeah, I saw that, and I tried that too.  Still no joy.

---

### Post by dcottingham on 2009-01-31
Turns out this works if you use the alternate iso instead of the desktop iso.  The right boot params to grub in this case are the ones pointed out by dstew above, that is, no params.

Still don't know how to do desktop, but alternate is good enough for me.

---

