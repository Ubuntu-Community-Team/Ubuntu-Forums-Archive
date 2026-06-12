---
title: "2tb ext HD"
date: 2019-04-28
forum: Hardware
---

### Post by swangnation on 2019-04-28
HI guys, I'm new to the forum. A few days ago i purchased a 2tb ext hard drive. I transferred about 900gb of videos to it, video formats are avi, mkv, mp4....the usual extensions however when i play my videos on my tv, they freeze after a few seconds.  On my windows computer which has Mpc player, they play fine. On this ubuntu computer through vlc they play fine as well.
With the old 1tb ext hd plugged into the tv, no problem either.

With this the video just freezes. 

When i run sudo fdisk -l i get the following output.

```
Disk /dev/sdb: 1.8 TiB, 2000398933504 bytes, 3907029167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: dos
Disk identifier: 0xa39efa50

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1        2048 3907026943 3907024896  1.8T  7 HPFS/NTFS/exFAT
```

In Gparted i got the same "type" as above.

I know that the "type" is ready to use on windows or Ubuntu but would it be better perhaps if i assigned a new label? defragment or reformat perhaps?

Thanks

---

### Post by TheFu on 2019-04-28
If it is a Linux only disk, then the partition would be much faster if it was using a native Linux file system, like ext4. Native Linux file systems have other capabilities that NTFS and FAT-anything don't have as well.

If you must share it with other devices that aren't Linux, then NTFS is probably the best of the available choices, but know that NTFS access is slow on Linux without some manual mount-time tweaks and it cannot be made faster through any GUI point-n-click tool, at least not currently.  The Gnome team has been working on making gvfs faster, but I don't know when/if those changes will be included in any Ubuntu.  There is a fix through mount options today that has been around perhaps, 10 yrs.

As for what your TV does, I don't know and that would be something to ask that manufacturer.  I don't have a TV.

It isn't clear what is connected to the TV that you are describing video freeze. The disk could be failing, the PSU for the disk could be bad or the USB cable, assuming it is USB, could be bad.  If it is within the return period, might be easiest to just take it back for a new one. Of course, wipe the disk and run dban over it at least once before returning.  Deleting the files alone won't stop someone else from using tools to see what's there.

New disk have an early failure rate that can be surprisingly high in the first month.  Wouldn't hurt to google for the exact model to see if there are lots of failures or if there is a firmware update for the disk.  Most disk vendors are secretive about lots of failures. Seagate lied for 3 yrs when they have a systematic issue with their 750G and larger disks in the mid-2000s.  I have some older Seagate disks - 300G and 320G that are still spinning - 15 yrs old and showing no issues at all. Some of the huge Seagate disks - 8TB and 10TB have been really good, compared to other vendors, for failures too, according to the quarterly backblaze disk reports.  You and I will never buy enough drives for statistical samples to matter, but backblaze does.

Label doesn't matter. If you've only copied huge files over, there won't be much, if any fragmentation, and new HDDs are shipped with NTFS format already. 

One more thing, file extensions only describe the "container", not the stuff stored inside. 15 yrs ago, .avi files might have had mpeg4, xvid or divx video and either mp2 or mp3 audio.  Each of those types has different encoding/decoding levels. In general, the harder they are to decode, the more CPU is needed and prettier the video/audio inside. There wasn't any hardware decoding in GPUs for that format, though I had an xvid encoder that was all handled in hardware.

---

### Post by mastablasta on 2019-04-30
> **TheFu said:**
> 
One more thing, file extensions only describe the "container", not the stuff stored inside. 15 yrs ago, .avi files might have had mpeg4, xvid or divx video and either mp2 or mp3 audio.  Each of those types has different encoding/decoding levels. In general, the harder they are to decode, the more CPU is needed and prettier the video/audio inside. There wasn't any hardware decoding in GPUs for that format, though I had an xvid encoder that was all handled in hardware.

i suspected this first. A workaround would be media player (like Kodi on raspberry pi, chrome stick or similar small PC). however, if these same files work well on another disk then the issue could very well be in the disk. you would need to at least to run SMART test for that. but even smart test are not definitive. and are more an indicator than anything else.

it could also be that the disk drivers that are not well recognised by TV. again a media player in between disk and TV would solve this.

---

### Post by SeijiSensei on 2019-04-30
Do all the files freeze, or only ones above a given size?  

Do ones that worked before on the old disk still work now?  Are the problematic files more recent and thus likely to require decoding for H.264/H.265 which the TV may not have?  How old is the TV?

fdisk might report that the partition type is NTFS, but that doesn't mean the filesystem placed there is also NTFS.  Plug the device into Ubuntu and then run the "mount" command.  It will report the type of each mounted filesystem, for instance,

```
/dev/sda6 on /home type ext4 (rw,relatime)
```

---

