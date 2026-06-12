---
title: "Have we fixed ubuntu's use of GRUB yet?"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by unyalli on 2008-12-24
Thanks for the efforts folks, ubuntu is great.

I've been reading and battling for days now. Can't figure out which post to reply to so started a new one. 8.10 server will not boot. Desktop will install and boot but server will not. Clean install no dual booting all partitions whacked by creating new partition table or by just deleting, new partitions created manually or guided no matter. I've been around and around.

**Tried the following machines:**
IBM xSeries 206m with PATA CD and HD and SATA fakeraid.
Proliant ML330 G2 with PATA CD and PATA fakeraid.
Home built ASUS with PATA CD and SATA HD no RAID. I've tried both 32 and 64 bit on the ASUS.


**[COLOR="Red"]GRUB is GRUB right? Why will desktop install it correct and server not?[/COLOR]**

Oh yes, Merry Christmas!!

---

### Post by cariboo on 2008-12-24
Can you boot using the boot from hard drive option using the LiveCD. It would also be helpful if you told us what kind of error message you are getting when trying to boot your server. More information means more help.

Jim

---

### Post by unyalli on 2008-12-24
It's the timeout then initramfs thing I've read so much about.

All though I felt I tried pretty much everything rest assured I missed one. Have not tried booting from hard disk with with live CD after installing server with server CD. Not sure why I would do this but ok, I'll try it and respond.

Thanks

is there a difference in
/boot/vmlinuz-2.6.27-9-generic
and
/boot/vmlinuz-2.6.27-9-server
??

Is something missing in the server kernel causing all these SATA problems?

---

