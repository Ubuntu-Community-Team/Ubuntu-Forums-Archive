---
title: "No swap?"
date: 2008-10-02
forum: General Help
---

### Post by joey-elijah on 2008-10-02
I used Wubi to install Ubuntu which i've since upgraded to a fully fledged install.

However, i don't think i have a swap partition? COuld this be the issue with hibernation/sleep?

I ran *sudo fdisk -l* and this is what it spat out. 

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9730    78148604   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x682a8121

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1946    15631213+   b  W95 FAT32
/dev/sdb2            1947       19457   140657107+   b  W95 FAT32

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7087ef7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

```

If i don't have a swap partition, how do i go about making one? Thanks

---

### Post by Ryadt on 2008-10-02
The hibernation issue is definitely due to the swap partition. 
Have a look here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by jerome1232 on 2008-10-02
Wubi doesn't support hibernation.

edit: Wow somehow I missed the upgraded to a full fledged install sorry

---

### Post by joey-elijah on 2008-10-02
thanks for the link - followed the tutorial, but i'm not sure my swap is working? I dunno,... lol

joey@joey-desktop:~$ cat /proc/meminfo
MemTotal:      3632144 kB
MemFree:       3061512 kB
Buffers:         17708 kB
Cached:         240516 kB
SwapCached:          0 kB
Active:         369604 kB
Inactive:       152312 kB
HighTotal:     2752448 kB
HighFree:      2232040 kB
LowTotal:       879696 kB
LowFree:        829472 kB
SwapTotal:     1048568 kB
SwapFree:      1048568 kB
Dirty:             824 kB
Writeback:           0 kB
AnonPages:      263692 kB
Mapped:          73456 kB
Slab:            21600 kB
SReclaimable:    12372 kB
SUnreclaim:       9228 kB
PageTables:       2336 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   2864640 kB
Committed_AS:   727276 kB
VmallocTotal:   114680 kB
VmallocUsed:     46056 kB
VmallocChunk:    61428 kB

and 

joey@joey-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       3632144     583016    3049128          0      17928     246600
-/+ buffers/cache:     318488    3313656
Swap:      1048568          0    1048568

Is there a reason it's not being used? I have 4GB ram and gave the swap file 1GB.

Also, since enabling (if i have!) swap my 'hibernate' option has disappeared from the log off dialog. Any reason for this?

EDIT: although i have 4gb ram, i am using 32bit Ubuntu - it'sa  long story, but my "upgrade" wrote itself over my 64 bit Vista....

---

### Post by ibuclaw on 2008-10-02
What is "top" telling you?
```
top
```

If swap is off/non-existant, the first five lines of the app should look like this:
```

top - 19:08:03 up  1:34,  3 users,  load average: 1.23, 1.36, 1.58
Tasks: 114 total,   1 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s): 31.9%us, 14.6%sy,  0.0%ni, 53.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1024792k total,  1014000k used,    10792k free,   102992k buffers
**Swap:        0k total,        0k used,        0k free,**   282908k cached

```

If it appears to be off, run "swapon"
```
sudo swapon -a
```
and try "top" again.

If this is to no avail, you'll have to boot into the Ubuntu LiveCD, shrink the Ubuntu partition using the "Partition Editor" and create a swap partition in the empty space.

Regards
Iain

---

### Post by joey-elijah on 2008-10-04
thanks for your reeeeeeply.

I think my swap is on then becasue first 5 lines be:

```
top - 14:20:06 up 9 min,  1 user,  load average: 0.95, 0.98, 0.60
Tasks: 128 total,   1 running, 126 sleeping,   0 stopped,   1 zombie
Cpu(s): 14.5%us,  5.1%sy, 25.0%ni, 38.3%id, 16.9%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3632144k total,   810740k used,  2821404k free,    18916k buffers
Swap:  1048568k total,        0k used,  1048568k free,   326728k cached
```

If I'm a total n0ob and am, infacto, incorrect someone let me know! But for now I'll assume it's on.

That said, since creating a swap file, 'hibernation', as an option, has disappeared from the logout menu. I type 'hibernate' into terminal but it said it had some kind of nvida error...

```
Some modules failed to unload: nvidia
hibernate: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).

```

i used --force to override it, but it didn't do anything. SO i either don't have hibernate (tho it's checked as on in the gnome/apps/power_manager thingy) or it just has a vendetta against moi.

ANy help?

---

### Post by porchrat on 2008-10-04
If you have 4Gb of RAM and 1Gb swap you probably won't be able to hibernate anyway...to hibernate you generally need at least as much swap as you have RAM, as the contents of your RAM need to be saved to the swap in order to hibernate.  Can't save 4Gb to 1Gb.

May as well post the contents of your fstab file as well.

Please post the ouput of this:

```
sudo cat /etc/fstab
```

---

### Post by joey-elijah on 2008-10-04
> **porchrat said:**
> If you have 4Gb of RAM and 1Gb swap you probably won't be able to hibernate anyway...to hibernate you generally need at least as much swap as you have RAM, as the contents of your RAM need to be saved to the swap in order to hibernate.  Can't save 4Gb to 1Gb.

May as well post the contents of your fstab file as well.

Please post the ouput of this:

```
sudo cat /etc/fstab
```

Haha, great! So does that mean i can't hibernate/sleep at all?! Unless i have a 5gb Swap... thats sucks!

here's the output you asked for:

```
 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sdb1
UUID=08417625-7107-48f0-a27c-e4b1e4f2e737     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda1
UUID=BC7C6C797C6C3076       /media/drv0       ntfs-3g         defaults      0   0
/mnt/1024Mb.swap  none  swap  sw  0 0


```

=o \

---

### Post by porchrat on 2008-10-04
Unfortunately yes you're going to need a little more than 4Gb in order to hibernate, although depending on what you do with the system you may be able to get away with a little less than that, hwoever it will still need to be pretty close to 4Gb.

You do seem to have a swap drive according to that fstab.

If you could also run this command that might help.

```
sudo blkid
```

---

### Post by joey-elijah on 2008-10-04
Grr - thats annoying in a way. If i up my SWAP file to 4.5 GB would that work? hmm... i don't mean to get gigabyte stingy but...

out put:
```
/dev/sda1: UUID="08417625-7107-48f0-a27c-e4b1e4f2e737" TYPE="ext3" 
/dev/sdb1: LABEL="M-XHZM-L.M-1SNM--M-^Yp" UUID="48E2-4C9B" TYPE="vfat" 
/dev/sdc1: UUID="5D5165E912592A10" LABEL="ExTeRnAl DriiiiVe" TYPE="ntfs" 
/dev/sdb2: UUID="48E2-4D5A" TYPE="vfat" 

```

---

### Post by ibuclaw on 2008-10-05
I can feel for you to some extent, but it is exactly the same in Windows. The difference being that is occurs on the same partition. Just in a 4.5GB pagefile...
Not that I want to indulge in lectures, but a swap does have it's advantages. For instance, this will prevent fragmentation in the main filesystem.

Regards
Iain

---

### Post by joey-elijah on 2008-10-05
i have a 4.5Gb swap file now, but i still can't get Ubuntu to hibernate..

---

### Post by coewar on 2008-10-05
Just to comment about the comparison with Windows... that's exactly the the problem... 

If I have swap partition set to be more than RAM, then I'm essentially just waisting the disk space. If I have the option of putting the "hibernated data" anywhere I want, I'm good because if I'm not using the system, I'm not technically wasting the space; it'll be freed up when I start it up again.

On side note, my Hibernate doesn't work either. after I tell it to Hibernate, it just blanks the screen and sits there indefinitely. If I power off and back on, it's booting as if I cut the power. :)

---

### Post by joey-elijah on 2008-10-06
mine's got past that.... and now when told to hibernate just tries, fails and returns to desktop... it's a feature that really needs a bit more attention sheld on it.

---

### Post by porchrat on 2008-10-07
I've heard people ahve problems hibernating when using slightly earlier ati catalyst drivers (like 8.5 or so as opposed to the newer 8.9)  I've recently ugraded my drivers but haven't tried hibernating (I can't hibernate either...some machines have ACPI issues...maybe you are one of the unlucky ones as some machines just hibernate out of the box).

---

