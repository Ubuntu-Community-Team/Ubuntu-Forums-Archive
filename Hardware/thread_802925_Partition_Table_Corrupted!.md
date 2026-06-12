---
title: "Partition Table Corrupted!"
date: 2008-05-21
forum: Hardware
---

### Post by AldenIsZen on 2008-05-21
Story short, I think when I installed EXT2 IFS  which was supposed to allow me to read and or write to EXT2 partitions in Windows XP it corrupted my partition table. At least that is what research seems to be telling me.

 Story Long, I am unable to get Acronis Disk Director 10 to start in Windows. It crashes with an error message stating "unable to find partitions." Not much on Google with error code, sorry I don't have it right now, but can get. When using GParted, I see all partitions correctly, however there is a red X next to a few of my NTFS partitons that I want to change. It states to boot into Windows, do a FSK (i think) and reboot twice. After doing so there is no change.

 I can see all my partitions correctly in Windows XP, however it seems to be booting slowly. That could be related to me using Super Grub Disk and doing what I believe was an installation of grub in effect to every partition. Of course it has ran through my mind that could also be what caused this to happen. Hardy boots and works fine. 

 I ended up using Super Grub Disk to install Windows MBR to my 1st hard drive, 2nd partition where Windows is (first is a hidden FAT16 Dell recovery partition,or was until EXT2IFS, now it is not listed as hidden with partition software.) Then I installed GRUB to my 2nd hard drive 2nd partition where Hardy is installed. 1st is swap partition.

 I tried using Partition Table Doctor, but not sure if it can help. It doesn't correctly see the labels of my (sick) partitions, just their size. When I try to "rebuild" the partition tables, the options include partitions no longer there, and all of my good partitions. The (sick) partitions are undersized, so I don't commit the changes in fear of losing data accessible to me now. I don't have room to just shuffle data and recreate partitions. I am considering, but would like to avoid deleting needed data.
 
 I'd laugh but I have little idea what I am doing, and don't want to laugh hysterically and then start crying. :(


 Thanks for taking the time to read this and understand my issue. I am not sure where else to turn. EXT2IFS didn't seem to have any forums.

---

### Post by Thanh-BKK on 2008-05-22
Hello :)

You know what? I had the exact same happen to me!! Just that i installed the thing under Vista, and immediately after i was able to see the first BSOD's since several years on Windows XP and lately Vista (first ever under vista in fact).

I removed the thing, but the BSOD's stayed - the error messages, if any, pointing to all sorts of files, mostly drivers. Needless to say, i hadn't installed any drivers or anything apart from that dodgy piece of software. 

Also Vista booted notably slower!

I then tried a "system restore" and that failed - "an unexpected error" or something was the message. 

I reinstalled Vista over itself and that cured it, however the very next day i pulled it out and replaced the HDD with a virgin one - which since holds Ubuntu Hardy, and Ubuntu Hardy ONLY.

In your case i would strongly recommend to do a Windows repair install - i.e. boot to XP, then insert the XP CD and run setup, chose to "upgrade - recommended" when you are asked for the type of install, and let it run. It looks like it will do a brand new install, but it only installs over itself, replacing damaged system files in the process and, importantly, fixing the partition table and MBR.

After that's done you will likely only be able to boot into XP. Don't worry - just use your Ubuntu Live CD to reinstall Grub, and all should be well again :)

I wish you success :)

Your Thanh

---

### Post by AldenIsZen on 2008-05-22
I wonder if it would fix the partitions on my 2nd hard drive? I will try that, unless I find another solution. I just had to to a repair install and I hate it. I still can't get all the updates to net framework due to a bug with doing a repair install on Media Center.

 I think I would be better of just buying that 1 TB drive I have been planning on and exporting the data off, but I am planning a trip back home real soon and don't have the funds, especially with the cost of gas to be making "unneeded" purchases.

 Anyone else have any other solutions?

---

