---
title: "Waiting for device... sda4 etc... forever on boot"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by jago25_98 on 2009-11-03
I did a dist-upgrade to karmic by changing sources.list because 
the ubuntu upgrade script couldn't see the update as available...

unfortunately now when I boot all I get is 

`waiting for device... sda4`
`waiting for device... sda3`
and so on, with all the mounts listed in /etc/fstab

why is it now doing this?

---

### Post by Dumdideldum on 2009-11-03
I second that - I have got exactly the same problem. Tried editing both menu.lst and fstab. UUID is correct, tried without UUID - same result, waiting for / forever - / is although mounted readonly, so I have to remount it using:
```

sudo mount -n -o remount /dev/sdc1 /

```

to be able to edit fstab.

Mounting using LABELS doesn´t work either. I updated my main system pretty flawlessy, my mythtv-box shows the results above. The update process didn´t work at all, because my computer crashed due to a bug in locales when using an AMD 64 processor - segfault (but that´s another topic). :confused:

Any help would be much appreciated - thx.

---

### Post by Dumdideldum on 2009-11-03
Okay, I have solved my problem.
It seems like that 9.10 won´t boot from an fstab, where 9.04 did boot flawlessly.

First you have to remount the / via
```

mount -n -o remount /dev/sdx /

```

to have write access to /etc/fstab.

Secondly, you have to edit your /etc/fstab after you have backed it up:
```

proc            /proc           proc    defaults        0       0
/dev/sdc1       /               ext3    defaults        0       1

UUID=13275c80-0102-46ed-a18b-317e0d71f435 /var            ext3    relatime        0       2
UUID=eba564ac-71ff-4158-a185-6eb0fd0445f9 none            swap    sw              0       0

```

This is my fstab for example, before, I had in front of the UUID also the drive name (like /dev/sdc3). By removing quiet splash from /boot/grub/menu.lst, I could see mountall nagging about syntax errors in the fstab.

Hope that helps a bit

---

### Post by jago25_98 on 2009-11-14
Even deleting /etc/fstab (by using esc) doesn't effect the waiting! 

I don't know where it's reading it's fstab from. 

*fdisk -l* tells me the partitions are not in order.

---

