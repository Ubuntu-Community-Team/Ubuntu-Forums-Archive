---
title: "mount says GPT partition table corrupt, gdisk is inconclusive"
date: 2018-12-27
forum: Hardware
---

### Post by lindajeanne on 2018-12-27
Greetings!

Firefox crashed my computer, and since rebooting, I've been unable to mount my primary data drive. (The drive with the OS seems, fortunately-and-knock-on-wood, to be fine)

Trying to google for solutions mostly finds things that are not  compatible with GPT, and the directions that  are specific to GPT assume that the "gdisk /dev/sdc" check would have  found something wrong.

Trying to mount manually:

```

~$ sudo mount /dev/sdc1 /mnt
mount: /mnt: can't read superblock on /dev/sdc1.

```

Using gdisk on /dev/sdc indicates no problems...

```

~ $sudo gdisk /dev/sdc
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): v

No problems found. 3437 free sectors (1.7 MiB) available in 2
segments, the largest of which is 2014 (1007.0 KiB) in size.

Command (? for help): i
Using 1
Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: 92FA9CD9-947D-4DF4-B841-F4062791ACA4
First sector: 2048 (at 1024.0 KiB)
Last sector: 1953523711 (at 931.5 GiB)
Partition size: 1953521664 sectors (931.5 GiB)
Attribute flags: 0000000000000000
Partition name: 'data-drive'

Command (? for help): 


```


...but trying to access /dev/sdc1 fails utterly:

```

~ $sudo gdisk /dev/sdc1
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

Command (? for help): v

No problems found. 1953521597 free sectors (931.5 GiB) available in 1
segments, the largest of which is 1953521597 (931.5 GiB) in size.

Command (? for help): i
No partitions

```

Parted shows me the following:

```

Model: ATA ST1000DM010-2EP1 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name        Flags
 1      1049kB  1000GB  1000GB  ext4         data-drive

```



Help?

---

### Post by oldfred on 2018-12-27
All that says is partition is ok.
But file system may be corrupted, probably more by your forced reboot. Any abnormal shutdown often corrupts file system and you have to run repairs. If NTFS you need chkdsk which you an only run from Windows. For ext 4 you use fsck.

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdc1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdc1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdc1

      
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[https://askubuntu.com/questions/926461/whats-the-difference-between-the-magic-reisub-reset-and-holding-down-the-power](https://askubuntu.com/questions/926461/whats-the-difference-between-the-magic-reisub-reset-and-holding-down-the-power)

---

### Post by lindajeanne on 2018-12-27
Sweet, I'm back in action! Thanks for the help. :)

I'll put Ctr+Alt_SysReq REISUB on a post-it on my monitor :D

---

### Post by oldfred on 2018-12-27
Glad that worked.

You can change to Solved.

---

### Post by lindajeanne on 2018-12-27
[s]I tried, but I can't find it? (The option was there when I first created the thread, but now I can't find it -- either as an option on the thread, or when editing the first post, or when creating a new post) :confused:[/s]


(nvm, it was hiding in plain sight)

---

