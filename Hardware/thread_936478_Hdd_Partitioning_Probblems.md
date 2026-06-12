---
title: "Hdd Partitioning Probblems"
date: 2008-10-02
forum: Hardware
---

### Post by hackerlife on 2008-10-02
Ok so I am trying to make my partition on my HP dv2000 larger by 30 gigs.
Because I have problems with Ubuntu and the Vista partition working together, I decided to shring the Vista partition inside Vista. 
I then booted from my Cd to run gParted.
Here's where the trouble starts.
The first problem was I had to move the unallocated 30 gigs over because it was on the wrong "side" of my / and /home folder.
So I had to enlarge my / by 30 gigs, then shrink it on the right, so i could enlarge my /home by 30 gigs. 
Before I go any farther, heres how my partitions are set up.
sda1 is the vista partion
sda2 is /
sda3 is an extended partition, with
sda4 (/home) and
sda5 (linux-swap) 
inside. I had to do this because sda6 is HP RECOVERY, and apparently i cant have four main partitions.

So while I was doing all this shifting around, an error occurred. It was too long ago for me to remember what the error was, but it ended up telling me that I had 34.9 gigs in my /.  
Lies.
When I go into computer or filesystem and right-click>properties, it says i have less than 3 gigs.
I didnt worry about it until now because nothing was wrong, gparted was just confused. 
Well, now I actually need those 30 gigs, and when I boot the ISO and run gparted, it wont let me shrink the 34 gig /dev/sda2, because it says i'm using almost 30 gigs (which I can assure you i'm not, but don't worry, i'm going to post screen shots later!!)
So pretty much my friend and I (who is pretty genius so I'm getting worried now that he can't figure it out!!) are getting mixed results around the system about how big everything is.
If I missed anything i'm sure he'll post it rofl!
my df -h output:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             8.0G  4.6G  3.0G  61% /
varrun                471M  116K  471M   1% /var/run
varlock               471M     0  471M   0% /var/lock
udev                  471M   56K  471M   1% /dev
devshm                471M     0  471M   0% /dev/shm
lrm                   471M   44M  427M  10% /lib/modules/2.6.24-19-generic/volatile
/dev/sda5             6.0G  5.2G  458M  93% /home
gvfs-fuse-daemon      8.0G  4.6G  3.0G  61% /home/william/.gvfs

```
sudo fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78e683e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13160   105701641+   7  HPFS/NTFS
/dev/sda2           18643       19457     6546487+   7  HPFS/NTFS
/dev/sda3           13161       17728    36692460   83  Linux
/dev/sda4           17729       18642     7333673    5  Extended
/dev/sda5           17730       18511     6281415   83  Linux
/dev/sda6           18512       18642     1052226   82  Linux swap / Solaris

Partition table entries are not in disk order

```
and finally some screen shots
the first is my my gparted screenshot (while running, so everything is mounted of course!),
i will next post my right click properties in filesystem.
Please help!! I'm getting really desperate!!!
Thanks in advance for all the help!!

---

### Post by hackerlife on 2008-10-02
Heres the correct screenie!

---

### Post by hackerlife on 2008-10-03
nobody??!!!
Please guys, I would really appreciate some help here!

---

### Post by hackerlife on 2008-10-03
Need help getting very desperate going to reformat soon...

---

### Post by hackerlife on 2008-10-11
c'mon guys...
didnt you notice all the exclamation points i used...
the nice type...
the few spelling errors...
the correct punctuation?
PLease?

---

### Post by jonelnz on 2008-10-11
Greetings Hackerlife...

I had Vista Ultimate pre-installed on my system but have since removed it.
Here is an extract from Hp's "Troubleshooting and Maintenance Guide" (page 24) which came with my system.

QUOTE:
"Complete the procedure in this section to create a set of recovery discs from the recovery image stored on your hard disk drive.
This image contains the operating system and software program files that were originally installed on your computer at the factory.
You can create only one set of recovery discs for your computer. Furthermore, the recovery discs you create can be used only with your computer.
*After creating the recovery discs, you can delete the recovery image if you want to make extra space available on your hard disk drive.*"

NOTE:
Do not delete the recovery image until you have made recovery discs.
END QUOTE:

Obviously in your stituation, removing the "Recovery Partition" will reduce the number of primary's you end up with plus release another 6GB.
For my situation I just created one / partition and a swap partition, that kept it nice and simple.

Hope this is of some help to you.

Regards
Jon

---

