---
title: "extra internal drive not active"
date: 2010-02-05
forum: Hardware
---

### Post by NNing on 2010-02-05
Greetings.

I'm another newbie ... sorry! Any help would be appreciated.

----

The basic problem is that one of my internal hard drives won't be seen by Ubuntu (Karmic Koala 9.10).

----

**BACKGROUND:**

I have 4 internal drives:
Three of these are NTFS formatted (including 1 with XP on it).
The other one has Ubuntu on it.

Within Ubuntu, I could see the three other drives in 'Places' but I couldn't read/write to them as they had to be mounted to Ubuntu. 

Being new, when I right-clicked one of the drives and saw the 'mount drive' option, I thought yep, good place to start. 

The drive mounted/mapped to my file system/media directory. However, I still couldn't do anything with it there because the system told me I was not the owner.

Fortunately, I found another way to successfully mount NTFS drives to Ubuntu. (You have to download 'NTFS Configuration Tool'. It gets added to System Tools. When you open this helpful program, it finds the extra drives that are available for mounting and makes things straightforward.)

I got the other two NTFS drives accepted by Ubuntu this way with read/write access (including the XP drive). 

However, the original NTFS drive would not be seen by the NTFS Configuration Tool. I 'unmounted' it (right-click menu). Still not seen by the tool. 

When I opened Disk Utility, I saw that this drive was shown differently from the other two NTFS drives. It had no partition it seemed. 

I downloaded and opened Gnome Partition Editor (GParted) to have a look. It just said it was in NTFS format but not much else (that I could decipher).

So I booted into XP to see how things looked from that side. I decided to reformat the drive from within XP (to NTFS still). I then booted into Ubuntu again to see if the NTFS Conf Tool would recognise the drive like it had with the others - but it didn't. 

So I formatted it again, this time from within Ubuntu using Gparted (to a Linux-share format). I rebooted into Ubuntu to let the system find it - but no luck. The drive doesn't show up anywhere (not even in Places). I can only see it if I go into Disk Utility or GParted. If I get information about it from within GParted, it says that the drive is not active.

Interestingly, in Disk Utility the drive shows up not once but three times. This is different to when I first started looking for my internal drives within Ubuntu (when there was only one copy of each. There is still only one copy each of the other drives.)

Sorry to ramble so much but I have no idea what details are important and what aren't. 

I'm now reformatting the drive again from within XP to NTFS, to try and get back to square one. I just need the NTFS Conf Tool to recognise it like it had with the others but I'm not sure if, each time I reformat it, it confuses the system with adding to a registry somewhere.

....any givers of wisdom wishing to share enlightenment?

cheers,
NiNo.

---

### Post by Grenage on 2010-02-05
Post the results of these two commands:

```
sudo blkid
sudo fdisk -l
```

Please also post the contents of /etc/fstab

---

### Post by NNing on 2010-02-05
**Results for sudo blkid:**


/dev/sda1: UUID="74F44805F447C7D6" LABEL="XP" TYPE="ntfs"
/dev/sdb1: UUID="da39c1d6-5717-48ec-af2d-afb49081af38" TYPE="ext4"
/dev/sdb5: UUID="f40c9a1b-4cfe-4f7d-9f19-e64b3015893a" TYPE="swap"
/dev/sdc1: UUID="EA38C34538C3100D" "LABEL="AUDIO" TYPE="ntfs"
/dev/sdd: TYPE="nvidia_raid_member"
/dev/mapper/nvidia_fagfacab1: UUID="FA9C06349C05EBC7" LABEL="VIDEO" TYPE="ntfs"

(FYI, the drive in question is the last one labelled "VIDEO", which is the only one with 500GB. The other three are 150GB each.)


**Results for sudo fdisk -l:**


255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68554b4e
 
Device Boot   Start   End     Blocks     Id   System
/dev/sdb1     1       17495   140528556  83   Linux
/dev/sdb2     17496   18241   5992245    5    Extended
/dev/sdb5     17496   18241   5992213    82   Linux swap / Solaris

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98439843

Device Boot   Start   End     Blocks     Id    System
/dev/sdc1     1       18240   146512768  7     HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier = 0x5e2b4034

Device Boot   Start   End     Blocks     Id    System
/dev/sdd1     1       60801   488384001  7     HPFS/NTFS


**Results for gksu gedit /etc/fstab:**


(gksu:2377) Gtk-WARNING **: cannot open display:

FYI I tried it again and got the same result but with a different number (gksu: 2532) Gtk-WARNING **: cannot open display:


In hope and trigue,
NiNo.

---

### Post by Grenage on 2010-02-05
> /dev/mapper/nvidia_fagfacab1

Do you have some on-board RAID, is it a RAID port that it's plugged into?  I think this is the cause of the problem.

---

### Post by NNing on 2010-02-05
oh hey, I didn't realise you were still at the computer.... I'll check back faster next time.

I used to have Raid 0 (striped) but I took it off before putting XP and Ubuntu on. 

The big drive (the one in question) was never part of a Raid. It was always stand-alone.

Thanks for your replies BTW.

NiNo.

---

### Post by Grenage on 2010-02-05
> oh hey, I didn't realise you were still at the computer.... I'll check back faster next time.

It's a forum, so there's rarely a rush. ^^

My guess is that the board is configured to use that SATA port as a RAID device port.  It might be worth looking in the BIOS to see if you can disable RAID functionality, or try a non-RAID port.  This is only my best guess; I once had a board with dedicated RAID SATA ports.

---

### Post by NNing on 2010-02-05
Would partitioning factor into this?

In Palimpset Disk Utility, when I click on the other three drives for details, I see that they are each "partitioned".

In contrast to these, the large drive is shown not once but 3 times (each time showing the full size - 500GB). 

For two of these entries, it is described as "unallocated space", and I am given the option to "create partition" eg. NTFS or other. 

For the remaining entry (the one with the assigned 'VIDEO' title), it is described as "not partitioned", and I am told that it contains a "mountable filesystem". 

It's weird that it shows up three times. I don't think it did that the first time (before I first mounted it by right-clicking the drive inside Places.... If only I'd found NTFS Conf. Tool earlier!)

Cheers,
NiNo.

---

### Post by Grenage on 2010-02-05
Partitioning shouldn't have an effect here.  I am pretty sure the issue lies with the port, or at least the configuration of the port on the motherboard.  Working on that assumption, any changes you need to make will be 'outside' the OS.  Either the main BIOS, or NVRAID BIOS.

---

### Post by NNing on 2010-02-05
> **Grenage said:**
> 
My guess is that the board is configured to use that SATA port as a RAID device port.  It might be worth looking in the BIOS to see if you can disable RAID functionality, or try a non-RAID port.  This is only my best guess; I once had a board with dedicated RAID SATA ports.


Just re-checked BIOS and all SATA ports are disabled for RAID. 

My humble techno opinion (based on cosmic instinct alone!) is that Ubuntu bewitched it when I first tried to mount it and it wouldn't recognise me as the owner.... Before that, only one entry of the large drive showed up in Disk Utility, and it showed details like the rest of them.

Worst case scenario = put Ubuntu back on & hopefully add all drives with NTFS Conf tool?

---

### Post by NNing on 2010-02-05
> **Grenage said:**
> Partitioning shouldn't have an effect here.  I am pretty sure the issue lies with the port, or at least the configuration of the port on the motherboard.  Working on that assumption, any changes you need to make will be 'outside' the OS.  Either the main BIOS, or NVRAID BIOS.


Drat. Am gonna have to log off soon & see if a tech-savvy mate can come over to look at cables. 

Thanks heaps for the input. If anything changes, will add to post for anyone else's reference.

N.

---

### Post by Grenage on 2010-02-05
Ok :)

Sounds like a plan; I hope you and your friend have some luck!

---

### Post by NNing on 2010-02-07
Hooray, problem solved.

The crux of it was that the drive must once have been in a (3-way) Raid set up (as Grenage thought). 

In theory I'd bought the drive new, and I know I'd never had it raided (other drives yes, this one no) - so the shop must have sold it on to me after it had come out of a Raid. The /dev/mapper is apparently a give-away of this.

Even though I'd formatted this drive a number of times, my mate told me that formatting doesn't usually erase Raid info, which can stay hidden at the end of the drive in a small space. To erase that, you need to do a 'low grade' format in small byte sizes (eg. 64KB) so no info can hide. I think there are a number of ways of doing this, but we typed a command into the terminal along the lines of: 
sudo dd if=/dev/zero of=/dev/sdd bs=64KB

For more, see: 
[http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux](http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux)

Incidentally, before we got to this point, we tried to get Ubuntu to ignore the Raid by adding (nodmraid) before (quiet splash) in the (sudo gedit grub) terminal but this didn't make a difference. 

For more, see:
[http://ubuntuforums.org/showthread.php?t=646340](http://ubuntuforums.org/showthread.php?t=646340)

After reformatting and rebooting, the Disk Utility now only saw one 500GB drive, (not 3, and not with dev/mapper info attached but with the simple /dev/sdd info). 

However, it wouldn't allow me to create a partition for it in Disk Utility and so could not be mounted/used. In GParted, I was not given the option to format the partition to NTFS, and the disk file type showed as "unknown". 

To get round this, I booted into XP and did a quick format from there (into NTFS). However, if others don't have dual-boot, they'll need to find another way to format the partition to NTFS (if that's what they want).

After that I just booted into Ubuntu again, and as it showed up nicely in Disk Utility, opened the NTFS Configuration Tool and it immediately suggested mounting the drive for me, like it had with the others : ) 

Hope this post helps anyone else in a similar position.

NiNo.

---

### Post by Grenage on 2010-02-07
Glad you got it sussed, nice work :)

---

