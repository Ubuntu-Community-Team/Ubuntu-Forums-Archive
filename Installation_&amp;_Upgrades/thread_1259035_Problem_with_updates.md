---
title: "Problem with updates"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by Arconius on 2009-09-05
Hello all again

Hope this is the right place to ask. Just install ubuntu. Its giving the updates I need to install. I tried to install them and its errors out saying it needs 400M and I only have 357M. Sounds like its still looking for my flash drive. I used a flash drive to install.

---

### Post by theozzlives on 2009-09-05
How big did you make your root (/) partition?

---

### Post by Arconius on 2009-09-05
No idea. Any fix for this? Or reinstall

---

### Post by Partyboi2 on 2009-09-05
Can you open  a terminal (Applications>Accessories>Terminal) and post the output to
```
df -h
```

---

### Post by Headbanger2510 on 2009-09-05
Can you post how your partition sizes are like, so we can help you?

---

### Post by Arconius on 2009-09-05
arconius@arconius-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             2.3G  2.2G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  108K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  160K  1.5G   1% /dev
tmpfs                 1.5G  120K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sr0              7.7G  7.7G     0 100% /media/cdrom1
/dev/sda5              73G  280M   72G   1% /media/New Volume

---

### Post by Headbanger2510 on 2009-09-05
Sounds to me like /dev/sda5 is getting the space destinated to /dev/sda2.
So what you need to do is to boot with your liveUSB or liveCD and execute gparted, then you should resize /dev/sda5 to something smaller so /dev/sda2 can get enough space.

---

### Post by Partyboi2 on 2009-09-05
> **Arconius said:**
> arconius@arconius-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             2.3G  2.2G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  108K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  160K  1.5G   1% /dev
tmpfs                 1.5G  120K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sr0              7.7G  7.7G     0 100% /media/cdrom1
/dev/sda5              73G  280M   72G   1% /media/New Volume
Your sda2 partitions which is the root partition is only 2.3 gig, so you will need to increase the size of it.
Can you also post the output to
```
sudo fdisk -lu
```

---

### Post by Arconius on 2009-09-05
How do I change /dev/sda2 size? I made  /dev/sda5 smaller. Looks like I need to resize /dev/sda1 its next to /dev/sda2 and it has a key to it.

---

### Post by Headbanger2510 on 2009-09-05
Just select /dev/sda2 and click resize/move.

---

### Post by Arconius on 2009-09-05
Thank you Headbanger2510! One of the partition was mounted, blocked from resize\move command. Once it was off all was good.

---

