---
title: "[SOLVED] drives not mounting"
date: 2008-10-05
forum: General Help
---

### Post by suhaib1thariq on 2008-10-05
i had now installed hardy.......by partitioning my last drive....
when i entered in to hardy all other hard drives are shown unmounted ...i mounted all the drives ...it opens....after i restarted the system the drives are again unmounted.....
how can i mount it permanently.......

---

### Post by Elfy on 2008-10-05
You need to add the drives to fstab - are they linux or windows partitions?

IF they are ntfs - install ntfs-config
```
sudo apt-get install ntfs-config
```

There will be a tool in System Tools - it will allow you to mount your drives permanently. 

IF they are linux post the outputs from these commands if you need help, look at the threads below

```
sudo fdisk -l
sudo blkid
```

[http://ubuntuforums.org/showpost.php?p=5720510&postcount=5](http://ubuntuforums.org/showpost.php?p=5720510&postcount=5)

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by janu005 on 2009-11-23
I have a Western Digital My Book Studio Edition 750GB external hard drive that I am using on Windows XP and it has a similar problem. When I start up, the drive's partitions show up just fine. However, if I leave the computer long enough for it to go to sleep, I often come back to find that either the WD's partitions have all disappeared, or that the partitions still appear in My Computer, but they do not show any files within them.

I bought this thing to store my iTunes music library on, but whenever the WD drive fails to mount, my iTunes Library file becomes corrupted. I can't count on this thing at all as a usable storage device, because I can never be sure when it is going to be freaking out on me.
==================
[Obesity in Teenagers](http://www.ebariatricsurgery.com/obesitysurgeryforteenagers.php)
[Jetta Turbocharger](http://www.turbochargerpros.com/jetta_turbocharger.html)

---

### Post by emigrant on 2009-11-23
> **janu005 said:**
> I have a Western Digital My Book Studio Edition 750GB external hard drive that I am using on Windows XP and it has a similar problem. When I start up, the drive's partitions show up just fine. However, if I leave the computer long enough for it to go to sleep, I often come back to find that either the WD's partitions have all disappeared, or that the partitions still appear in My Computer, but they do not show any files within them.

I bought this thing to store my iTunes music library on, but whenever the WD drive fails to mount, my iTunes Library file becomes corrupted. I can't count on this thing at all as a usable storage device, because I can never be sure when it is going to be freaking out on me.
==================
[Obesity in Teenagers]("http://www.ebariatricsurgery.com/obesitysurgeryforteenagers.php")
[Jetta Turbocharger]("http://www.turbochargerpros.com/jetta_turbocharger.html")

out put for?:

```
sudo fdisk -l
```

```
gedit /etc/fstab
```

---

