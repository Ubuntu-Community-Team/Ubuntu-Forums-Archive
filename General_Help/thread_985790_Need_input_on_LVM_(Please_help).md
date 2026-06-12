---
title: "Need input on LVM (Please help?)"
date: 2008-11-18
forum: General Help
---

### Post by Th3Professor on 2008-11-18
I recently read a &#8220;howto&#8221; on LVM+RAID and it successfully threw me off because the individual writing it only used RAID1... I'm using RAID5... they set up LVM, then RAID, then did more with LVM (moved, reduced, removed, and recreated volumes). I'm wondering if I could do just as well to set up RAID first and LVM second (no &#8220;redundant&#8221; use of commands).
 

 I have 4 hard drives, each 500GB, using #1 for OS/apps/editing, #s 2,3,4 for RAID+LVM.
 

 I'd like to utilize 3 sections of the space (on HDD2,3,4) for the following purposes:
 &#8220;vault&#8221; = /studio/vault (mount point) for housing audio from my music recording studio.
 (I currently have &#8220;/studio/workspace&#8221; on hard drive #1 for editing audio.)
 &#8220;zone&#8221; = /zone (mount point) for housing my non-studio &#8220;home&#8221; (Solaris if possible).
 &#8220;nomad&#8221; = /nomad (mount point) for housing my alternate-*nix home (testing systems).
 

 Would this work?
 

```

 # fdisk /dev/sdb
 (add primary 1, set to &#8220;linux raid auto&#8221;, write/exit)
 # fdisk /dev/sdc
 (add primary 1, set to &#8220;linux raid auto&#8221;, write/exit)
 # fdisk /dev/sdd
 (add primary 1, set to &#8220;linux raid auto&#8221;, write/exit)
 # mdadm -C /dev/md0 -c 128 -l 5 -n 3 /dev/sdb1 /dev/sdc1 /dev/sdd1
 # pvcreate /dev/md0
 # vgcreate vg0 /dev/md0
 # lvcreate -n vault -L 755G vg0
 # lvcreate -n zone -L 53G vg0
 # lvcreate -n nomad -L 53G vg0
 # mkdir /studio/vault /zone /nomad
 # mkfs.xfs /dev/vg0/vault
 # mkfs.ext4 -b 4096 -E stride=32 /dev/vg0/zone
 # mkfs.ext4 -b 4096 -E stride=32 /dev/vg0/nomad
 # mount /dev/vg0/vault /studio/vault
 # mount /dev/vg0/zone /zone
 # mount /dev/vg0/nomad /nomad
 # vi /etc/fstab
 (add)
 /dev/vg0/vault    /studio/vault    xfs    rw,noatime    0    0
 /dev/vg0/zone /zone    ext4    rw,noatime    0    0
 /dev/vg0/nomad    /nomad    ext4    rw,noatime    0    0
 (save/quit)
 
``` ...or... would I have to do this?
 (I'm going off RAID1 tips and trying to make this work with RAID5...)
 

```


 # fdisk /dev/sdb
 (add primary 1, set to &#8220;linux lvm&#8221;, write/exit)
 # fdisk /dev/sdc
 (add primary 1, set to &#8220;linux lvm&#8221;, write/exit)
 # fdisk /dev/sdd
 (add primary 1, set to &#8220;linux lvm&#8221;, write/exit)
 # pvcreate /dev/sdb1 /dev/sdc1 /dev/sdd1
 # vgcreate vg0 /dev/sdb1 /dev/sdc1 /dev/sdd1
 # lvcreate -n vault -L 755G vg0
 # lvcreate -n zone -L 53G vg0
 # lvcreate -n nomad -L 53G vg0
 # mkdir /studio/vault /zone /nomad
 # mkfs.xfs /dev/vg0/vault
 # mkfs.ext4 -b 4096 -E stride=32 /dev/vg0/zone
 # mkfs.ext4 -b 4096 -E stride=32 /dev/vg0/nomad
 # mount /dev/vg0/vault /studio/vault
 # mount /dev/vg0/zone /zone
 # mount /dev/vg0/nomad /nomad
 # vi /etc/fstab
 (add)
 /dev/vg0/vault    /studio/vault    xfs    rw,noatime    0    0
 /dev/vg0/zone /zone    ext4    rw,noatime    0    0
 /dev/vg0/nomad    /nomad    ext4    rw,noatime    0    0
 (save/quit)
 (I have no idea if I can use these next steps with RAID5
or if it's a RAID1-only thing; it seems like these would defeat
the purpose in a level 5 RAID, I'm not sure...) ???
 # modprobe dm-mirror
 # pvmove /dev/sdc1
 # vgreduce vg0 /dev/sdc1
 # pvremove /dev/sdc1
 # pvmove /dev/sdd1
 # vgreduce vg0 /dev/sdd1
 # pvremove /dev/sdd1
 # fdisk /dev/sdc
 (set type to &#8220;linux raid autodetect&#8221; and write/exit)
 # fdisk /dev/sdd
 (set type to &#8220;linux raid autodetect&#8221; and write/exit)
 # mdadm -C /dev/md0 -c 128 -l 5 -n 3 /dev/sdc1 /dev/sdd1 missing
 # pvcreate /dev/md0
 # vgextend vg0 /dev/md0
 # pvmove /dev/sdb1 /dev/md0
 # vgreduce vg0 /dev/sdb1
 # pvremove /dev/sdb1
 # fdisk /dev/sdb
 (set type to &#8220;linux raid autodetect&#8221; and write/exit)
 # mdadm /dev/md0 -a /dev/sdb1
 
```Thank you for your replies!

---

### Post by Th3Professor on 2008-11-19
bump

---

### Post by psusi on 2008-11-20
You have the right idea with the first one.  The second looks more like a pointless exorcise in moving data from drive to drive to drive.

---

### Post by Th3Professor on 2008-11-20
> **psusi said:**
> You have the right idea with the first one.  The second looks more like a pointless exorcise in moving data from drive to drive to drive.

I've read so many RAID+LVM, LVM, LVM+RAID, etc. webpages that my eyes are ready to pop out. lol I believe the one that had the steps (in the 2nd example I put in the OP) was this:
[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

I took that and reworked it a bit, the 1st example I posted in the OP was my variation on it, hoping that the less-redundant steps would be equally effective, though I'm not really sure.

The other day I went ahead and used the 2nd example, ended up having problems by creating volumes at max size, which were thus unable to be moved around. So perhaps it would work if I start with smaller volume sizes and max them out after everything's finished, though not sure. I also had to zero out the disks as it ended up with a "still busy" kind of thing that couldn't be -f or -ff to removal.

The 2nd approach appears to create volumes, create raid, reduce (remove) volumes one-by-one while moving other volumes to raid, and after moving recreating the previously created volumes. I don't see the point in it. However, if there is one, I'd like to know the advantage in it. lol :p

The 1st approach, the one I came up with after doing some digging, seems more appropriate though I'm not sure if it is as effective as it could be.

1. fdisk 3 drives to raid type.
2. mdadm the raid5.
3. pv/vg/lv -create the volumes.
4. mkdirs and mount them.
5. update fstab.

That's it... though it seems so simple that it seems like it's missing something.

The other idea is...

1. fdisk 3 drives to lvm type.
2. pv/vg/lv -create the volumes.
3. mkdirs and mount them.
4. update fstab.
5. pvmove, vgreduce, pvremove 2 of the 3 volumes.
6. fdisk 2 of the 3 drives to raid type.
7. mdadm the raid5 (2 drives + 1 "missing").
8. pvcreate another physical volume.
9. vgextend the original pv with the new pv.
10. pvmove, vgreduce, pvremove volume 3.
11. fdisk volume 3 to raid type.
12. mdadm add volume 3.

Why do all that?

That looks like volume>raid>volume... is that somehow "better" than raid>volume?

Here's another webpage, which I have not read yet (will be reading it today), it might shed a new light on this subject:
[http://tjworld.net/wiki/Linux/Ubuntu/HardyRAID5EncryptedLVM](http://tjworld.net/wiki/Linux/Ubuntu/HardyRAID5EncryptedLVM)

---

### Post by psusi on 2008-11-20
Either way you end up with lvm over raid.  The second example seems to be geared towards explaining how to migrate an existing lvm only setup over to lvm on top of raid.

---

### Post by Th3Professor on 2008-11-20
That make sense.

Here's another link:
[http://www.gagme.com/greg/linux/raid-lvm.php](http://www.gagme.com/greg/linux/raid-lvm.php)

---

### Post by edvar on 2008-11-24
LVM on top of RAID is the recommended and best way. Not sure why you would want LVM and then RAID and then LVM again on top of the RAID.

RAID would give you the fault tolerance and on top of the safe RAID setup you can have the flexibility of LVM. Remember, LVM doesn't give you any fault tolerance (if you only have LVM and one of your disks fail then say goodbye to your data).

Just create partitions of the same size on each disk and then create a RAID array WITH THEM:

# mdadm --create /dev/md0 --level=5 -n 3 /dev/sda2 /dev/sdb2 /dev/sdc2

In my case I have 3x 500Gb disks each with 1x 8GB partition (sda1, sdb1 and sdc1) and 1x 492GB partition (sda2, sdb2 and sdc2). Sda1 is my boot partition (the boot partition cannot be on RAID or LVM or else your system won't boot), sdb1 is my swap partition and sdc1 is unused. 

After creating the array I have a /dev/md0 disk with 968Gb.

Now it's just a matter of doing the usual LVM setup (pvcreate, vgcreate, lvcreate) and voila: you get yourself a fault tolerant LVM setup where you can add, remove, resize partitions on the fly with no need to reboot.

---

### Post by Th3Professor on 2008-11-25
> **edvar said:**
> LVM on top of RAID is the recommended and best way. Not sure why you would want LVM and then RAID and then LVM again on top of the RAID.

Glad to hear more agreeing with RAID+LVM (instead of LVM+RAID+LVM). I believe, as someone mentioned earlier, that the webpage where I found LVM set up twice might have referring to someone who had an LVM set-up prior to setting up RAID. Who knows. :)

> **edvar said:**
> RAID would give you the fault tolerance and on top of the safe RAID setup you can have the flexibility of LVM. Remember, LVM doesn't give you any fault tolerance (if you only have LVM and one of your disks fail then say goodbye to your data).

My thoughts exactly... security of RAID, flexibility of LVM.

> **edvar said:**
> Just create partitions of the same size on each disk and then create a RAID array WITH THEM:

# mdadm --create /dev/md0 --level=5 -n 3 /dev/sda2 /dev/sdb2 /dev/sdc2

Okay I have not done that (re: partition prior to setting up RAID+LVM), though I can go ahead if it's necessary.

I did this:
1. Set up 3 disks with RAID5 using only 1 partition (entire disks).
2. Set up LVM on the 3 disks with LVM using multiple "partitions" (volumes).

I didn't think separate partitions would be necessary pre-RAID and pre-LVM set-up if I was going to basically partition them via LVM anyway... or is it? (Why?)

> **edvar said:**
> In my case I have 3x 500Gb disks each with 1x 8GB partition (sda1, sdb1 and sdc1) and 1x 492GB partition (sda2, sdb2 and sdc2). Sda1 is my boot partition (the boot partition cannot be on RAID or LVM or else your system won't boot), sdb1 is my swap partition and sdc1 is unused. 

After creating the array I have a /dev/md0 disk with 968Gb.

That's odd. I also have 3x 500GBs, though after RAID5 set-up I have 931GB, not 968GB. How did you end up with that much more?

I'm not using boot on any of my RAID+LVM hard drives, I have a 4th 500GB drive that I use for boot, operating systems, applications, and temp/editing storage that can be transfered to the RAID+LVM for safe storage. As far as boot goes, I suppose I don't have to worry about how that plugs into the 3x disk set-up. Though, I am curious how to squeeze in 968GB instead of 931GB. :D

> **edvar said:**
>  Now it's just a matter of doing the usual LVM setup (pvcreate, vgcreate, lvcreate) and voila: you get yourself a fault tolerant LVM setup where you can add, remove, resize partitions on the fly with no need to reboot.

That flexibility in LVM - resize partitions, for example - is where I wonder why I'd need to set up partitions prior to all of that (such as via fdisk).

---

### Post by edvar on 2008-11-25
I know it's a bit of a complicated setup (partitioning + mdadm + lvm pvs, vgs, and lvs) but once you get the concept right it becomes easy.

No problem if you're using entire disks (I had to partition each disk with more than one partition because I needed the boot and swap partitions outside of the RAID array and didn't have a 4th disk to put them there as you do). However you need to create a partition for each entire disk using all space of the disk and specify the type of the partition on fdisk as type fd (Linux Raid Auto) before creating the md device. You can have consistency problems in the future if you don't do that and only use /dev/sda (unpartitioned) instead of /dev/sda1 (partitioned) on your mdadm --create command.

Even if you don't use RAID, you'll need to setup the partitions before hand (in that case they would be type 8e - Linux LVM) so they can become the PVs (Physical Volumes). Remember, the flexible part of the LVM are the logical volumes (LVs). That's why you create a large Volume Group (VG) and create smaller LVs inside it so you can resize the LVs as you wish. The LVs can only be as bigger as the total VG size (which is the sum of the size of all the PVs assigned to it). You can add more PVs later (e.g. more disks or partitions) to the VG so you can extend its size but bear in mind the PVs are pretty much static (not resizable as the LVs).

After you have the partitions, you create the md device and them setup LVM as it suits you best. As a last step you create the file systems on the logical volumes using mkfs (don't mix up mkfs with fdisk partitioning - they are different).

In regards to the size, well, I have less usable space than you (916Gb out of 984Gb total) as you can see here:

/dev/md0:                                  
        Version : 00.90                    
  Creation Time : Sat Nov 22 12:09:33 2008 
     Raid Level : raid5
     Array Size : 961120512 (916.60 GiB 984.19 GB)
  Used Dev Size : 480560256 (458.30 GiB 492.09 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

My mistake!

---

### Post by Th3Professor on 2008-11-25
Gotcha, everything ya said makes sense, and yep mkfs/fdisk/etc. Here's what I ended up doing:

1. **fdisk** (1 primary each, type set to raid auto)
2. **mdadm** (128 chunk-size, level 5 raid)
3. **lvm** (pv/vg/lv-etc.)
4. **mkfs** (xfs on "vault" (music) and ext3 on the rest; used -b 4096 and stride 32)
5. **mount** (new RAID+LVM set-up)
6. **fstab** (update for auto mount at boot)
7. **Rock on and have fun with a sweet set-up!**

:guitar:

...I actually already set up my RAID+LVM a week or two ago, though I still haven't done much with it yet just in case I'd have to redo it all. lol ;)

I really wanted to use ext4 but it presented problems with the set-up so I reverted back to ext3 for some of my storage space. I was able to stick with xfs for the other space with no hitches.

---

### Post by psusi on 2008-11-26
Now if you are feeling adventurous you can try using all 4 drives in the raid5 instead of keeping one out to boot from ;)

---

### Post by Th3Professor on 2008-11-26
> **psusi said:**
> Now if you are feeling adventurous you can try using all 4 drives in the raid5 instead of keeping one out to boot from ;)

;) Very true.

Well, all 4 are 500GB. They would make perfectly fitting puzzle pieces.

However... I run Vista, Linux, and Unix... I'm an OS nut. #-o

At present I have these partitions set up, though I may still change things around a bit:

d1p1, /boot
d1p2, vista
d1p3, boot for unix (for sysv (solaris) or bsd (openbsd))
d1p4:
d1p5, / for linux (ubustu right now, will try 64 studio later)
d1p6, /studio/workspace (editing (and temp storage for) music I record)
d1p7, swap
d1p8, swap
d1p9, / (other than boot) for unix
d1p10, "other" linux (for learning new linux systems)

d2,3,4 as raid+lvm:
LV vault - /studio/vault (primary storage for music I record)
LV zone - /zone (for bsd or sysv home, i.e. /zone/home for solaris (if I can make it work))
LV nomad - /nomad (for "other" linux / and all subdirectories)

One of the reasons I opted for disk1 being excluded from disks2,3,4 raid+lvm is so I can have some improved performance on the non-storage space (more actively used). Though, I still had to pull the little plastic pins out of all 4 hard drives before hooking them up inside the computer case (to move their 1.5Gb/s to 3.0Gb/s). That'll help performance on both disk1 and disks2,3,4, even if a little. I went ahead and set up the file systems on the raid+lvm, at least the ext3, with 4x32 (bytes per block and stride size) to line up with the 128 chunk-size of the raid5 to help performance a little more since it's naturally reduced a little with the raid. The portion of the raid+lvm that's using xfs didn't require any flags/options like the 4x32 ( 128 ) since it defaults at that anyway (xfs is an awesome file system for raid). I was pretty bummed that I couldn't get ext4 to work. :( Oh well, maybe in due time the *nix coders will put ext4 into the mainstream. I'd like to be able to "shelf" ext3, mostly because ext4 offers some very nice improvements.

I suppose you can another reason for 1 disk being excluded is the data on that disk is not crucial, like if it is lost or damaged then all will be well because the primary storage is separate. Having one disk separate slightly increases the amount of space available, which is useful when running multiple OS set-ups.

I do like the idea of running all 4 disks on raid+lvm, which is actually exactly why I ended up getting a 4th disk identical to the first 3. :) So if/when I go through another period of time where I opt to run only one operating system, then I could group all of it together and have a very nice, simple, clean set-up. That'll be very cool.

Actually, right now I'm mostly using:
d1p1, /boot
 d1p2, vista
 d1p5, / for linux (ubustu right now, will try 64 studio later)
 d1p6, /studio/workspace (editing (and temp storage for) music I record)
 d1p7, swap
 d1p8, swap
 
I'm presently only "somewhat" using:
 d2,3,4 as raid+lvm:
LV vault - /studio/vault (primary storage for music I record)
...though that's because I haven't purchased my "home recording studio" equipment yet. <grin> I can't wait to get that stuff going! It'll be very helpful for my career (music).

I'm working on getting other linux systems installed on raid+lvm for:
d1p10, "other" linux (for learning new linux systems)
 
I'm not sure how to get unix (sysv or bsd) installed on raid+lvm:
d1p3, boot for unix (for sysv (solaris) or bsd (openbsd))
  d1p9, / (other than boot) for unix
d2,3,4 as raid+lvm:
LV zone - /zone (for bsd or sysv home, i.e. /zone/home for solaris (if I can make it work))
  LV nomad - /nomad (for "other" linux / and all subdirectories)

However, last time I tried installing any system other than Debian-based I was using dmraid, which is awesome when it comes to running Vista and *nix together, though with the drive that's separate from the raid+lvm it doesn't matter lol... so I just went with mdadm. So, I'm guessing that, since my OSs will now be all on a non-raid non-lvm disk, they'll install just fine (even unix, since I reserved a primary partition for it).

Though, I found out that it is possible to install pretty much any Linux system on at least raid, using dmraid, with something similar to this:

[LIST=1]
[*]boot livecd
[*]goto terminal
[*]sudo apt-get install dmraid
[*]sudo modprobe dm-raid4-5
[*]sudo dmraid -ay
[*]cd /dev/mapper
[*]ls (for raid "nvidia_[letters]")
[*]ubiquity (install)
[*]used guided partition with raid volume (let it automatically do it, it just created / and swap)
[*]disabled grub install
[*]reboot to livecd again
[*]sudo fdisk nvidia_[letters] (listed in /dev/mapper) (fdisk to see how it's set up, prtn.5 was / and prtn.6 was swap)
[*]sudo mkdir /target
[*]sudo mount nvidia_[letters]5 /target
[*]sudo mount --bin /dev /target/dev
[*]sudo mount -t proc proc /target/proc
[*]sudo mount -t sysfs sys /target/sys
[*]sudo chroot /target
[*]apt-get update
[*]apt-get install dmraid
[*]apt-get install grub
[*]mkdir /boot/grub
[*]cp /usr/lib/grub/[arch]/* /boot/grub
[*]grub --no-curses
[*]device (hd0) /dev/mapper/nvidia_[letters]
[*]find /boot/grub/stage1
[*]root (hd0,4)
[*]setup (hd0)
[*]quit
[*]update-grub (selected "yes" for new menu.lst)
[*]vi /boot/grub/menu.lst
[*]changed "# groot=(hd0,0)" to "# groot=(hd0,4)"
[*]changed to hd0,4 in boot entries
[*]added: title windows root (hd0,0) chainloader +1
[*]opted to change delay to 30 and commented out "hiddenmenu"
[*]save/exit
[*]update-grub (kept "local file")
[*]reboot (vista & linux both work now)
[/LIST]
 (The Vista part is of course optional.)

...however... I found that it's going to take some more digging to see how I can establish a "work-around" for installing Unix on the same raid. We shall see.

8-)

---

### Post by psusi on 2008-11-26
Whoa there cowboy.  A couple of things:

1) I am 99% sure that sysv and bsd do not understand linux mdadm raids and lvm, so there's no getting them on there.

2) dmraid is for hardware fake raid support.  It has nothing to do with mdadm so if you don't have a hardware fake raid controller, it is of no use to you.  See [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for more info.

3) ubiquity can't partition dmraid volumes, so you have to set up the partitions by hand first and have ubiquity install to the existing partition(s).

---

### Post by Th3Professor on 2008-11-26
> **psusi said:**
> 1) I am 99% sure that sysv and bsd do not understand linux mdadm raids and lvm, so there's no getting them on there.

Henceforth, 1 separate hard drive. :D

> **psusi said:**
> 2) dmraid is for hardware fake raid support.  It has nothing to do with mdadm so if you don't have a hardware fake raid controller, it is of no use to you.  See [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for more info.

I have BIOS RAID (on the mobo), though am not currently using it.

> **psusi said:**
> 3) ubiquity can't partition dmraid volumes, so you have to set up the partitions by hand first and have ubiquity install to the existing partition(s).

The steps I listed worked with me, though I didn't mention that I had set up partitions prior. <grin> EDIT: The "guided partition" bit was something I used along with ubiquity, it worked. Though I just went with the steps available, as I had already set up partitions anyway.

---

### Post by edvar on 2008-11-26
Just to add some more info, if you want to install Ubuntu from scratch with MDADM and LVM using the Live CD (not sure why LVM is not the default on Ubuntu as it is on Fedora):

(make sure you started your computer on the Live CD environment and your network connection is up)

BEFORE INSTALLATION

Plan your partitions and volumes before hand. For instance, in my case I have a md device /dev/md0 that handles my RAID 5 on 3x 500GB disks. This is my main Physical Volume PV. I added the PV /dev/md0 to a Volume Group called VG. On top of VG I have 4 logical volumes:

lv-root = 20GB for the / partition
lv-home = 50GB for the /home partition
lv-var = 20GB for the /var partition
lv-media = 650GB for my /MediaCenter partition with all my media files

The rest of the space is unallocated on VG so I can extend my LVs in the future, if needed.

Other than that my /boot partition is on a separate device /dev/sda1.

After you have your partition scheme figured out, execute these commands on the terminal:

# sudo -i
# apt-get install lvm2 mdadm system-config-lvm  
# modprobe dm-mod
# fdisk (check fdisk man page on how to create the FD - Linux RAID Auto type partitions)
# partprobe
# mdadm --create (check mdadm man page and use the partitions created on the step above to create the /dev/md0 device)
# partprobe (again, just in case)
# system-config-lvm (for the LVM setup tool GUI or, if you feel adventurous, use the command line tools pvcreate, vgcreate and lvcreate)

INSTALLATION

Proceed with the normal installation. The Partitioner will recognize the LVM volumes and will format them with EXT3 accordingly.

AFTER INSTALLATION

Now you need to add the MDADM and LVM modules to your kernel so the RAID and LVM Volumes are recognized after reboot:

# mkdir /myraid
# mount /dev/VG/lv-root /myraid (assuming you have a LV for your root partition)
# mount /dev/VG/lv-var /myraid/var (assuming you have a LV for your rvar partition)
# mount /dev/sda1 /myraid/boot (assuming your boot partition is on /dev/sda1 - REMEMBER: BOOT PARTITIONS CAN NEVER BE ON MDADM OR LVM DEVICES)
# mount --bind /dev /myraid/dev
# mount -t devpts devpts /myraid/dev/pts
# mount -t proc proc /myraid/proc
# mount -t sysfs sysfs /myraid/sys
# chroot /myraid
# apt-get install mdadm lvm2
# exit

---

### Post by psusi on 2008-11-26
> **edvar said:**
> Just to add some more info, if you want to install Ubuntu from scratch with MDADM and LVM using the Live CD (not sure why LVM is not the default on Ubuntu as it is on Fedora):

Because it is incompatible with other operating systems, and many Ubuntu users dual boot with Windows.  Also it does not provide any benefit to most users who don't need to do online resizing of partitions or use volume snapshots.

---

### Post by edvar on 2008-11-26
Yeah, good point... From a Windows partition I wouldn't be able to see md devices or logical volumes. With a normal EXT3 partition at least you can install the EXT2 Driver on Windows and access files on the EXT3 partition.

MDADM + LVM is a better setup if you only have Linux on your box or at least use it more often than other OSes.

---

### Post by Th3Professor on 2008-11-27
My RAID+LVM is working for my 3 storage disks, with a 4th disk housing OSs, apps, temp/editing space. This is with Vista & Linux (Ubustu at the moment).

My current dilemma involves getting Unix and other Linux systems installed. Although they should install just fine on the spare partitions of my non-RAID/non-LVM disk, they are, for some reason... not installing. I'm an advocate of OpenBSD, though opted to reserve a general "unix" partition for sysV and BSD systems, and my spare Linux partition can be pretty much any other linux.

I have a primary reserved for Unix and a logical reserved for Linux.

At present, I'd like to install Solaris and Gentoo.

When I put in the CD or DVD to install, it starts up but "hangs" part-way through. I'm not sure why. Bad discs?

I'm not even touching the RAID+LVM disks with the other Unix/Linux installs. However, once I *do* install the other OSs on the nonraid/nonlvm disk, I'd like to be able to use some of the storage spaceon the raid+lvm disks with those. I know that will work with Linux, though am not sure if there is a work-around for Unix (or at least Solaris).

The most recent release of Solaris 10 is much more Linux-friendly than ever before, so I am betting that - while it won't boot from those disks - it will have some way of accessing the disks at least for storage purposes (as I do with other systems).

I might have to set up a non-ZFS file system in Solaris, though, if I want it to be able to recognize LVM, much less, RAID.

That is something I could ask in a Unix forum or Solaris-specific forum, though I've already tried in one other message board with no luck so far.

---

### Post by Th3Professor on 2008-11-28
...anybody have any ideas on how to install Solaris and Gentoo on this type of set-up?

---

