---
title: "Script to find USB based on PARTUUID"
date: 2017-10-24
forum: Hardware
---

### Post by bosscheesemo on 2017-10-24
I have a USB thumb drive with PARTUUID="ecb0d130-01" (found by blkid).

I need a simple script that can detect the thumb drive's partuuid and then do something based on whether or not the device is detected. Is that possible?

I know that it's possible to use this script to find a USB based on the name of the drive:

<
#!/bin/bash

if sudo lshw | grep "label=USBNAME" ; then
  echo "Flash Drive Available"
else
  echo "Flash Drive NOT Available"
fi
>

but a drive's name can change. I'd prefer to base the if condition on something static to the device, if possible.

Thank you!

---

### Post by TheFu on 2017-10-24
I use the LABEL for the flash partition to determine where to mount my flash drives to specific locations for each. Perhaps if you say what the purpose of the script is, then someone will provide a better/more complete answer?

---

### Post by oldfred on 2017-10-24
The partUUID is only with gpt partitioned drives as it really is the GUID.

       lsblk -f -o +PARTUUID /dev/sda 
```
fred@Z170N:~$ lsblk -f -o +PARTUUID /dev/sda
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT PARTUUID
sda                                                                 
&#9500;&#9472;sda1 vfat   ESP   D966-440A                            /boot/efi  c371fe4e-a6db-4c46-b056-a4eea609f81d
&#9500;&#9472;sda2 ext4         5c1e1a3f-261f-4da5-a0c2-8f479b3039de /          81e01570-23ce-4eed-ab28-35d40ff1ea7c
&#9500;&#9472;sda3 ext4   ISO   ab916e15-8a74-4d6e-a0b1-32718a505dc7            a4277e02-fcf0-43e7-a037-8a3687ca9f8b
&#9492;&#9472;sda4 ext4   root2 85a3d0a5-d4f8-473e-b89c-24c2cba6631a            b993b0cb-f41c-4152-9701-ae8133f5e6d6

```
sudo blkid
```
fred@Z170N:~$ sudo blkid
/dev/sdb7: UUID="3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd" TYPE="swap" PARTUUID="d7090376-3479-46ef-a3ee-dba7c351d607"
/dev/sda1: LABEL="ESP" UUID="D966-440A" TYPE="vfat" PARTLABEL="ESP" PARTUUID="c371fe4e-a6db-4c46-b056-a4eea609f81d"
/dev/sda2: UUID="5c1e1a3f-261f-4da5-a0c2-8f479b3039de" TYPE="ext4" PARTLABEL="System" PARTUUID="81e01570-23ce-4eed-ab28-35d40ff1ea7c"
/dev/sda3: LABEL="ISO" UUID="ab916e15-8a74-4d6e-a0b1-32718a505dc7" TYPE="ext4" PARTLABEL="ISO" PARTUUID="a4277e02-fcf0-43e7-a037-8a3687ca9f8b"

```

---

### Post by TheFu on 2017-10-24
The solution would also depend on the releases the OP is trying to support, since on my 14.04 servers, there isn't anything like 
```
$ lsblk -f -o +PARTUUID /dev/vda
lsblk: unknown column: +PARTUUID

``` that's a virtual machine.  A physical box: 
```
$ lsblk -f -o +PARTUUID /dev/sda
lsblk: unknown column: +PARTUUID

```

Which is why I asked about the purpose and mentioned LABELs.   Looking in /dev/disk/, we can see 
```
$ ls /dev/disk/
by-id/  by-label/  by-uuid/
```
Which hold the mapping from these different identifiers back to the correct /dev/sdXY as needed.

On my system, the interesting parts are:
```

$ find . -ls
  7209    0 drwxr-xr-x   5 root     root          100 Oct 18 09:12 .
  7537    0 drwxr-xr-x   2 root     root           80 Oct 18 09:12 ./by-uuid
  7548    0 lrwxrwxrwx   1 root     root           10 Oct 18 09:12 ./by-uuid/89bce4c4-5949-40ff-9e61-c1d6b3d8d7ce -> ../../vda2
  7538    0 lrwxrwxrwx   1 root     root           10 Oct 18 09:12 ./by-uuid/df8b97db-e432-4417-a088-7e4309e37d92 -> ../../vda1
  7533    0 drwxr-xr-x   2 root     root           80 Oct 18 09:12 ./by-label
  7545    0 lrwxrwxrwx   1 root     root           10 Oct 18 09:12 ./by-label/swap -> ../../vda2
  7534    0 lrwxrwxrwx   1 root     root           10 Oct 18 09:12 ./by-label/root -> ../../vda1
  7210    0 drwxr-xr-x   2 root     root           60 Oct 18 09:12 ./by-id
  7211    0 lrwxrwxrwx   1 root     root            9 Oct 18 09:12 ./by-id/ata-QEMU_DVD-ROM_QM00003 -> ../../sr0

```

No LVM in that virtual install.  LVM would require **not** assuming /dev/sd* in the scripting.
I would post an LVM example, but there are 90 different identifiers for that situation, as the machine as a bunch of disks connected. ;)   On another system using LVM with just 1 disk, there are 40 identifiers, though the disk tree is fairly simple:
```
$ lsblk
NAME                             MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                                8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1                             8:1    0   100M  0 part 
&#9500;&#9472;sda2                             8:2    0    60G  0 part 
&#9500;&#9472;sda3                             8:3    0  58.6G  0 part 
&#9500;&#9472;sda4                             8:4    0     1K  0 part 
&#9500;&#9472;sda5                             8:5    0  19.9G  0 part /
&#9500;&#9472;sda6                             8:6    0   6.4G  0 part [SWAP]
&#9492;&#9472;sda7                             8:7    0 786.6G  0 part 
  &#9500;&#9472;vg--hadar-lv--hadar (dm-0)   252:0    0 393.5G  0 lvm  /var
  &#9492;&#9472;vg--hadar-lv--backups (dm-1) 252:1    0   393G  0 lvm  /Backups
sr0                               11:0    1  1024M  0 rom  

```

If looking for a mounted flash drive is the goal, then the OP needs to know that gvfs doesn't tell the OS about mounts in the same way every other method does.  It caused enough problems here that we purge gvfs from all our systems, and have an automatic script that keeps it off daily.  If they only worked with the mtab like all other mount tools do, we probably wuoldn't have any issues with it.

As for checking whether any storage is mounted, we just look for a previously placed file in a specific location on the storage.  If it exists, [ -f $file ], then we know the storage is mounted, otherwise, it isn't.  This won't work for random storage devices, but the OP knows something about the device (guid?) - so that implies something more could easily be known too.  We use the [ -f $file ] check to ensure our backup storage is mounted.  We didn't always and bad things happen when a disk gets full on Unix-like systems.  What's worse was that a new admin just manually mounted the backup storage - effectively hiding all those files that filled it in the first place. Took a few hours to figure out that we had to umount the backup storage to gain access to all the files eating the storage that prevented any real disk clean up from being possible.

Or I could be missing the entire point of the OP question. That is just as likely. ;)

---

### Post by oldfred on 2017-10-24
I just posted the info on PartUUID to show it is available.
But that is only with gpt and newer tools with 16.04 or later.
Most users still use MBR(msdos) partitioning with flash drives, so no PartUUID anyway as that is the GUID with gpt partitioning.

Or TheFu's suggestion of labels makes the most sense as that should work whether flash drive is gpt or MBR. 
Note with gpt there are two labels. One is gpt's filesystem (partlabel) and other is format's partitions(label). I have mixed those up, particularly using Data and data.

---

### Post by TheFu on 2017-10-24
And I've been burned by a LABEL on a flash drive that disappeared - ok, I was forced to reformat the partition, which cleared the LABEL.  Because I forgot to add it back later, any scripts dependent on it failed.  The same would happen if blkid was used - formatting might change this info.   Humans deal with labels better than funky hex sequences.

---

### Post by bosscheesemo on 2017-10-25
Well the general idea that i've been experimenting with recently is ways of automatically pulling files from a USB drive. I'm going back to school and I'm looking to save myself some time by writing a script that can detect a USB thumb drive and, upon detecting the drive, offloading its contents (assignments, notes, projects) to my computer and from there storing a copy to my NAS.

The thing I don't like about automatically pulling files from a USB drive is that it's an enormous security risk. If someone copied my USB's drive name then they could place whatever they like on my computer. I'm hoping that a USB can be detected by something unique and static to the USB drive itself so that my automatic file movemements would have a sort of IFF protection: only certain USB devices flagged by information on the drive can be used.

Or at least that's the idea.

---

### Post by TheFu on 2017-10-25
The "automatic" part on insertion is the hardest part since system accepted the udev project.  I don't know how to make that work anymore, but if you are willing to manually run a script - perhaps for --> then for <-- later, it would be really easy.

Some pseudo-code ....

# If the "special file" exists on the flash drive, then

# use rsync to pull the files to my NAS.

The real issue is that flash drives usually have FAT32 or xfat file systems which don't maintain file ownership and permissions, so those need to be addressed.  For less than 500MB of data, tar is an option.  You could automate creating the gtar file and pulling them off.  tar maintains ownership/groups and simple permissions.

Also, rsync likes to work on file timestamps and diffs, so if you are plugging this into different boxes all the time, who knows what time or even which date the files might get?

Plus, flash drives are a very common way to spread malware, even on Linux.

Of course, if you aren't using untrusted computers, then most of those concerns just don't matter.  If there is a Windows machine, then the ownership and permissions will be lost.

Interesting problem.  I used to do something similar with a 250MB tape drive - took work home and back using it.  

These days, I use nextcloud over a VPN.  Anywhere I have network connectivity (almost), I have access to my files.  For a long time, I just uses ssh and rsync and sftp to grab files are needed.

But ... **rsync** is THE tool for this sort of stuff.

---

### Post by efflandt on 2017-10-26
I don't know if PARTUUID is something that does not show before 16.04, but it shows on my system, and I do not even have any gpt partitions on my PC from 2010. The one I ls in this case is a USB memory stick:```
~$ sudo blkid
/dev/sda1: UUID="EED2-7775" TYPE="vfat" PARTUUID="2fb1db22-01"
/dev/sda2: LABEL="RECOVERY" UUID="E6CAD622CAD5EF35" TYPE="ntfs" PARTUUID="2fb1db22-02"
/dev/sda3: LABEL="OS" UUID="6440DA0C40D9E538" TYPE="ntfs" PARTUUID="2fb1db22-03"
/dev/sda4: UUID="b226357c-b349-498a-8bba-1ea7bed78d43" TYPE="ext4" PTTYPE="dos" PARTUUID="2fb1db22-04"
/dev/sdb1: UUID="6787eaaf-0994-4467-897b-538f5c624731" TYPE="ext4" PARTUUID="7e78a7d3-01"
/dev/sdg1: LABEL="USB20FD" UUID="161E-CC6E" TYPE="vfat" PARTUUID="16c941b2-01"

~$ ls -l /dev/disk/by-partuuid/16c941b2-01
lrwxrwxrwx 1 root root 10 Oct 26 17:55 /dev/disk/by-partuuid/16c941b2-01 -> ../../sdg1

~$ grep sdg1 /etc/mtab
/dev/sdg1 /media/efflandt/USB20FD vfat rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro 0 0
```Otherwise couldn't you look it up by UUID:```
~$ ls -l /dev/disk/by-uuid/161E-CC6E
lrwxrwxrwx 1 root root 10 Oct 26 17:55 /dev/disk/by-uuid/161E-CC6E -> ../../sdg1
```

---

