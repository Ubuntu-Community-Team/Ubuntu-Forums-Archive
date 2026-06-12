---
title: "Partition Help Needed"
date: 2008-11-11
forum: General Help
---

### Post by k3y5rmy1if3 on 2008-11-11
Hi, I've been trying to install ubuntu on my desktop computer and have been having some trouble partitioning the hard drive. I took the advice of others, and attempted to resize my Vista partition first in the partition editor (I wish to dual boot), but when I attempt to resize, I get the message 

See the details for more information.

IMPORTANT
If you want support, you need to provide the saved details!
See [http://gparted.sourceforge.net/larry/tips/save_details.htm](http://gparted.sourceforge.net/larry/tips/save_details.htm) for more information

And when trying to use the link to save the information...the input ```
root@GParted:~# fdisk -l | grep sd
```

is not recogized...I believe I am lost...and help would be appreciated

---

### Post by k3y5rmy1if3 on 2008-11-11
Oh, and the gParted window is still open

---

### Post by DGortze380 on 2008-11-11
looks like you're using a gparted live cd??

just put your ubuntu live cd in, and follow the install prompts. 
You will have the option to partition your drive during the install.

resize whatever partitions you want. create at least 1 primary ext3 for / and 1 swap (approx 1.5x the amount of RAM you have).

back up an import files before attempting this.

---

### Post by k3y5rmy1if3 on 2008-11-13
Well...I took your advice...and was messing around on the partitioning page. The thing is...I never pressed the forward button, and..well, windows won't start now, and it seems as if my whole hard drive has been reformatted. Is there any way I can access windows again? This is really...not good.

---

### Post by k3y5rmy1if3 on 2008-11-13
When I attempt to start windows...all I see is a flashing cursor.

---

### Post by k3y5rmy1if3 on 2008-11-13
If you guys could help me recover my system...that would be really great (if possible). Right now when I try to boot, it shows the flashing cursor...then "disk boot failure, insert system disk and press enter". At the moment I dont have the system disk...so I was wondering if I could fix it from the ubuntu live cd...

---

### Post by DGortze380 on 2008-11-13
> **k3y5rmy1if3 said:**
> If you guys could help me recover my system...that would be really great (if possible). Right now when I try to boot, it shows the flashing cursor...then "disk boot failure, insert system disk and press enter". At the moment I dont have the system disk...so I was wondering if I could fix it from the ubuntu live cd...

What is your boot order in the BIOS?

Did you back up your files before attempting partitioning like I suggested?

Can you boot the live cd, run gparted, and post a screenshot? Or the output of df -l

---

### Post by k3y5rmy1if3 on 2008-11-13
My boot order in bios was fine...i just checked that.

I'm downloading the windows recovery disk right now...and no, i stupidly didn't back it up. I didnt think it would save the changes, because I didnt go to the next step... Here is the output you asked for:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                  1619220      2000   1617220   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                  1619220      2000   1617220   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                  1619220         0   1619220   0% /lib/init/rw
varrun                 1619220       100   1619120   1% /var/run
varlock                1619220         0   1619220   0% /var/lock
udev                   1619220      2808   1616412   1% /dev
tmpfs                  1619220       144   1619076   1% /dev/shm
rootfs                 1619220     20624   1598596   2% /
/dev/scd0               715592    715592         0 100% /cdrom
/dev/loop0              691712    691712         0 100% /rofs
tmpfs                  1619220        12   1619208   1% /tmp

```

---

### Post by k3y5rmy1if3 on 2008-11-13
Yeah...i'm wondering whether I should reinstall windows or not...because the recovery disk is working

---

### Post by k3y5rmy1if3 on 2008-11-13
Is it possible that I could go into the /dev/sda1 drive through the live cd and at least recover some of my files?

---

### Post by DGortze380 on 2008-11-13
> **k3y5rmy1if3 said:**
> Is it possible that I could go into the /dev/sda1 drive through the live cd and at least recover some of my files?

Take a deep breathe. We don't all sit on the forums all day.

We haven't even figured out whether or not you've deleted anything.

Can you please post a screenshot of gParted from the live cd.

---

### Post by k3y5rmy1if3 on 2008-11-14
Alright...the screenshot is attached. Thanks for all your help so far...

---

### Post by DGortze380 on 2008-11-14
> **k3y5rmy1if3 said:**
> Alright...the screenshot is attached. Thanks for all your help so far...

Time to look into data recovery. Good Luck. Chances are slim.

[http://googlesystem.blogspot.com/2006/03/testdisk-recover-lost-partitions.html](http://googlesystem.blogspot.com/2006/03/testdisk-recover-lost-partitions.html)

It's always a good idea to do backups before partitioning.

---

### Post by k3y5rmy1if3 on 2008-11-14
Well...I dont have many important files...so I guess I'll reinstall windows. Though would it be possible if you could help me install Ubuntu again? I wouldn't want to mess up a second time...

---

### Post by DGortze380 on 2008-11-14
> **k3y5rmy1if3 said:**
> Well...I dont have many important files...so I guess I'll reinstall windows. Though would it be possible if you could help me install Ubuntu again? I wouldn't want to mess up a second time...

Ok. Step-By-Step.


1)  Boot Ubuntu Live CD
2)  Run GParted
3)  Delete All Existing Partitions 
4)  Make One Partition Of Whole Drive
5)  Format It FAT32
6)  Shrink The Only Partition Leave Space For:
       a- Root Ubuntu Partition (ext3)
       b- SWAP Partition (2x RAM) (SWAP)
       c- Separate home partition if desired. (ext3)
7)  Use new free space to create the above partitions
8 ) Apply changes

9)  Boot Windows Install CD
10) Reformat FAT32 partition to NTFS
11) Install Windows to NTFS Partition.

12) Boot Ubuntu Live CD
13) Choose manual partitioning
14) Don't change any of the partitions you've alreayd made
15) Install / to /, SWAP to SWAP, (optional) /home to /home
16) Finish Install

---

### Post by k3y5rmy1if3 on 2008-11-14
Gparted will only let me delete the /dev/sda1 partition...I can't delete any of the other ones

---

### Post by DGortze380 on 2008-11-14
> **k3y5rmy1if3 said:**
> Gparted will only let me delete the /dev/sda1 partition...I can't delete any of the other ones

That's ok. You can just grow the SWAP partition that's already there to whatever size you need. partition the rest.

---

### Post by blake82 on 2008-11-14
I just fixed a similar problem on my work laptop where a partition magic error deleted my ubuntu partition..... and I didn't have a backup (doh!)

It sounds like you're having a similar problem, as long as you haven't written anything to the disk since this hapened, your data is probably still there.

Here's what you want to do:

1. Boot up into your ubuntu live cd
2. Go to System -> Administration -> Software Sources
3. Check the 1st 4 boxes under (Downloadable from the Internet)
4. Hit close, software sources will ask you if you want to reload the sources. Say yes.
5. Open up a terminal and enter:
```
sudo apt-get install gpart
```
6. After it's done installing, enter
```
sudo gpart -W /dev/sda /dev/sda
```
The system will hang for a while while it reads the disk. Eventually it should come back with a bunch of "guesses" of what partitions are on your disk. If you haven't done anything drastic to your disk, you should hopefully see your missing partitions on there.
7. First it will ask if you want to edit the partitions. Say NO
8. Next it will ask if you want to activate partitions. Say YES
9. Type in the partition number you want to activate, gpart will work for a second and then tell you to restart.
10. repeat for each missing partition

**NOTE**
First, I seriously recommend doing a bit by bit backup of this disk before screwing around with the partition tables. You can use the dd command to do this, but you'll need an empty hard drive. You can google info about this, I don't remember exactly how I did it, it takes a LONG time though (hours and hours)... but if you screw anything up, you can always revert back to your backup

Second, this did the trick for me, and it sounds like you have the same problem, and it should work, but I'm not guaranteeing it will.

Good luck!

---

### Post by k3y5rmy1if3 on 2008-11-15
Alright...it said that the partition has activated...yet when I start up I still get the blinking cursor. But Im pretty sure the activation did something...as the partition table is completely different now...

---

### Post by k3y5rmy1if3 on 2008-11-15
There are now 2 partitions... /dev/sda1, and unallocated, which has 11gb in it...

---

### Post by k3y5rmy1if3 on 2008-11-15
Is there any way I could browse unallocated to see if perhaps that contains my files?

---

### Post by blake82 on 2008-11-15
does gpart see more than one partition? I don't know too much about the boot process and grub, but if your system needs stuff on the (still deleted) partition, it won't boot.

You need to repeat the gpart process for each partition you want to activate, so activate #1, reboot, repeat the process for #2 and so on

As for browsing files on your unallocated space, I don't know how to do that. I know there are some forensic hard drive tools available, as well as some other tools that will look for files on unallocated space and pull them out, but UI don't know anything about them.

---

### Post by DGortze380 on 2008-11-16
> **k3y5rmy1if3 said:**
> Is there any way I could browse unallocated to see if perhaps that contains my files?

Nope. That's why I suggested data recovery first. Now that the partition has been mounted, chances went from slim to next to none. Unallocated has no file system to browse any more. It's either all 0's or raw data.

---

