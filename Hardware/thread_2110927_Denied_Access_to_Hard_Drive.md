---
title: "Denied Access to Hard Drive"
date: 2013-01-31
forum: Hardware
---

### Post by Rebecca_D on 2013-01-31
I have a 64 bit version of Ubuntu 12.10 (Quantal Quertzel) installed running on a ACER P6T SE motherboard. This is installed on the primary hard drive (dev/sda) and I have two other drives, one internal drive and one external drive. All are mounted.

Since installation I have only been able to access the secondary internal drive (dev/sdb5) for read only when logged in as administrator. I can copy to it from a /home folder but cannot save directly to it. I have tried to change the permissions through Properties/Permissions. This states that the Owner is 'root' but all the options are greyed out. Very frustrating.

Can anyone suggest a way of changing the properties so I can access it fully.

Many thanks

---

### Post by greatsirkain on 2013-01-31
I think to change the privileges it would be
sudo chmod -R 777 /media/name of drive you can't save to

but I'm unsure that's correct so wait for an experienced second opinion before entering any code. I thought if you could mount it then you had full access to it.

---

### Post by ajgreeny on 2013-01-31
It will depend upon the filesystem to which the partition/disk is formatted, and also how you are mounting the disk.

Is it mounted at boot automatically?

Let's see the output of ```
cat /etc/fstab
```

---

