---
title: "Computer will only boot to live CD"
date: 2009-01-10
forum: Hardware
---

### Post by soad524 on 2009-01-10
One of my computers will only bot to a live cd. We have tried swapping out the hard drive, the power supply and replaced the MBR.

When i boot without a live cd the computer loads the bios then goes to a screen that just has a flashing underscore( _ ). There are no beeps when booted.:confused:

But when a knoppix live cd is in it will boot. I can also view the contents of the hd.

BTW it is a 
HP Pavilion A000
2.5 Ghz
512 RAM

Thanks in advance!

---

### Post by oilchangeguy on 2009-01-10
ok, have you tried the cd in another computer, to verify it works?

---

### Post by soad524 on 2009-01-10
the problem isnt that it wont boot to the cd its that i cant boot to the hd

---

### Post by oilchangeguy on 2009-01-10
> **soad524 said:**
> the problem isnt that it wont boot to the cd its that i cant boot to the hd

ah, my fault. i misread your post. anyway, what is your specific question? if you've done all of the changes to your computer that your first post says. there's not much this forum can do for you.
and i'd suggest using the live cd that will boot, and backing up your hard drive.

---

### Post by soad524 on 2009-01-10
i was mainly wondering if there was anything i had missed

---

### Post by mgol on 2009-01-10
If the problem appears while loading Ubuntu, You can check logs. Just boot using LiveCD, then enter the Terminal (Applications -> Accessories -> Terminal) and mount Your main Ubuntu partition:
```
sudo mkdir /media/root
sudo mount /dev/sdaX /media/root
```
where You must replace X with the number of Your Ubuntu partition. Then post the contents of a file /media/root/var/log/dmesg.

---

### Post by oilchangeguy on 2009-01-10
> **mgol said:**
> If the problem appears while loading Ubuntu, You can check logs. Just boot using LiveCD, then enter the Terminal (Applications -> Accessories -> Terminal) and mount Your main Ubuntu partition:
```
sudo mkdir /media/root
sudo mount /dev/sdaX /media/root
```
where You must replace X with the number of Your Ubuntu partition. Then post the contents of a file /media/root/var/log/dmesg.

mods, please delete my post. thanks! typed a reply, and changed my mind.

---

