---
title: "My Book 3 TB suddenly fails to mount"
date: 2012-01-03
forum: Hardware
---

### Post by superscriptdot on 2012-01-03
Hey all,

My Book previously worked fine on my Acer Aspire 5538G, then during a file transfer it crashed. When attempting to reopen, I got the following error:

```
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```To be on the safe side, I backed up some files to another external HD through a Windows machine. After that I reconnected the drive to Ubuntu and have since been getting this error:

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```I ran dmesg | tail and got this the first time:

```
[13744.092986] NTFS-fs error (device sdb1): parse_ntfs_boot_sector(): Volume size (2TiB) is too large for this architecture.  Maximum supported is 2TiB.  Sorry.
[13744.093000] NTFS-fs error (device sdb1): ntfs_fill_super(): Unsupported NTFS filesystem.
[13774.439993] NTFS-fs error (device sdb1): parse_ntfs_boot_sector(): Volume size (2TiB) is too large for this architecture.  Maximum supported is 2TiB.  Sorry.
[13774.440119] NTFS-fs error (device sdb1): ntfs_fill_super(): Unsupported NTFS filesystem.
[13782.360944] NTFS-fs error (device sdb1): parse_ntfs_boot_sector(): Volume size (2TiB) is too large for this architecture.  Maximum supported is 2TiB.  Sorry.
[13782.360957] NTFS-fs error (device sdb1): ntfs_fill_super(): Unsupported NTFS filesystem.
[13828.989517] NTFS-fs error (device sdb1): parse_ntfs_boot_sector(): Volume size (2TiB) is too large for this architecture.  Maximum supported is 2TiB.  Sorry.
[13828.989530] NTFS-fs error (device sdb1): ntfs_fill_super(): Unsupported NTFS filesystem.
[14899.658952] type=1400 audit(1325548018.572:19): apparmor="DENIED" operation="open" parent=11942 profile="/usr/bin/evince-thumbnailer" name=2F6D656469612F4D7920426F6F6B5F2F416B7475616C6E6F2F736B75706E612F43656E696B2D506F7374612D4E6F7472616E6A69 pid=11947 comm="evince-thumbnai" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
[14899.893620] type=1400 audit(1325548018.808:20): apparmor="DENIED" operation="open" parent=11942 profile="/usr/bin/evince-thumbnailer" name=2F6D656469612F4D7920426F6F6B5F2F416B7475616C6E6F2F736B75706E612F43656E696B2D506F7374612D4E6F7472616E6A69 pid=11947 comm="evince-thumbnai" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
```The Windows machine still recognised it, so used it to erase some files to keep it under 2 TB. After reconnecting to Ubuntu and running dmesg | tail again, I got this:

```
[ 7416.137869] sd 10:0:0:0: [sdb] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[ 7416.139831] sd 10:0:0:0: [sdb] No Caching mode page present
[ 7416.139838] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 7416.148175]  sdb: sdb1
[ 7416.150567] sd 10:0:0:0: [sdb] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[ 7416.152693] sd 10:0:0:0: [sdb] No Caching mode page present
[ 7416.152702] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 7416.152709] sd 10:0:0:0: [sdb] Attached SCSI disk
[ 7416.997097] NTFS-fs error (device sdb1): parse_ntfs_boot_sector(): Volume size (2TiB) is too large for this architecture.  Maximum supported is 2TiB.  Sorry.
[ 7416.997109] NTFS-fs error (device sdb1): ntfs_fill_super(): Unsupported NTFS filesystem.
```Have I made it worse and is there any way to fix this? I don't have enough internal disk space to backup everything while reformatting the drive.
Also, the other HD I did the backup on through Windows is now in read-only mode in Ubuntu - can I return it to write mode without touching the files?

I would really appreciate any help!

---

### Post by superscriptdot on 2012-01-05
I still haven't figured this out; anyone have any ideas?

---

### Post by Mark Phelps on 2012-01-05
Unfortunately, you may have a LOT of work to do to recover your files.

Mentioning this because, ironically, I had this happen to me last week.  Part way into a file transfer, suddenly, the external drive dismounted -- and would not mount again.  When I hooked it up to a Windows PC to run CHKDSK on it, Windows said the filesystem type was "Raw"!  Had to use Runtime Software's GetDataBack for NTFS to recover the directories and files.

You can try what I did -- hooking the drive up to a Windows PC and seeing if that can mount it.  If it can, perhaps running CHKDSK for you will fix it.  If that doesn't work, then read on below ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by hramat on 2012-03-02
I am having the same issue with the My Book. I just have it completely new for few hours. It works fine on Win7, Archlinux but in Ubuntu 11.10 it gives the same NTFS-fs error as described above. 

Same issue was reported [here]("http://www.wodejukebox.org/viewtopic.php?f=4&t=3312&start=14")

Any news on proper resolution.

---

### Post by matt_symes on 2012-03-02
Hi

From parse_ntfs_boot_sector() in fs/ntfs/super.c in the kernel sources.

```
/*
         * On an architecture where unsigned long is 32-bits, we restrict the
         * volume size to 2TiB (2^41). On a 64-bit architecture, the compiler
         * will hopefully optimize the whole check away.
         */
        if (sizeof(unsigned long) < 8) {
                if ((ll << vol->cluster_size_bits) >= (1ULL << 41)) {
                        ntfs_error(vol->sb, "Volume size (%lluTiB) is too "
                                        "large for this architecture.  "
                                        "Maximum supported is 2TiB.  Sorry.",
                                        (unsigned long long)ll >> (40 -
                                        vol->cluster_size_bits));
                        return false;
                }
        }
```

You have a 32-bit PC or Ubuntu install ? If you are then 2TiB is a coded limit because of the 32-bit architecture you are using.

Kind regards

---

### Post by hramat on 2012-03-03
Ubuntu is 32bit system (Kernel 3.0.0.16.19) run on nettop Foxconn nt-a3500 which I use as media center. This one could also run 64bit system. Not sure if 64bit system would be better.

I have also used in on 32bit Archlinux (Kernel 3.2.8 ) and the disk works just fine.

As I could find this could be caused by MBR vs. GPT; as the standard MBR-based partitioning scheme only supports system disks that are less than 2TiB in size [[1]("http://www.funtoo.org/wiki/GUID_Booting_Guide"),[2]("http://lime-technology.com/forum/index.php?PHPSESSID=1095ab0d49130611afdaf40fbb1bffc0&topic=5904.msg154988#msg154988")]


Seems, [splitting the disk onto two primary partitions would solve the issues for now]("http://www.wodejukebox.org/viewtopic.php?t=3312&p=30422")

---

### Post by matt_symes on 2012-03-03
Hi

I think 64bit would get around the 2TiB partition limit. If your PC can use it then i would upgrade.

Kind regards

---

### Post by hramat on 2012-03-03
I have just changed the partition table of this external disk from msdos to gpt but it did not help. I am getting the same error as before.

I will try to make 2 partitions, both below 2tb just to prove that it works.

I would not like to change the system from 32 to 64 bit. But maybe I will give it a try later on. I use it as a media center with openbox and xbmc. It took me some time to set it up. Also I prefer 32bit over 64bit so far.

---

### Post by matt_symes on 2012-03-03
Hi

> I will try to make 2 partitions, both below 2tb just to prove that it works.

That will/should work.

Kind regards

---

### Post by hramat on 2012-03-05
I have just tried ubuntu 64bit live CD and the disk was recognized and automatically mounted. I hope I will succeed with VAAPI HW acceleration

---

