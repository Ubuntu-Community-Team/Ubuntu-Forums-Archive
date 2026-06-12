---
title: "After installing Ubuntu, 1 of my 2 hard drives is &quot;corrupted&quot; and I can't get access"
date: 2015-08-21
forum: Hardware
---

### Post by Boaty_Gatling on 2015-08-21
I have 2 hard drives in this laptop, both internal. [COLOR=#008000]C:[/COLOR] ( Where Windows was Installed) and [COLOR=#ff0000]D:[/COLOR] (What I used to install Ubuntu on). I dual booted it.

Windows and Ubuntu both work. I am unable to access [COLOR=#ff0000]D:[/COLOR] on both OS's. 

[COLOR=#ff0000]D:[/COLOR] worked during me demoing Ubuntu, but after installing it, I was unable to use D:.

During the installation process, when I was asked to partition or something and allocating space for Ubuntu, It prompted me to allocate a certain amount of space for Ubuntu, and it was on [COLOR=#ff0000]D:[/COLOR]. I gave Ubuntu ~40 Gbs. 

[http://imgur.com/c6hXqJE](http://imgur.com/c6hXqJE)   <---- Is a picture of what pulled up when I opened disc manager. I'm sure that might be useful to see. 
[http://imgur.com/gallery/o1VswmH](http://imgur.com/gallery/o1VswmH) <----------- are 2 pics of the overview of the 2 drivers. Not sure if that would be helpful or not.

So I just want to see is there anyway to save and get access to that driver again.

Thanks in advance, and if you need any other information please do not hesitate. I cannot lose this drive.

---

### Post by howefield on 2015-08-21
> **Boaty_Gatling said:**
> Windows and Ubuntu both work. I am unable to access [COLOR=#ff0000]D:[/COLOR] on both OS's. 

[COLOR=#ff0000]D:[/COLOR] worked during me demoing Ubuntu, but after installing it, I was unable to use D:.

Your question is a little confusing, but one thing is sure, you only have one drive, which has been partitioned into several parts. Windows sees each part as a separate drive.

Are there files that you need to access on the "D" drive or is it simply space that you want to reclaim ?

---

### Post by Boaty_Gatling on 2015-08-21
Sorry for make it confusing. I just realized I misspelled drives(hard drives) as drivers in the title. I was wondering why there was a lag of response ( thanks for responding btw). 

I have 2 hard drives. C: and D: . After installing Ubuntu, D: seemed to be "corrupt" as I wasn't able to see or get in the file. I believe I partitioned D: for linux but somehow something went wrong and I'm now not able to get access into it.

---

### Post by howefield on 2015-08-21
I have changed the thread title to reflect what you intended..

As for "lag of response" please bear in mind that this is a volunteer forum where people like you and I come together and try to help each other, forum members are spread all over the world and may be in a different time zone to you. If you want instant support try a paid service from Canonical.

Btw, you have one hard drive.

---

### Post by Boaty_Gatling on 2015-08-21
Oh. Oh that makes sense, sorry for me being a idiot. So I'm trying to get to the D: or as marked 'Local Disk'. I'm trying to reclaim that space instead of being greeted with a error of me not being able to get there.

---

### Post by The Cog on 2015-08-21
Since Ubuntu is working, let's get a list of what's *really* on the disk. Can you post the outout of the commands:
```
df -h
sudo parted -l
```

---

### Post by Boaty_Gatling on 2015-08-21
When I input *df -h* I got:

```
[COLOR=#4b0082]Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           791M  9.4M  781M   2% /run
/dev/sda8        39G   15G   23G  41% /
tmpfs           3.9G  156K  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda2       296M   53M  244M  18% /boot/efi
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           791M   56K  791M   1% /run/user/1000[/COLOR]


```

When I input *sudo parted -l I got:*


```
[COLOR=#4b0082]Model: ATA WDC WD7500BPVX-2 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  630MB   629MB   ntfs            Basic data partition          hidden, diag
 2      630MB   945MB   315MB   fat32           EFI system partition          boot, esp
 3      945MB   1079MB  134MB                   Microsoft reserved partition  msftres
 4      1079MB  457GB   456GB   ntfs            Basic data partition          msftdata
 5      457GB   457GB   472MB   ntfs                                          hidden, diag
 6      457GB   680GB   223GB   ntfs            Basic data partition          msftdata
 8      680GB   723GB   42.5GB  ext4
 9      723GB   731GB   8504MB  linux-swap(v1)
 7      731GB   750GB   19.1GB  ntfs            Basic data partition          hidden, diag[/COLOR]


```[COLOR=#4b0082]


[/COLOR]Thanks for the response.

---

### Post by The Cog on 2015-08-21
You have one hard disk, size 750GB.
Your Ubuntu is on partition 8, /dev/sda8, side 42GB, formatted to ext4 filesystem.

It seems that D: is partition 6 (223GB, Microsoft always gets the size wrong). The partition table labels the partiton as NTFS, but windows disk manager describes it as RAW. 
I have no idea why windows might show the partition as RAW rather than NTFS. The fact that Ubuntu can't mount the partition either does suggest that it is corrupt. You probably need windows based tools rather than linux tools to try to fix it (if possible) since it's a windows filesystem. 

Ubuntu does have an ntfsfix utility but its help page says it's not intended to match chkdisk. I would regard it as a last resort.

I think you will get better matching of partition sizes if you tell parted to print sizes in Gibibytes instead of Gigabytes, like this:
```
sudo parted /dev/sda unit GiB print
```

---

### Post by ajgreeny on 2015-08-21
As far as I can make out there is absolutely nothing wrong with your partition setup, though I do not know how Windows partitions disks by default any more, not having used the MS OS for several years.

Are you aware that Windows can not access or read files on any partitions formatted with the Linux filesystems such as ext4, or not without a third party driver, which used to be very unstable years ago though may now work fine.  That may be the reason for your idea that the partition is corrupt, though I am still not completely sure why you believe that to be the case, as you say that both OSs are working.

If you want to be able to create files in Ubuntu and also access them with your Windows OS you will need to save them to one of the NTFS data partitions shown in the fdisk output as sda4 and sda6, ie 4 and 6 in the list.  These can be mounted at boot of Ubuntu easily, though will not be by default, as far as I'm aware, and all files in them will then be available to both OSs without a problem.

PS:
I have just seen The Cog's reply to you; he knows more about Windows than I do so we may have confused you a bit.
However, the MS naming of partitions as C: & D: etc etc is totally confusing and unhelpful when we are trying to figure out Linux partitioning, and I also find the Windows disk-management output unhelpful in many situations.

Let's keep discussing; I'm sure we can figure this iut for you without too much trouble.

---

### Post by Boaty_Gatling on 2015-08-21
Yeah I'm all for discussing.

So I know really minimal about this whole situation, but what I see that's in the spotlight are 3 important drives. 1 with my windows installation (C : , the potentially corrupt drive that I want (D :, and the ~39gb partition from D: to store Ubuntu and it's files on. 

What I want to is ( new demand ) to have C:  and the 39gb partition that has Ubuntu on it, is to keep it like it is right now, working; but just with me able to get into D : . 

So since as stated in this [http://i.imgur.com/c6hXqJE.png](http://i.imgur.com/c6hXqJE.png) , D: is still healthy, but it was turned into a RAW file. 

So could I try to return / convert it back to a NTSF file?

---

### Post by Boaty_Gatling on 2015-08-21
So, a anti-climatic ending? It works, yay. 

It's always tempted me to wait 10 secs when I just start booting Windows(10), so it could check discs. I never really paid attention to it so I always skipped over it. Well I didn't and it just said repairing D: . 

That worked.

But really and honestly if I was never going to get that disc checked, I would of converted D: back into nsfw. This seems like a common problem on the interwebs. It would of took a few lines on cmd to convert it. 

But who knows, it works know, I would like to thank howefield, The Cog, and ajgreen(y), for helping me throughout the process and ready to discuss this topic more. Thanks.

---

### Post by ajgreeny on 2015-08-21
Great!

To help future searchers can you please mark the thread as SOLVED from the Thread Tools menu up-top.

---

### Post by oldfred on 2015-08-21
RAW can be a totally unformatted NTFS partition, or it can be the PBR or partition boot sector or first sector of a partition is corrupt. 

Some users have totally corrupted a NTFS partition by installing grub into the PBR. Sometimes it just happens.

But NTFS does keep a backup of the PBR and testdisk can restore it if the backup is valid.

       You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by The Cog on 2015-08-22
Out of curiosity I googled for "what is windows raw disk type" and this was the top result:
[http://html5.litten.com/updated-how-to-fix-external-disk-drive-suddenly-became-raw/](http://html5.litten.com/updated-how-to-fix-external-disk-drive-suddenly-became-raw/)

It may be of help, but I haven't even read it yet so don't take this as an endorsement.

---

### Post by oldfred on 2015-08-22
Your thread also suggests testdisk & shows several of the testdisk screens. Discusses other drive issues, and does point out that you do not want to format drive or else you will lose your data.

---

