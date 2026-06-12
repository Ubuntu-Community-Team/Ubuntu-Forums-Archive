---
title: "Strange problems with bad sector"
date: 2009-09-10
forum: Hardware
---

### Post by turqoisehex on 2009-09-10
I have a Western Digital 500GB RE2 with XP [ntfs] and Ubuntu 9.04 [ext4], and it's been behaving in a weird way, giving me errors about a single bad sector. I've never had a problem with bad sectors in the past, so hopefully this will be a noobish question that can be easily explained; I'll attempt to explain this in as concise a way as I can.

This first appeared when I wanted to use GParted to resize the disk to put Ubuntu on it. It gave me the error about the bad sector and said I couldn't resize it. So I used “chkdsk c: /r” in XP, rebooted twice, went back into the liveCD, and Gparted still said there was a bad sector. I then used NTFSclone --rescue to make a backup, deleted and recreated the partition in GParted, and viola, no bad sectors. I then used NTFSclone to restore the image of the drive to the partition, and the bad sector returned. 

My guess is that a file is corrupt, and it's reading it as a bad sector, if this is the case, how do I identify and remove that file? I've used spinrite, and a few more chkdsks, both with no success. Any help is appreciated, thanks.

---

### Post by thegreatsnafu on 2009-09-10
> **turqoisehex said:**
> My guess is that a file is corrupt, and it's reading it as a bad sector...

You are probably correct. The problem is, that most disk diagnosis apps, diagnose problems with, well, disks. You are pretty out of luck here. The file is probably one of the hundreds of thousands of files located in the Windows folder, and unless you wand to spend the rest of eternity going thorough files, You have to delete Windows, sorry.:(

---

### Post by tgalati4 on 2009-09-10
Take note of the block location (sector number).  Run badblocks:

sudo badblocks /dev/sda1
sudo badblocks /dev/sda2

This will take a while.

Make note of the blocks that are found (if any).

If badblocks are found then add them to the badblock list:

sudo fsck -c /dev/sda1

---

