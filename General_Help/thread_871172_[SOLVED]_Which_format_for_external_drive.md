---
title: "[SOLVED] Which format for external drive?"
date: 2008-07-26
forum: General Help
---

### Post by ratdog on 2008-07-26
Hello!
I have a new external usb hard drive that I will be using mainly as backup, but would also like to be able to use it to transfer bigger files between my work computer and my wifes windows laptop (still trying to get her to switch to ubuntu).  What format would you all suggest?  Is there a site that explains the pros and cons of different formats?
Thank you

---

### Post by nelmo on 2008-07-26
OK, I can't help but I've got a similar problem - took the hard drive out of my old Windows laptop but Ubuntu can't read it...so if someone answers this, maybe they can help me as well...:)

---

### Post by silkstone on 2008-07-26
If you are using Hardy, you should be able to read and write to Windows' standard NTFS filesystem.

The native Linux filesystem is Ext3 (or Ext2), but Windows does not recognise this without installing an additional driver. That's fine for your own machine, but you may not be able to do that on a work PC.

There's also FAT32 which can be read by either, but there are some limitations including a maximum file size of 4GB - that matters if you do 'zipped' backups.

So the best choice for you is probably NTFS. If it becomes fragmented, you'll have to defrag it on a Windows (XP) machine.

---

### Post by Traumadog on 2008-07-26
Hello ratdog & nelmo,

If you're going to be moving your external hard drives back and forth between Windows and Linux computers, you should probably consider using FAT32.  FAT32 is not the latest or greatest, but Windows and most Linux systems are able to read from and write to hard drives that are using that format. 

Hope this post was useful.

Best wishes, :)

Traumadog.

---

### Post by wdaniels on 2008-07-26
The pros and cons of all the various Linux filesystems are largely irrelevant if you need compatibility with Windows (unless you want to start installing extra stuff on the Windows machine). Your choice is pretty much limited to NTFS or FAT32. Of the two, NTFS is usually preferable, certainly for larger partitions. But be aware that with non-native Linux filesystems, things like file ownership can only be set for the partition as a whole. But for the general transfer/backup storage requirement you describe, I would definitely say NTFS.

Otherwise, the most significant limitations of FAT32 are a 4GB maximum file size and poor performance for large (more than say 32GB) partitions generally. [Wikipedia]("http://en.wikipedia.org/wiki/Comparison_of_file_systems") can give you all the dirty details if you're interested. Unfortunately, I don't know of a more concise reference off-hand.

---

### Post by A. J. Rimmer on 2008-07-26
I have two laptops both of which dual boot Windows and Ubuntu, and my wife still uses Windows, so I have the same situation.  My solution was to partition an external drive and leave one partition as NTFS and have a second partition as FAT32.  That way I can use the NTFS partition with Windows for backups, etc., and use the FAT32 partition to share files between operating systems (plus, Ubuntu can read from NTFS even if it can't write).

About all I use Windows for anymore is my photo management and editing software, which I like better than F-spot, so I need a fairly large NTFS partition for my Windows backups.  On Linux I tend not to have extremely large backup requirements, so the FAT32 partition is smaller.

---

### Post by ratdog on 2008-07-26
Yes, I am using hardy so it sounds like NTFS would work.  It is kind of a bummer to have to defrag it on a windows machine though.  It would probably be fine for me to install a simple driver on my work machine, so maybe I should go with ext3.  Is there a way to defrag ext3 in linux or is there just no need to do defrag those drives when using linux?
Thanks for all the help!

---

### Post by wdaniels on 2008-07-26
> **ratdog said:**
> It would probably be fine for me to install a simple driver on my work machine, so maybe I should go with ext3.

The driver actually needs to be installed on Windows (i.e. your wife's laptop, if I read your original post correctly) since it is Windows that does not support the ext filesystem by default. Ubuntu includes the NTFS driver as standard so you can use Microsoft's NTFS without installing anything extra on your work (Ubuntu) machine.

As far as I know, the [Windows ext filesystem drivers]("http://www.fs-driver.org/") only support ext2. However, ext3 is backwards-compatible with ext2 so you can still use either, only that the "journalling" features of ext3 will not be operative when used from the Windows machine.

> **ratdog said:**
> Is there a way to defrag ext3 in linux or is there just no need to do defrag those drives when using linux?

Yes, there are ways, but it might take a bit of googling to dig them up since almost nobody defrags ext filesystems (they don't really need it).

Note that there are also [Windows drivers for other popular Linux filesystems]("http://www.crossmeta.com/crossmeta.html"), such as ReiserFS and XFS if you're prepared to go down that road.

---

### Post by silkstone on 2008-07-26
ext3 and ext2 filesystems work a different way from FAT32 and NTFS. When a new file is written in ext3, space is left for the file to expand without fragmentation. With Windows filesystems, if a file expands it is likely to fragment.

In general, if an ext3 drive or partition is less than 80% full, you won't have a fragmentation problem - i.e. any fragmentation that does occur will not cause a noticeable reduction in performance.

---

### Post by ratdog on 2008-07-26
So am I understanding correctly that ext3 can be used with a windows system with no extra drivers?

---

### Post by Joeb454 on 2008-07-26
> **ratdog said:**
> So am I understanding correctly that ext3 can be used with a windows system with no extra drivers?

No. There is an externally available driver somewhere on the internet (a quick Google search should bring it up)

---

### Post by ratdog on 2008-07-26
OK, so my external drive actually is formatted in ntfs right now. However, it seems to be working very slowly and whenever I ask to delete something, it says it is unable to move it to the trash and must delete it immediately instead.  Is this normal?  I like having the option of taking things out of the trash if I make a mistake.
Also, if possible I'd like to start from scratch with a new ntfs formatting.  Is there any way at all to format in ntfs from my linux machine?

---

### Post by ratdog on 2008-07-27
Anyone?
I'd like to figure this out soon and my wife is out of town with her windows laptop so I can't use it for the ntfs formatting.

---

### Post by pjnsmb on 2008-07-27
looks like you can use Gparted -available in Synaptic- to format your external drive in ntfs

---

### Post by silkstone on 2008-07-27
See my post #3 above. Windows does not recognise ext3 or ext2 filesystems unless you install an additional driver.

Linux does recognise Windows filesystems (FAT32 and NTFS) at least if they are formatted on XP. I am not sure about NTFS if formatted with Vista.

---

### Post by vanadium on 2008-07-27
```

sudo mkfs -t ntfs /dev/sdc1

```

Replace /dev/sdc1 by the actual name of your partition.

I am not sure if you will need to install ntfsprogs first. If the above command produces an error, then first run

```

sudo apt-get install ntfsprogs

```

I did not see the entire thread but my advice for the format of an external drive is:

Use with Linux only: ext3
Share with Windows: ext2 or 3 (need windows driver for access from Windows) or ntfs
Compatibility required with other systems ("on the road") fat32 (can be read by Windows, Apple, Linux)

---

### Post by ratdog on 2008-07-27
After trying this code:   

sudo mkfs -t ntfs /dev/sdb


I get this: 

/dev/sdb is entire device, not just one partition.
Refusing to make a filesystem here!

I will try gparted now and let you know what happens...

---

### Post by vanadium on 2008-07-27
/dev/sdb is not your partition. It is your drive. You need to substitute the name of your partition (/dev/sdb1 or /dev/sdb2 ...)

---

### Post by ratdog on 2008-07-27
now I see...
I need to type 
sudo mkfs -t ntfs /dev/sdb1

---

