---
title: "3 questions regarding grub, booting and swapfiles"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by HAARP on 2006-07-11
**1. grub**
Is grub able to see SATA disks on a SilRaid3112 Controller? **Any Raid-Features of that Controller are disabled.** When booted, they're there, but in grub? 

**2. Booting**
What is needed to boot until the **fstab**-filesystems are mounted?? I want to mount a raid0-array to **/**, but that's only possible after the array has been started. In order to do that, I need files from **/**. I want to create a fake-**/** which the system boots from until the raid-array is started, then remount the real **/** from the array


If everything works like supposed, it'll look like this:

**sda** (160GB)
[color=#FFFFFF]----[/color]**1** - **swap** (512MB-xMB)
[color=#FFFFFF]----[/color]**2** - **/** *real, part of raid0* (rest of disk)
[color=#FFFFFF]----[/color]**3** - **/** *boot* (xMB, depends on q.2)
**sdb** (160GB)
[color=#FFFFFF]----[/color]**1** - **swap** (512MB)
[color=#FFFFFF]----[/color]**2** - **/** *real, part of raid0* (rest of disk)

---

### Post by HAARP on 2006-07-12
Please, there has to be someone who can help me :???:

---

### Post by Teroedni on 2006-07-14
The reason you have not get answer is that it is extremely difficult to get such things working in linux.

I did a google linux  search on your problem and found that you controller is software raid. That means you need software to do Raid

Fortunally i found a link to a driver which is supposed to do that.
I hope that this helps, and i am sorry that i cant help you more on this matter as i have never done Raid myself.


Here is the link Good Luck;)

[Software raid for linux]("http://www.infowares.com/linux/")

---

### Post by HAARP on 2006-07-14
Ok, thanks for at least replying :)

Linux Software-RAID is way faster even than the Fake-Hardware-Raid the Controller does, so I'm using Linux-Raid (md0)

I already did extensive googling. I always do, because it's faster than waiting for answers. Booting from a Soft-Raid isn't easy, most of the things I'm able to find this way are for Kernels as old as 2.0, use Lilo or simply aren't what I'm looking for. But I'm sure there's someone, even in this forums, who has such a thing running and could help me.

I'm not even directly asking for help getting the array to work. I just need to know if the bootmanager can handle disks on the controller and what the kernel needs to boot until fstab is initialised. I mean, even if only one of the questions is answered, I would be damn happy! ;)

---

### Post by John.Michael.Kane on 2006-07-14
Here these may offer some help.

[**Using RAID in Linux/Setting It Up**]("http://www.linuxplanet.com/linuxplanet/tutorials/4349/6/")

[**linux_software_raid**]("http://www.howtoforge.com/linux_software_raid")

[**linux_poormans_raid**]("http://www.howtoforge.com/linux_poormans_raid")

[**Software-RAID-HOWTO**]("http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html")

[linux/raid-lvm]("http://home.gagme.com/greg/linux/raid-lvm.php")

---

### Post by HAARP on 2006-07-14
Thanks, but those tutorials are either for RAID1 (mirroring), or are not about booting from a RAID.

The problem is, I want to boot from a RAID0-array (striping). But he array doesn't work until the kernel modprobes the module and starts the array. Catch-22 :p 
What I'm trying to do is move everything needed to boot onto a small non-raid boot partition, and then mount the array on top of this partition after the kernel is ready.

But thanks to anyone who tries to help! I appreciate that.

---

### Post by Arnaud_B on 2006-07-14
Considering the size of your drives I would suggest you to do more partitions... some will say it's not necessary but I still find it cleaner (and *very* useful in case of recovery) and I would especially advise you to do a separate /var partition... /var can get huge sometimes (logs...) and having it separated is generally a good idea... about your questions you won't have any problems it will work fine as long as you don't try to put /boot on a raid array (you could have a raid 1 for /boot though but I don't see the point and it might be more tricky to set up...). I would suggest (total size): 
/boot --> 300M
/     --> 900M   <-- way too much but if you happen to save stuff in /root this might be necessary...
/usr  --> 10-15G <-- way too much but well you have plenty space, it's up to you... you could actually also have a separate /usr/local partition if you have a lot of "non-ubuntu" stuff
/var  --> 5-6G
swap  --> 2G
/tmp  --> 1G
/home --> the rest
Also... if you install stuff in /opt instead of /usr/local when it's not ubuntu maybe you could do a /opt partition instead of a /usr/local one...
It's just recommendation... I have a raid 0 array working pretty much like that...
Good luck!
A.

---

### Post by HAARP on 2006-07-14
I like having one big partition :D I've had different partitions before, and eventually, one becomes full.
So it works for you. How did you do it? Just put /boot onto a non-raid partition and make him remount after initialising? It's that easy?

No wait, now I get it. You mount the different /usr, /tmp, etc. after it's booted. Yeah, that would work. But I'm looking for a solution to put as much as possible on the array in one single partition. ;)

---

### Post by Arnaud_B on 2006-07-14
If you like having one big partition it's very ok and can be actually better... dividing like that may only have an advantage if you know how u use your space otherwise you can end up filling a partition indeed and that can become annoying ;-)
well not sure my current setup might help u though because I use an array of 4hds (each 80G, 10Krpm :-) )which is not your case... but common you have a *lot* of space and by setting up a raid 0 array you will have all 320G available! it's hard to fill no? ;-) don't make things complicated just setup a /boot of 300M let's say at the beginning of the first disk, trash the first 300M of the second disk, and then setup / and swap (if this is your choice) on both sides to use with raid, then launch mdadm and create your arrays, and finally choose the mount points (--> / swap) and voila :-)
Good luck!
A.
PS: As a side note: backing up *every* day is *not* optional when you have a raid 0 setup and care about your data ;-) it's not that it's that much more dangerous than a normal hd but if it goes wrong it might be *bad* ;-)

---

### Post by HAARP on 2006-07-15
Thanks!
I've got a 320GB backup disk. Gonna be a 3-disk RAID9.9 :mrgreen: Expect I will backup manually.
I've already got 260GB filled with stuff. You don't know how fast your disk becomes full when you save every one of your music CDs in lossless ;) 

One last question: When does your mdadm start? Even before init?
I'm using raidtools2, because mdadm seems to destroy my array again and again. I don't know how to get it to start at that time. I think it's supposed to be integrated into the kernel or something. How do I pump raidtools and the md_mod module into the kernel? mdadm seems to have done that automaticly.
...and there goes my obscure question :p

---

### Post by HAARP on 2006-07-15
I've got an idea:
I'm using my backup drive for a 1:1 copy of the array anyway. So why not boot from the backup drive and mount the array on top of it when it's ready? :D 
I think I'll settle with this method.
Thanks everyone!

---

