---
title: "SD memory card problems 8.04"
date: 2008-09-27
forum: General Help
---

### Post by MPD on 2008-09-27
_O.K. I have several cards:_
1G card works great w/Fspot
2G Says "Unable to mount location"
Another 1G Shows card but nothing else
8G Is a Notice.txt.lnk File,won't open.

I am very new at Linux and thank any responses !

Also curious if this is the right distro for a family used to (but never again going to) XP?

                                                    Thanks again Mike

---

### Post by vanadium on 2008-09-27
Sure, Ubuntu is the right distro to a family used to a proprietary OS. You just need to get used to it for a while.

Problems with reading removable drives (and cards in this case) can be due to the file system not being in a good state, for example because it was removed too quickly from Windows without using the "safely remove hardware" icon or from Linux, without right-clicking the icon of the volume on the desktop and choosing "unmount".

If you still have Windows, it will be easiest for you to check the memory cards under Windows using the Windows tools.

Linux can also check various file systems although thee are limitations for ntfs, the file system of Windows, because that one is not only complex, but also proprietary.

The general command is, assuming for example that the partition we want to check is /dev/sdc1

```

sudo umount /dev/sdc1
sudo fsck /dev/sdc1

```

In Linux, we can only check a file system when it is not in use. That is why the first command makes sure the partition is unmounted.

Normally, Ubuntu will recognize the file system automatically and invoke the proper tool. For a badly damaged disk, you might need to add the option -t to specify the file system.

---

### Post by MPD on 2008-09-28
Thanks you so much for the reply.I posted a few places and not one person was willing to help me...Other than you.Let me explain what is going on.The one card that works is from my camera and opens perfect into Fspot.The other cards don't work at all in anything now other than the 2G in my palm tx.I just got lucky when I burned the Ubuntu 8.04 cd and loaded it onto the Dell Latitude D410.I learning everything that I know from searching and using Ubuntu Hardy.I purchased an 8G w/reader on ebay,When I load it I get Notice.txt.lnk I click it and "pop up" Couldn't dislpay media/sd/notice.txt.lnk. I click O.K. and have no idea what to open it with.When I unmount volume and put another card in the read (2G) nothing happens at all.Please help,I just want to figure this out but it is way above me at this time.Thank you again.

---

### Post by Sef on 2008-09-28
> The other cards don't work at all in anything now other than the 2G in my palm tx.

Did the 2 GB card come with the palm tx?

---

### Post by vanadium on 2008-09-28
Try checking the file systems first. To this aim, you will need to determine the device name of the partition. To this aim, unmount and remove the card. Open a terminal, type

```
sudo blkid
```

Now insert a card, wait until the icon appears on the desktop and again issue the command

```
sudo blkid
```

You will see an extra line: that is the partition of your card. The beginning of the line is the device na,e. It will look like /dev/sd##. Let us assume you find it is /dev/sdc1.

To check the file system, you first need to unmount it: a filesystem you check may not be in use. You can right-click the icon to unmount, or unmount directly from the co,,and line:

```
sudo umount /dev/sdc1
sudo fsck /dev/sdc1
```

The second command runs the check. It will tell you whether the file system is healthy or not. You can copy/paste the output here so we can help to interpret it.

---

### Post by MPD on 2008-09-28
Did the 2 GB card come with the palm tx?

No,I bought it at a later time.I had XP and everything worked fine.Now the card (2G) can read everything on the Palm TX.I just can't use it on the Ubuntu laptop,I plug it in and nothing at all happens.It doesn't even recognize it.

---

### Post by MPD on 2008-09-28
O.K. I did the unmount and then in terminal sudo blkid.
Got this:
/dev/sda1: UUID="c1d1d5e1-7ed9-43f4-b9d7-377b26cc0f90" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="e865ebcb-a0cf-4cb2-bd64-7fd1ec62d65c" 
/dev/sdb1: LABEL="SD" UUID="54E2-843B" TYPE="vfat" 

Then typed in terminal:
sudo fsck /dev/sdb1

Got:
 sudo fsck /dev/sdb1
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? (Still blinking) man am I lost....

---

### Post by MPD on 2008-09-28
Sorry,I don't know if this matters but that is with the 8G card.Eventualy what I'm trying to do is get everything on my 8G card.And by the way..Thank you everyone for the help.

---

### Post by vanadium on 2008-09-29
This indicates some problem that might be the cause. I am not sure what the right answer is and whether one can know what it should be. I would probably answer " 1"  to remove the inconsistency that was detected.

---

### Post by MPD on 2008-09-29
O.K. I did that with the Number 1.I still get a Notice.txt.lnk file that I can't open.What can I use to open it? Also,I tried the same thing with my 2G caed and get this:
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Reclaimed 1 unused cluster (32768 bytes).
Leaving file system unchanged.
/dev/sdb1: 263 files, 31641/62262 clusters

I can't find the files or anything having to do with the card anywhere on my computer.I'll keep trying things though.Thank you for your help.

---

### Post by MPD on 2008-09-29
Update
I got the 8G card working in Ubuntu,Now I'm trying to get it to work on the Palm TX.The 1G I have is the only one that will work in both the Ubuntu box and the Palm TX (I have no idea why).I'll keep trying.Again,Thank you guys so much for gettingme this far.

---

### Post by ThrobbingBrain66 on 2008-09-29
Does your Palm support high capacity SD cards (anything 4GB+ is considered SDHC)?  Depending on the age of your device, you may need to update the Palm software/firmware to be able to read SDHC cards.

---

