---
title: "Grub booting to clone drive"
date: 2008-05-24
forum: Hardware
---

### Post by puzzledinmn on 2008-05-24
I have a dual boot system which I back up to a clone drive about once a month.  I have a problem that I have sometimes been booting to the clone drive version of Ubuntu.  When I upgraded to version 8.04 I was alternately booting to that and 7.10.  The grub menu.lst correctly has hd0 in it so I'm not sure how grub is booting to hd1 sometimes.  Any ideas on how to fix this or do I need a new backup strategy to work with Ubuntu?  My Seagate/Acronis software has an imaging option but I'm not familiar with it and would prefer the bootable clone if possible.

---

### Post by meierfra. on 2008-05-24
I suspect that  the clone and  the original partition have the same UUID. 
So you  can either change the UUID of the clone,
or you can replace the UUIDs in menu.lst and fstab by  the device names.

Please post  the output
```
sudo blkid
```

and I'll (or someone else) can give you more detailed instruction.

---

### Post by puzzledinmn on 2008-05-27
I don't have the Ubuntu ext3 clone partition right now but you can see the other partitions (including the swap) have the same uuids so it is a true clone-

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-081E" TYPE="vfat" 
/dev/sda2: UUID="0A0AB0EB0AB0D4C3" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="4842B3AE42B39EDE" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="5984db2e-5ccc-489c-bf1f-5f3b88307039" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="3b040462-a711-48b5-85d2-3b8cc401b166" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-081E" TYPE="vfat" 
/dev/sdb2: UUID="0A0AB0EB0AB0D4C3" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sdb3: UUID="4842B3AE42B39EDE" LABEL="OS" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="3b040462-a711-48b5-85d2-3b8cc401b166" 

I'm not sure why grub wouldn't consistently boot to one or the either even if it is confused.

1. Is there an easy command to tell what drive I am booted to? (either sda or b?)
2. I'm an engineer but new to Linux so how would I change the sdb UUID? Can that be done when I am booted to the primary drive sda?  Any help would be greatly appreciated.

I guess I would still have a bootable Vista clone but it looks like my Ubuntu clone would not be bootable unless I changed menu.lst and fstab on the clone too (a lot of manual editing for a backup).  Thanks.

---

### Post by meierfra. on 2008-05-27
> Is there an easy command to tell what drive I am booted to? (either sda or b?)

```
df /
```



> so how would I change the sdb UUID? 


```
sudo tune2fs -U random /dev/sdb5 
```

will change the UUID of /dev/sdb5 to a random UUID. (this only works for ext2/ext3 file systems.

The swap space you  can just deleted with "gparted" and create again. 

I don't know how to change the UUID for ntfs and vfat.

If you do change the UUID's don't forget to update "/boot/grub/menu.lst" and "/etc/fstab" on sdb.

---

### Post by puzzledinmn on 2008-05-27
> **meierfra. said:**
> ```
df /
```


[QUOTE]I don't know how to change the UUID for ntfs and vfat.

Grub is not having any problems booting to the Vista clone.  In that sense, it works better with Windows than with Ubuntu!

---

### Post by meierfra. on 2008-05-27
> Grub is not having any problems booting to the Vista clone

Yes, but does Vista appear in the fstab of Ubuntu, that is,  are you mounting the Vista  partition in Ubuntu? If yes, you'll  never know whether you are mounting Vista or the  Vista clone. Anyway, you can just use "/dev/sd.." in place of UUID, and the problem is solved.

---

### Post by puzzledinmn on 2008-05-27
My primary drive is a Western Digital and the clone is Seagate so I can tell which drive is mounted by fstab by using Computer and right clicking to get the OS partition properties with the manufacturer model.  You do have to be careful because Ubuntu lists the clone first for some reason.  I would know if the wrong one got mounted because my shared Thunderbird mail profile is in Vista and that would be out of date. 

Are you saying that I can just replace the uuid string with /dev/sdax instead in menu.lst and fstab?  That would be much cleaner than altering uuids.

I just made an image backup of my system in 25 min.  Much faster than cloning.  Of course I am not willing to test it to see if it really works.  Matter of faith I guess.

The boot directory has a file that maps hd0 to sda.  I guess the uuid takes precedence for the Ubuntu boot. There is something at the bottom of menu.lst that says map hd0 hd1 then map hd1 hd0.  No clue what that could be for.

I was having some boot failures so I deleted the clone swap partition and it seems better now.

---

### Post by meierfra. on 2008-05-27
> Are you saying that I can just replace the uuid string with /dev/sdax instead in menu.lst and fstab? 
Yes, that's what I meant with

> Or you can replace the UUIDs in menu.lst and fstab by the device names.

in my first post.


Just replace "UUID=...." by "/dev/sd.."


> The boot directory has a file that maps hd0 to sda. I

That file is not used during boot up.

> 
There is something at the bottom of menu.lst that says map hd0 hd1 then map hd1 hd0.

This is used for booting Windows.  If Windows is not on the drive your are booting from, it is used to trick Windows  into thinking it is.

---

