---
title: "Hard drive not recognized(Ubuntu), works in XP."
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by Kristo, act 1 on 2009-07-20
Hi,

I'm having trouble with an invisible (on Ubuntu 8.10) hard drive, which I hope some noble personality might be able to help me with. Needless to say, I'm not very experienced with Ubuntu. :(

I have XP and Ubuntu 8.10 installed on the same, partitioned hard drive. Also, I've got a hard drive physically identical to the other, which I use for storage. I have installed windows first, so it is NTFS.
What I need help with is that the storage hard drive doesn't show up in gparted or fdisk -l. On XP it works alright, though. I'm doing my best to provide info straight up, so please bear with me. I hope maybe someone has experience in this particular problem type, which seems to be very common by the looks.:? So, all the info I could gather:

Links I found important but did not know how to use if to use:

[http://ubuntuforums.org/showthread.php?t=370386](http://ubuntuforums.org/showthread.php?t=370386)
[http://ubuntuforums.org/showthread.php?t=1181092&highlight=hard+drive+-recognized](http://ubuntuforums.org/showthread.php?t=1181092&highlight=hard+drive+-recognized)

Output of sudo lshw (the part I found important):
I really hope I know how to wrap the text properly. Any other would be embarrasing.
```
 *-ide:1
             description: IDE interface
             product: 182 SATA/RAID Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_sis latency=64 module=sata_sis
           *-disk
                description: ATA Disk
                product: ST3160023AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.00
                serial: 5MT2KX2S
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0001c4ee
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/D
                   version: 3.1
                   serial: eec20b5c-cd35-c746-868e-5796353d3791
                   size: 97GiB
                   capacity: 97GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-06-14 18:26:00 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: bfa90e70-95d2-4c14-96b3-c2762d02ee6b
                   size: 972MiB
                   capacity: 972MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: dc81e8dc-f486-43f1-8788-007ec6c4cba2
                   size: 6675MiB
                   capacity: 6675MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-08-30 17:26:05 filesystem=ext3 modified=2009-07-20 14:18:32 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-07-20 14:18:32 state=mounted
              *-volume:3
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /home
                   version: 1.0
                   serial: 0e96082a-2bfa-43cf-84d3-fb0f57d4cbfc
                   size: 43GiB
                   capacity: 43GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-08-28 02:01:01 filesystem=ext3 modified=2009-07-20 14:18:33 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered mounted=2009-07-20 14:18:33 state=mounted
```The output of sudo fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c4ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       12872      996030   82  Linux swap / Solaris
/dev/sda3           12873       13723     6835657+  83  Linux
/dev/sda4           13724       19457    46058355   83  Linux
kristo@nurkka:~$ 
```* Both hard drives show in BIOS as third master and slave.
*Gparted shows no trace of the storage drive.
*"I have PCI S-ATA Controller" in BIOS set to "Native" as it could also be "RAID"(if my memory serves me right, it was RAID)
*I am able to access the Windows -partition from Ubuntu without any problems.
*Oh, and Windows hinted that the storage drive is location 1 as the install-drive is location 0.

I hope I did not miss anything important. As I said, I have overdone my talents in this one, I would be very glad to receive any tips or tricks about where to look for the problem or, if possible, even solution.

Regards,
Kristo

---

### Post by Azyl on 2009-07-20
from what i am seeing you shouldn`t have troubles with it, if i rember well there was a special program or component for ubuntu that alowed the mounting of ntfs partions and you should check that your fstab config is ok (usualy there is the problem) and that the hard drive is listed there so it can be mounted and used by ubuntu sorry for my english

---

### Post by Kristo, act 1 on 2009-07-20
Hey Azyl,

I appreciate your lightning-fast response.

I checked the fstab file as you kindly suggested, but I cannot tell if and how I should modify that file, should the problem be in it. It doesn't show the second hard drive. I'll post it in its great eight rows, just in case.

/etc/fstab: (sda is the installation drive. I do not know what the missing one would be called.)
```

proc /proc proc defaults 0 0
UUID=dc81e8dc-f486-43f1-8788-007ec6c4cba2 / ext3 relatime,errors=remount-ro 0 1
UUID=0e96082a-2bfa-43cf-84d3-fb0f57d4cbfc /home ext3 relatime 0 2
UUID=bfa90e70-95d2-4c14-96b3-c2762d02ee6b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/D ntfs defaults 0 0
```Thank you for the tip, I appreciate it. :)

Kristo

---

### Post by ajgreeny on 2009-07-20
I'm pretty sure this is nothing to do with your fstab or any filesystem files on your machine but more likely a kernel problem.  From the first of the links you gave I wonder if the boot parameter ```
pci=nomsi
```added to the grub menu list kernel line might help.

Try the following, it will not make permanent changes at the moment to your system so don't worry.  Reboot and at the grub menu hit "e" on the ubuntu line, then with your cursor keys go down to the second line starting "kernel" and ending in "quiet splash" and add "pci=nomsi" to the end.  Now hit enter to accept the edit then "b" to boot and see if the disk is now recognised when you have booted in to the system.  If ity does not work, don't worry, just boot again and the edit you made will have gone and you'll be back where you were.

Are you sure you have the second disk properly attached in your machine, because as you said, it is not being seen at all by ubuntu, you only have sda showing in fdisk and lshw commands.  Can you check the jumpers on the side of the disks are correctly set to master and slave, assuming they are both IDE disks, though I don't think that would stop it being seen totally by ubuntu.

---

### Post by Kristo, act 1 on 2009-07-20
Ajgreeny,

Thank you for your most educated advice.

I hope I did the first advice properly, as I just added pci=nomsi right after the last word in the line as in "kernel .... quiet splash pci=nomsi". Unfortunately, it did not take me much further. Still nothing on gparted or fdisk -l.

About the cable settings. I tried to look into the box, but didn't find anything hinting for master/slave. So, I googled "st3160023AS manual". The first result said in it: 
"There is no master/slave relationship
with Serial ATA devices like there is with parallel ATA. If two drives are
attached on one Serial ATA host adapter, the host operating system views
the two devices as if they were both “masters” on two separate ports.
"
News for me, but I can't see any switch on the disks, and the cables only fit one socket on each drive. Does all this sound sensible?

Thank you for your input.

Kristo

---

### Post by ajgreeny on 2009-07-20
OK, if the disks are attached by narrow cables they are sata drives and will not need the master/slave arrangement.  That would be needed only if they are connected by ribbon cables about 2cm wide, so it sounds as if you have sata drives, which leaves me even more confused and baffled, I'm afraid, and not knowing quite where else to turn.  Sorry about that.

---

### Post by Kristo, act 1 on 2009-07-21
Hey,

Yes, the cables were narrow ones. I find it strange, though, that BIOS lists them as master and slave even though the manual says they both act as master. Can't imagine it affecting, but it just occurred to me.

Thank you for your help. Even though the answer hasn't come up, we're still a few tries further. After all, there is a limited amount of false solutions :o.

It bothers me that a year or two backwards I did have that hard disk visible on Ubuntu. Might have been a different version of Ubuntu, though.
Then some day it just wasn't there. Cannot recall if anything happened back then. There were several users on the computer... Think my brother stuck a jellyfish in there.

There is one you might be able to answer for me, Ajgreeny, if you please.

If and when Ubuntu recognizes the disk physically is there, will it automatically show up both in fdisk -l and gparted? So there wouldn't be the chance I just miss it?

Kristo

---

### Post by ajgreeny on 2009-07-21
Yes, I'm pretty certain it will. As to why it's not at the moment, I'm afraid I'll have to admit defeat.
However, just a thought:  what happens if you change over the cable mounts of the disks, ie swap them round the other way?  Perhaps either both disks will become available, or just the second one will now be seen.  This would suggest that the cable or connector is not working properly, though the fact that windows sees both suggests something else is the problem.

As you can see, I'm grasping at straws now, but always, always, hopeful.

---

### Post by Kristo, act 1 on 2009-07-22
Hey,

I tried switching the cables. Considered it earlier but I thought maybe it will mess up something. Turns out it seems to have had no influence whatsoever to either Ubuntu or Windows. Tried the pci=nomsi trick with it, too. Hmm.

Maybe if we chat long enough, try after try, either someone wiser sees the post or we hit the target :) I kind of think the first one is more efficient a way, though.

Anyone up for a try? Any input would be great, even if it's just to bump up the post :-#.

Thanks
Kristo

---

### Post by vanadium on 2009-07-22
Just some other ideas for debugging: how does it work from within a live session? Try an Ubuntu 9.04 live Cd or another distro. This way you could see if the problem is limited to Ubuntu 8.10.

---

### Post by Kristo, act 1 on 2009-07-22
Hey,

Thanks for the note, hadn't thought about it that way. I'll try it tonight if I can get a friend to bring a live cd to me.

I pay for the slowest possible internet connection, and I don't even get what I pay for, so no use trying to create one :D

If you have any other clues, I'd be happy to try and even fail.

Kristo

---

### Post by Kristo, act 1 on 2009-07-22
Hey,

Just an update to report the result of the suggestion Vanadium made.

I tried both Ubuntu 7.04 and Ubuntu 8.04 on live CDs. With them, the second hard drive is clearly VISIBLE as expected.

So, thank you, Vanadium.

Sure as hell bothers me that it's a problem with the operating system, (so that I have to compromise) but maybe I'll just give in and install a new one. Who knows, maybe 9.04 works. Haven't got my hands on that one yet.

Reinstalling Ubuntu is not such a massive job after all anyway. As everything important is saved on the second hard drive, I'll just let it go untouched.

Yea, so, solved, in a way.. If you experience the same problem... Change the version.

Thank you for everyone for your kind input.

Kristo

---

### Post by Kristo, act 1 on 2009-07-28
Hey,

Updating to note that the problem is limited to ***versions 8.10 and 9.04***..
I'm now running 8.04, which is not cool, but there doesn't seem to be another way around.

Kristo

---

### Post by beacon on 2009-08-14
I'm not certain this is the same problem, but if not, it is close. I have two hard drives, but only the first ever appears when booting. I have used fdisk -l and got the following:



Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d9d9d9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19272   154802308+  83  Linux
/dev/sda2           19273       19457     1486012+   5  Extended
/dev/sda5           19273       19457     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77777777

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1019     8185086   83  Linux
/dev/sdb2            1020       19457   148103235    5  Extended
/dev/sdb5            1020        1528     4088511   82  Linux swap / Solaris
/dev/sdb6            1529        1594      524288   83  Linux
/dev/sdb7   *        1594        1619      204799+  83  Linux
/dev/sdb8            1619       19457   143285572   8e  Linux LVM

That clearly shows two hard drives, but there seems no way I can get access to the second. The bios show the boot sequence: CD/Rom as first, removable hard drive second, and hard drive third. 

Even the chap who built the machine is unable to help. I would appreciate any advice. By the way, I have PClos on the second and Ubuntu Jaunty on the first.

---

