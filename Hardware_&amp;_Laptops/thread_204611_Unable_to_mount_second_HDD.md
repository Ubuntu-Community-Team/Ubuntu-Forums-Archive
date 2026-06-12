---
title: "Unable to mount second HDD"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by OldZack on 2006-06-27
Hi!
I've just installed Ubuntu 6.06 and all went extremely well. The M/c is dual boot with SimplyMepis as the second system. I have a second hard drive, formatted to Fat32 which is not being recognised. It's just a backup drive for data. With all other systems I've used all I had to do was create a folder as root in /mnt eg: mkdir /mnt/maxtor and then edit /etc/fstab, adding a line: /dev/hdb1  /mnt/maxtor/   vfat   defaults  0 0 then use the command 'mount /mnt/maxtor' and that was it. Job done! But not with Ubuntu? Any ideas very welcome.

---

### Post by taurus on 2006-06-27
See if this command works first from a terminal!
```

sudo mount -t vfat /dev/hdb1 /mnt/maxtor

```

---

### Post by OldZack on 2006-06-27
Tried that but no joy!

This is what I got:

garth@garth-desktop:~$ sudo mount -t vfat /dev/hdb1 /mnt/maxtor
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Does that help?

Zack :-k

---

### Post by OldZack on 2006-06-27
Oh dear! Problem solved! Guess who forgot he'd reformatted hdb1 as ext3 and was still trying to mount it as vfat! My only defence is I'm nearer 80 than 70... bring on the Zimmer frame.

regards to all,

Zack.

---

