---
title: "How to unmount &quot;/home&quot; from external hard drive"
date: 2011-09-12
forum: Hardware
---

### Post by premchand21 on 2011-09-12
Hello gurus,
I installed a new external hard drive as I wanted to mount the new hard drive to "/var/www" folder. But unfortunately I mounted to "/home" by mistake while testing something. I am banging my head to unmount the new hard drive from "/home" but it is not allowing me to do so. I also tried logging in as root and tried to unmont but I had no success.
I really appreciate if somebody could help me unmount "/home" from my the newly installed hard drive.

FYI: The main hard drive is mounted to "/" folder and the newly installed hard disk is installed to "/home" directory.

Here is the output of "df" command
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             24027628  21780516   1026576  96% /
udev                   1676736       316   1676420   1% /dev
none                   1676736      1196   1675540   1% /dev/shm
none                   1676736       148   1676588   1% /var/run
none                   1676736         0   1676736   0% /var/lock
none                   1676736         0   1676736   0% /lib/init/rw
/dev/sdb2             96124936  36505628  54736352  41% /home
/dev/sda1            480618344  14591324 441612960   4% /mnt/data1
/dev/sda2            961529388  16216192 896470332   2% /mnt/data2
```

Thanks in advance!!!

---

### Post by papibe on 2011-09-12
If you put a rule on the /etc/fstab, you need to boot into safe mode and change it in text text mode. Alternatively, you can boot into the Ubuntu Live CD (installation CD but choose 'Try Ubuntu').

If you don't, just restart your machine and the previous rules (/home where it used to be) will be applied.

Hope it helps,
Regards.

---

