---
title: "Increasing unallocated space using Gparted."
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by benon on 2009-06-16
Am using ubuntu 8.04 on a dell vostro a860 notebook. I had made a partition of just 10GB for windows-xp using Gparted. Now i need to increase the size of this partition to 20GB so i can replace xp with vista. I have failed to use the resizing option in Gparted to increase the size. It seems to just move the partition not resize it!
 
      I even deleted the partition hoping it would disappear completely so that i can make a new one but it remains as unallocated space. I just need to either resize to 20 GB it or remove it completely so that i can make a new partition. 

    seems simple but i just can't get around it!

---

### Post by benon on 2009-06-17
I managed to get the solution as i kept looking around. When u use the live CD the drives are not mounted so u get the resize option.
 Guess the thread is closed!

---

### Post by raymondh on 2009-06-17
> **benon said:**
> I managed to get the solution as i kept looking around. When u use the live CD the drives are not mounted so u get the resize option.
 Guess the thread is closed!

Congratulations.

Links that may serve you in the future.

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Once again, congratulations.

---

### Post by Idefix82 on 2009-06-17
Before you proceed, be warned that you will have to repair the boot sector as Windows will kick out grub from the MBR upon installation and you won't have the option of booting into Ubuntu until you reinstall grub.

---

### Post by benon on 2009-06-22
Thanks everyone for the advice. Am now happily duabooting ubuntu and vista! My main challenge now is resizing the vista partition as safely as possible without losing data. I had given it little space.

---

### Post by Mark Phelps on 2009-06-23
> **benon said:**
> Thanks everyone for the advice. Am now happily duabooting ubuntu and vista! My main challenge now is resizing the vista partition as safely as possible without losing data. I had given it little space.

"Without losing data" is the key phase here ...

So, be sure to use the Vista Disk Management tool to shrink the Vista OS, not the Ubuntu partition editor or a GParted Live CD.  Using either of the latter runs the risk of corrupting the Vista OS partition.  If you have a Vista DVD, you can reboot using it and run Startup Repair repeatedly until it finds no more problems -- and that MIGHT repair the partition.  But, it also might not.

---

### Post by raymondh on 2009-06-23
another tip ....

Before shrinking, try to defrag 1 or 2x which (HOPEFULLY) will push all data to the front of the partition.

Mark is right .... use Vista' disk management tool to shrink the Vista partition.

Good luck.

---

### Post by benon on 2009-06-23
Thanx. However i need to expand not shrink the vista partition. I want to get some space from the ubuntu partition and give it to the vista partition. Does the advice still hold?

---

### Post by raymondh on 2009-06-23
> **benon said:**
> Thanx. However i need to expand not shrink the vista partition. I want to get some space from the ubuntu partition and give it to the vista partition. Does the advice still hold?

Sorry, my mistake.  Thought you were shrinking Vista.

---

### Post by benon on 2009-06-24
Well, it's probably my mistake too. Didn't specify. U see i installed ubuntu 1st then created some little space for vista to try it out. This is why i now need to give vista a bit more space .

This is totally different but my computer's fanning system is a little louder than usual, like the fan is hitting on something! Any ideas.

---

### Post by raymondh on 2009-06-24
> **benon said:**
> Well, it's probably my mistake too. Didn't specify. U see i installed ubuntu 1st then created some little space for vista to try it out. This is why i now need to give vista a bit more space .

This is totally different but my computer's fanning system is a little louder than usual, like the fan is hitting on something! Any ideas.

Couple of ideas ...

Fan may be out-of-mount. 
You may need to do some cleaning.
Fan may be going kaput.

Also, it may be getting HOT inside hence requiring the fan to do some extra work.

Is it the same noise when you run Vista?

Some threads for reading.

[http://ubuntuforums.org/showthread.php?t=477258](http://ubuntuforums.org/showthread.php?t=477258)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_control_fan_speed_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_control_fan_speed_.28lm-sensors.29)

They may be for feisty but they may give you clues.

If you post a new thread with a specific title, someone in the know may get to see it and give you proper directions.

Good luck.

---

### Post by benon on 2009-06-30
Thanx. The sound is in both operating systems. I'll check out the links. But what about increasing the vista partition.

---

### Post by raymondh on 2009-06-30
> **benon said:**
> Thanx. The sound is in both operating systems. I'll check out the links. But what about increasing the vista partition.

Kindly share a  screenshot of gparted as well as outputs of these terminal commands

```
sudo fdisk -l
df -h
```


on the fdisk ... that's a small L and not number 1

Thanks.

---

### Post by benon on 2009-07-08
[[img]http://img181.imageshack.us/img181/2312/screenshotdevsdagparted.png[/img]]("http://[url=http://www.imagehosting.com/)"]http://[[img]http://img181.imageshack.us/img181/2312/screenshotdevsdagparted.png[/img]](http://www.imagehosting.com/)[/URL]


benon@benon-laptop:~$ sudo fdisk -l
[sudo] password for benon: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3853    30947328    7  HPFS/NTFS
/dev/sda2            3854       18704   119290657+  83  Linux
/dev/sda3           18705       19457     6048472+   5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris


benon@benon-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             113G   88G   22G  80% /
varrun               1009M  228K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   44K 1009M   1% /dev
devshm               1009M   12K 1009M   1% /dev/shm
lrm                  1009M   39M  971M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      113G   88G   22G  80% /home/benon/.gvfs

Hope that helps. Sorry i took a little long to reply.

---

### Post by benon on 2009-07-13
Hey! Am still waiting for some advice. Anyone please.

---

### Post by anchorschmidt on 2009-07-13
Download EASUS partition manager for Windows vista from 

[http://download.cnet.com/Easeus-Partition-Manager-Home-Edition/3000-2248_4-10863346.html](http://download.cnet.com/Easeus-Partition-Manager-Home-Edition/3000-2248_4-10863346.html)

Its completely free and you can increase your Vista partition. Please defrag first though. Reply if you have problems using it.

---

### Post by raymondh on 2009-07-13
> **benon said:**
> Hey! Am still waiting for some advice. Anyone please.

Hello Benon,

*Disclaimer* :  I usually prefer not to resize partitions by grabbing the left side and moving it because it *may* subsequently move root (/) or boot files and create havoc.  The operative word is **may**.  So back up your files pls.

Use the liveCD and access gparted.  Better option is to burn yourself a standalone gparted CD, latest version, as it seems to be better.  

Right click on all partitions and if youre given the option to unmount, go ahead and unmount.  Same for swap ... swapoff.  Then try

1. With everything unmounted, move/resize down sda2 to give desired space.
2. Extend sda1.
3. Review and apply

Once done, check booting into sda2 (Ubuntu).  I can't seem to post links now.  If you visit [gparted.sourceforge.net]("http://gparted.sourceforge.net/"), you'll find the gparted manual for reference.  Another link for reference is [howtoforge.com/partitioning_with_gparted]("http://howtoforge.com/partitioning_with_gparted").

Good luck.

---

### Post by benon on 2009-07-15
Thanks guys. I'll keep in touch.

---

