---
title: "Woe is me! The tale of the two hard drives."
date: 2008-07-14
forum: General Help
---

### Post by Bside Starchild on 2008-07-14
Well my computer of 6 years or so has finally died, it has reached the point where I no longer feel upgrading and repairing is a wise use of my money. I am fairly certain the only problem is the psu is dead but I would like to avoid spending any more money on this machine. Now I am faced with the challenge of retrieving data off of the computers drive. This seemingly trivial task is turning into quite an event. The 120 gig western digital drive from my machine has an oem copy of windows on it which, I learned rather quickly, prevents me from simply placing it into another computer and booting up. I have an even older computer (with a non compatible psu, but good idea) which I have attempted to place this drive in as a slave with the older machines 40 gig seagate as master but I am still getting non system disk errors. I have been loading into ubuntu and knoppix via live cd hoping to gain access to the drive but I must admit I am not particularly well versed in linux and could not find any drives to mount. When I remove the 120 gig drive and leave only the original 40 gig drive ubuntu and knoppix both mount the drive fine and I am able to browse the contents but as soon as the 120 gig drive is added I am unable to mount any drive. I have tried putting the hdds in cable select and setting them to master and slave respectively to no avail.

If anyone could shed some light on this situation I would be forever grateful.

---

### Post by iaculallad on 2008-07-14
Ok, boot from you're LiveCD with the 120GB drive attached. When you reached the GNOME desktop, drop to your terminal and issue the command below and post whatever it displays:

```
cat /etc/fstab
sudo fdisk -l

```

If you're booting off Ubuntu Desktop 8.04 LiveCD, that drive will automatically be mounted.

---

### Post by Bside Starchild on 2008-07-14
Thanks for the reply!

cat /etc/fstab yeilds

ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

and sudo fdisk -l brings up another blank command prompt.

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ 


Under places no drives show where the 40 gig partitions showed when that drive was attached.

---

