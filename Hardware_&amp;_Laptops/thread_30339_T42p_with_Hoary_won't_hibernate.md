---
title: "T42p with Hoary won't hibernate"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by egibbs on 2005-04-28
This is strange - everyting I've seen says hibernate works out of the box, but not for me.  The system looks like it's going to hibernate, writes to disk for 30 seconds or so, turns the backlight off, then turns the baclight back on and brings the desktop back up (or if I have the screen saver enabled brings up the screen saver).

Suspend to RAM works fine - even with close and open the lid - but hibernate refuses to behave.

I've followed the instructions in the Ubuntu on IBM T42 HowTo found here [http://resolute.ucsd.edu/diwaker/articles/howtos/howto-t42-ubuntu.html](http://resolute.ucsd.edu/diwaker/articles/howtos/howto-t42-ubuntu.html) and elsewhere, including:

Got the 686 kernel
Set ACPI_SLEEP=true in /etc/default/acpi-support (yes, I know this should only affect suspend to RAM)
Installed Thinkpad Buttons, they work.
Added resume=/dev/hdc3 to the #kopt line in /boot/grub/menu.lst and run update-grub (yes, my Linux drive is hdc and the swap partition is 3).

I checked my swap partition and it is 2.5 GB.  I have 1 GB of RAM, so I would think that is plenty big enough.

I've googled and googled and searched the Ubuntu forums and I've found a few people who have trouble waking their machines from hibernate, but only one post with a problem similr to mine, and they had no replies.

Anyone have any ideas?

Thanks,

Ed Gibbs

---

### Post by egibbs on 2005-05-02
I fixed it - for any other noobs struggling with this the Linux swap partition is 5, not 3.  You know, it's as easy as 1,2,5...

Ed Gibbs

---

### Post by kvidell on 2005-05-07
[QUOTE=egibbs]I fixed it - for any other noobs struggling with this the Linux swap partition is 5, not 3.  You know, it's as easy as 1,2,5...

Ed Gibbs[/QUOTE]
 My 42p hibernated the second I finished the install, I had to do some hackery to get it to suspend though..
```
kernel          /boot/vmlinuz-2.6.10-5-686 root=/dev/hda1 ro quiet splash apm=on acpi=off nolapic
```

---

