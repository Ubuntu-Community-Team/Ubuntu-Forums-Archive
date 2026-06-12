---
title: "/boot is full"
date: 2008-07-18
forum: General Help
---

### Post by Helios1276 on 2008-07-18
After a fresh install(Heron) and downloading all updates (dumb in retrospect), I'm getting "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." whenever I try Synaptic or Enabling restricted ATI drivers.

helios@helios-laptop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: subprocess post-installation script returned error exit status 1
helios@helios-laptop:~$

(so it appears /boot is near full and causing me trouble)

helios@helios-laptop:~$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda8 30G 2.9G 25G 11% /
varrun 759M 104K 759M 1% /var/run
varlock 759M 0 759M 0% /var/lock
udev 759M 68K 759M 1% /dev
devshm 759M 12K 759M 1% /dev/shm
lrm 759M 39M 720M 6% /lib/modules/2.6.24-19-generic/volatile
/dev/sda7 46M 41M 2.9M 94% /boot
gvfs-fuse-daemon 30G 2.9G 25G 11% /home/helios/.gvfs
/dev/scd1 3.8M 3.8M 0 100% /media/cdrom1
/dev/sdb1 958M 791M 168M 83% /media/CleverStuff
helios@helios-laptop:~$ 

I've not come across this problem before so I'm looking for a fix. Cleaning up /boot or resizing partitions to give it more space?

---

### Post by damis648 on 2008-07-18
Well, as long as /boot is a separate partition, go ahead and resize it. Make another partition smaller and that one bigger.

---

### Post by Helios1276 on 2008-07-18
> **damis648 said:**
> Well, as long as /boot is a separate partition, go ahead and resize it. Make another partition smaller and that one bigger.

Gave that a shot , I fired up Parted Magic and had a go at downsizing the Hardy / partition which freed up space. However (being new to this side of things possibly) I was unable to add that freed space to the /boot partition. There is the option to 'copy' , would copying the /boot partition to the newly freed space (i.e. making a newer bigger /boot partition) work or cause more trouble?

---

### Post by Dutch70 on 2008-07-18
run this to get into synaptic...

```
sudo dpkg --configure -a
```

edit....run that in terminal, and then you should be able to get into synaptic

Dutch

---

### Post by Helios1276 on 2008-07-18
> **Dutch70 said:**
> run this to get into synaptic...

```
sudo dpkg --configure -a
```

I've tried that , see my first post.

---

### Post by kevdog on 2008-07-18
Maybe somebody can clarify this for me, but I thought you couldnt grow and shrink partition sizes except for the last partition.  For example, say your partitions are set in order on the HD /boot, <everything else>, /swp.  You could delete /swp, add or subtract from the /swp space to give for example <everything else> more space, and then recreate the /swp partition.  To increase the /boot partition, you would have to delete both the /swp and <everything else> partitions -- however if deleting the <everything else> partion -- what's the point??  Just reinstall.

That's what I have found -- anybody else with any other info?

---

### Post by plucky on 2008-07-19
> That's what I have found -- anybody else with any other info? 

You can resize the rear of a partition not the front of a partition.

You can move the front of a partition,but if the partition has a lot of data **this can take a long time.**

To grow a partition,there has to be unallocated space adjacent to the rear of the partition,so the partition can grow into it.

You can shrink a partition as long as the partition is not full.

Resizing partitions is best done from a Live CD as partition cannot be changed when mounted.

Changing partition sizes also changes the UUID of the partition,which can cause problems booting or mounting because the fstab  and menu.lst file needs to be changed.

As always,you should backup your data before changing partitions,so that if anything goes wrong during the partitioning,you will not lose your data.


Good Luck

:)

---

### Post by plucky on 2008-07-19
> I've not come across this problem before so I'm looking for a fix. Cleaning up /boot or resizing partitions to give it more space?

Your /boot partition seems a bit small,I would probably double its size.
In the mean time.

Open a terminal and [code]cd /boot
ls -l[code]
This will show you how many kernels you have installed.You could delete some of the **.bak** files of the older images as they are only backup files.

You should see a number of kernel images,so you can remove some of the older ones.It is best to do so from Synaptic.

Open Synaptic and search for "linux-image" and mark the older kernels for complete removal.It is a good idea to keep at least one older kernel just in case your present kernel breaks,and you have something else to boot into.This will free up space in the /boot partition and also clean up your menu.lst file.


Good Luck

---

### Post by HunkirDowne on 2008-07-19
*I think I'm at least half-way there.  I'm running through a long list of updates as I've had this problem for a couple months and haven't had the time until recently to tackle this problem.*

I was having the same problem... the eternal 'sudo dpkg --configure -a' loop.  Deleting the earliest two of three *.bak files freed up enough space but before I could get Synaptic Package Manager (SPM) to work, I had to run 'sudo dpkg --configure -a' one last time to get going again.  Once that was done, I used SPM to remove the earliest kernel sets to regain even more space on '/boot'.

Steps:
_From the terminal window_:
'**cd /boot**'
'**ls -l *.bak**' *(note chronology, delete all but last one)*
'**sudo rm initrd.img-2.6.24-16-generic.bak**'
'**sudo rm initrd.img-2.6.24-17-generic.bak**'
'**sudo dpkg --configure -a**'

_From the Desktop Panel_:
System / Administration / Synaptic Package Manager: remove oldest kernel then close SPM (details available upon request).

Start the (long?) task of installing updates.
(98 and counting for me.)

---

### Post by der_joachim on 2008-07-19
@OP:
Did you by any chance compile your own kernel? I used to have an issue simiar to yours, although my /boot partition was 250 Megs (which should be more than enough). Turns out that I had to disable some debug flag in the kernel configuration. After doing that, my initrds got a lot smaller, thus solving all the space issues I had.

---

### Post by Helios1276 on 2008-07-19
Thanks for the replies lads, ya I shrunk the / Ubuntu Partition a little and brought the boot partition up to 250mb last night. It was as mentioned, I had to allocate the free space to precede the the partition I was shrinking and thus allow the boot partition to 'grow' into it. First time using Parted Magic, it's fantastic! So, Ive got the extra space but I'm still getting the original error request me to run 'dpkg --configure -a' , which I do ( and it now works). However, I'm unsure what my next steps are to fix the problem.

---

### Post by Helios1276 on 2008-07-19
> **plucky said:**
> Your /boot partition seems a bit small,I would probably double its size.
In the mean time.

Open a terminal and [code]cd /boot
ls -l[code]
This will show you how many kernels you have installed.You could delete some of the **.bak** files of the older images as they are only backup files.

You should see a number of kernel images,so you can remove some of the older ones.It is best to do so from Synaptic.

Open Synaptic and search for "linux-image" and mark the older kernels for complete removal.It is a good idea to keep at least one older kernel just in case your present kernel breaks,and you have something else to boot into.This will free up space in the /boot partition and also clean up your menu.lst file.


Good Luck

helios@helios-laptop:~$ cd /boot
helios@helios-laptop:/boot$ ls -l
total 36227
-rw-r--r-- 1 root root  422607 2008-04-10 17:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root  422667 2008-07-12 06:30 abi-2.6.24-19-generic
-rw-r--r-- 1 root root   79964 2008-04-10 17:51 config-2.6.24-16-generic
-rw-r--r-- 1 root root   80049 2008-07-12 06:30 config-2.6.24-19-generic
drwxr-xr-x 2 root  999    1024 2008-07-18 18:13 grub
-rw-r--r-- 1 root  999 7868878 2008-07-18 19:20 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root root 7349268 2008-04-22 19:00 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root 7479560 2008-07-18 18:13 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7479098 2008-07-18 18:13 initrd.img-2.6.24-19-generic.bak
drwx------ 2 root root   12288 2008-07-18 18:00 lost+found
-rw-r--r-- 1 root root  103204 2007-09-28 11:06 memtest86+.bin
-rw-r--r-- 1 root root  899892 2008-04-10 17:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root  905170 2008-07-12 06:30 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root 1904248 2008-04-10 17:51 vmlinuz-2.6.24-16-generic
-rw-r--r-- 1 root root 1921432 2008-07-12 06:30 vmlinuz-2.6.24-19-generic
helios@helios-laptop:/boot$ 

This is where I'm at currently, also I'm unable to open Synaptic at the moment without receiving the original error.

---

### Post by plucky on 2008-07-19
You have now increased you space in the /boot partition so you need to fix the problem it caused.

Try ```
sudo apt-get install -f
``` to see if it will repair the failed install.

If that doesn't work then try ```
sudo update-initramfs -k all
``` to actually generate the failing file.

Good Luck

---

### Post by louieb on 2008-07-19
Just wondering why the separate partition for  /boot?
The only time I know you need one is to get around receiving a GRUB error 18. 
> **Error 18**: Selected cylinder exceeds maximum supported by BIOS[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

If your running out space in /boot might be just as easy to copy the files and folders in the /boot partition to the /boot folder in the Ubuntu root partition. (can be done with a live CD).

And then  change the MBR to point to Grub's  new location.[IDBS Restore Grub w/LiveCD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") 

and then merge the old /boot back in another partition. or better yet turn it into a dedicated boot loader partition.[IDBS make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_") 
(not the same thing as a separate /boot partition)

---

### Post by Helios1276 on 2008-07-20
> **louieb said:**
> Just wondering why the separate partition for  /boot?
The only time I know you need one is to get around receiving a GRUB error 18. 
[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

If your running out space in /boot might be just as easy to copy the files and folders in the /boot partition to the /boot folder in the Ubuntu root partition. (can be done with a live CD).

And then  change the MBR to point to Grub's  new location.[IDBS Restore Grub w/LiveCD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") 

and then merge the old /boot back in another partition. or better yet turn it into a dedicated boot loader partition.[IDBS make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_") 
(not the same thing as a separate /boot partition)

I had never tried it this way before, it was actually recommended by a friend and seeing as I had no problems with my Ubuntu for a while I was starting to think it was time to try something new/break something and need to fix it lol

---

