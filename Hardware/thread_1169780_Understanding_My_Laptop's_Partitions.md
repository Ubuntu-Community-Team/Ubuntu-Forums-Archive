---
title: "Understanding My Laptop's Partitions"
date: 2009-05-25
forum: Hardware
---

### Post by Eeve on 2009-05-25
Hi everyone.

After first installing Ubuntu from within WindowsXP (via Wubi) on my Acer laptop I could dual boot and just loved it. But as soon as Ubuntu tried to install updates I started getting [bugs]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289718") which eventually killed the entire OS. I un-installed it from within Windows. So I think I need to install it directly into a partition that is properly formatted rather than in the Windows NTFS(?) format.

So... I popped in my Ubuntu 8.10 cd, booted and got to the step where I can create a partition for Ubuntu. The thing is, I can't figure out which partitions that currently exist are the ones used by Windows and the Acer recovery partition.

I know that if I just boot from the Ubuntu cd I can see 2 partitions in the filesystem: ACER and ACERDATA. I know that ACERDATA is the one that has the recovery data. However it is much larger than it needs to be and I want to ensure that's the one that gets shrunk.

The Ubuntu partition screen says that I have this

/dev/sda1 - 4%
/dev/sda2 - 47%
/dev/sda3 - 48%

Am I correct in thinking that sda1 is the swap space for windows, sda2 is Windows C: drive, and sda3 would be the (much too large) hidden AcerData partition? How would I find out what is in each of these or how each of these maps to what I see in the FileSystem explorer?

It says that after the partitioning the new situation will be:

/dev/sda1 - 4%
/dev/sda2 - 47%
/dev/sda3 - 0%
/dev/sda4 - 47%  (Ubuntu)

Does that mean it is shrinking down the sda3 then maybe that is the AcerData partition?

Forgive me for all these questions, I find this kind of stuff very confusing, and I want to be sure I'm resizing the right partition.

I will also have to tell it to format the new partition into whatever is the best for Linux.

Thanks for any help! I'm anxious to get Ubuntu back up and running again b/c I was enjoying it!

---

### Post by taurus on 2009-05-25
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by kiridude on 2009-05-25
One way to tell is to see what format type your partitions are. For example, XP will be ntfs. To tell you the truth, I found the partitioner in setup to be a quite limited - especially for resizing and reorganizing partitions. Try booting by live cd, then open a terminal and type:

```
gksudo gparted
```

Using this tool, you can format your drive how you want, then go back and install in the partition you have already created for Ubuntu.

Be careful, however, that you don't accidentally erase something, and back up important stuff beforehand.

---

### Post by Eeve on 2009-05-25
I will post the results of sudo fdisk -l as soon as I get back to it.

Thanks for the suggestion kiridude, I will look at that too.

Currently I know both Acer and AcerData are Fat32. I know they are the two large ones sda2 and sda3. Just don't know which is which. I would assume Windows is installed in sda2 b/c it would make sense for it to be first. 

From within Windows it only shows 2 partitions, the small one sda1 is hidden. *sigh* so bizarre. I don't understand why it would hide info from the user about their own computer.

---

### Post by Eeve on 2009-05-27
Results:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8f0ffa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638        7583    55793745    c  W95 FAT32 (LBA)
/dev/sda3            7584       14593    56307825    c  W95 FAT32 (LBA)
```

I'm going to guess that sda2 is Windows and sda3 is that acerdata folder.
Not sure what sda1 Compaq diagnostics means.

---

### Post by kiridude on 2009-05-28
I would back up your stuff to an external source (ext. drive, dvd, etc) and drop all partitions except for windows (sda2). Now, if your disk fails, you're backups are on the same disk - not a good idea.

Then, download 9.04 (why install an outdated version), and split your disk between windows and ubuntu.

---

### Post by raymondh on 2009-05-28
> **Eeve said:**
> Results:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8f0ffa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638        7583    55793745    c  W95 FAT32 (LBA)
/dev/sda3            7584       14593    56307825    c  W95 FAT32 (LBA)
```

I'm going to guess that sda2 is Windows and sda3 is that acerdata folder.
Not sure what sda1 Compaq diagnostics means.


Hello Eeeve,


Similar to us (in ubuntu) having  a separate /home partition for good reason, SOME OEM/Retailers set up the HD to have a separate data partition.  Here's a probable tip (though am not sure as I have not used windows in a while ...... in windows, look at the directory of documents.  If it is different from C:, then PROBABLY your docs go to the acerdata partition.   That being the case, I would double-check and make sure you are not deleting your own files.... and as kiridude says, back up/copy your personal files to an external in the meantime as you explore your 2-boot configuration/installation

Compaq diagnostics .... when you return the machine to compaq/acer for repair, they rely on that program to diagnose and troubleshoot your problem....it just makes their job faster.


Good luck and regards,

---

### Post by Eeve on 2009-05-28
Hmm... interesting.

Luckily I have essentially zero personal files on this laptop, it is not my main machine. My only concern is that if it dies, I don't have any recovery CDs. It's out of warranty so sending it to Acer for repairs won't happen. Actually, now that I think about it, what am I scared of? If it dies completely, I will format and install Ubuntu alone!

I think what I will do is leave the windows partition and compaq diagnostics alone for now and size the nearly empty ACERDATA sda3 down to say 5 gigs. Then create a new partition with the rest of the room for Ubuntu.

And yes, burning a new iso of the latest version of Ubuntu is what I'll do.

Thank you to everyone for the comments. I find the Ubuntu community very welcoming to newbies!

---

### Post by raymondh on 2009-05-28
> **Eeve said:**
> Hmm... interesting.

Luckily I have essentially zero personal files on this laptop, it is not my main machine. My only concern is that if it dies, I don't have any recovery CDs. It's out of warranty so sending it to Acer for repairs won't happen. Actually, now that I think about it, what am I scared of? If it dies completely, I will format and install Ubuntu alone!

I think what I will do is leave the windows partition and compaq diagnostics alone for now and size the nearly empty ACERDATA sda3 down to say 5 gigs. Then create a new partition with the rest of the room for Ubuntu.

And yes, burning a new iso of the latest version of Ubuntu is what I'll do.

Thank you to everyone for the comments. I find the Ubuntu community very welcoming to newbies!

Good call.

Some folks have had an ubuntu install (/root) at between 8-15GB's.  I, personally, make mine 20GB as I tend to grow my install "fat" and prefer not to mess with re-sizing later on.  I also have /home in a different partition and that, I make sure I allocate appropriately for my needs.  Albeit, nowadays, an external USB hardrive is quite affordable so... your mileage and intentions may vary.

Here are some links of interest for reference

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Good luck and happy ubuntu-ing.

Regards,

---

