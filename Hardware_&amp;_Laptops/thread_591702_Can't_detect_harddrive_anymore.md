---
title: "Can't detect harddrive anymore"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by jcmachad on 2007-10-25
Yesterday I was trying to figure out how to read-write to my Simpletech external harddrive.  IT is currently formated as NTFS.  I was trying to install the NTFS configuration tool last night, and I am not sure what happened, but now kubuntu does not even recognize the HD.  it used to appear on the desktop when I turned it on, but now it doesn't.

So my questions are :

How do I get kubuntu to recognize this, (I have checked my home folder, and all that stuff)
and

how can i read/write this NTFS partition?

*edit* i think i figured this part out. ntfs-config right?

Thanks

---

### Post by jcmachad on 2007-10-26
you can delete this, problem solved.

---

### Post by juanphd on 2007-10-26
Hi, I'm new in Ubuntu and I have the same problem, I plug a SimpleTech 160 Gb USB harddrive and Ubuntu doesn't recognize it. This drive takes the energy from the USB port. I'd appreciate any help.
Thank you

---

### Post by Road Mark Borromeo on 2007-10-27
i have a similar problem. I installed Ubuntu 7.10 yesterday on my 2nd hard drive. The installation was fine but tried installing it again to use the boot loader of my Vista. I repair my MBR using the Vista DVD but I had a hard time figuring it out using Easy BCD. After 2 installations, it screwed my Hard Drive. I recoverd one partition and formatted the remaining space. And know, the liveCD can't detect my second hard drive. Please help

I searched some forums and used 

sudo fdisk -l on the terminal window

i don't even know what this command is but this is the result.

===========================================
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3bac3bab

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/hda2            6375       19456   105081165    f  W95 Ext'd (LBA)
/dev/hda5            6375       10198    30716248+   7  HPFS/NTFS
/dev/hda6           10199       19456    74364853+   7  HPFS/NTFS

Unable to seek on /dev/hdb
============================================

Please help. This is the first time i'll be using linux

---

### Post by juanphd on 2007-11-11
Hi, I solved my problem. It seems that the external hard drive needs certain amount of energy from the USB port; I was connecting the drive to the front USB ports of my PC and it didn't work and then I tried plugging the drive to the USB ports on the back, those that are directly attached to the motherboard and it worked.

---

### Post by Giradman on 2007-11-11
> **juanphd said:**
> Hi, I solved my problem. It seems that the external hard drive needs certain amount of energy from the USB port; I was connecting the drive to the front USB ports of my PC and it didn't work and then I tried plugging the drive to the USB ports on the back, those that are directly attached to the motherboard and it worked.

**Juanphd** - thanks for the explanation of your problem and the solution - always a courteous gesture to others to post an answer to a problem you have solved since many may be struggling w/ the same issue(s) - :-D

---

### Post by avai on 2008-01-31
I'm using the simpletech 160GB as well.

I've had it plugged into the back port of my laptop for a while now and I'm still not getting any indication that my computer is acknowledging it aside from when I inputted the following command line into terminal: **sudo fdisk -l** , where I get the following output.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks             Id    System
/dev/sda1   *           1           9566    76838863+   83   Linux
/dev/sda2            9567        9729     1309297+    5     Extended
/dev/sda5            9567        9729     1309266       82   Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Any suggestions?

---

### Post by avai on 2008-01-31
After googling, I found a page that in summary provided the following for me.


mkfs -t ext3 /dev/sdb

afterwards the following command worked.
fdisk /dev/sdb
and I entered for commands
n
p
1 
19475
w

now I get the following when I input **sudo fdisk -l**:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9566    76838863+  83  Linux
/dev/sda2            9567        9729     1309297+   5  Extended
/dev/sda5            9567        9729     1309266   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux


So now that I'm here, there is still no indication the new drive is available.

---

### Post by Yellow Pasque on 2008-01-31
I assume you didn't have any previous data on there before you did mkfs (if you did, it's gone). Anyway...

You need to mount it now. You can do this at startup with an entry in your /etc/fstab file. First, you'll need a directory to mount it in. If you don't already have an empty directory in mind, then
```
cd /media; sudo mkdir <whatever you want to call it, omit brackets>
```
Then:
```
sudo gedit /etc/fstab
```
Add this:
```
/dev/sdb1 <dir you want to mount to, omit brackets> ext3  rw,auto,exec,user,uid=1000  0  0
```
Save. Reboot.

---

### Post by avai on 2008-02-04
Alrighty, here's an update. 

I followed the instructions but no indication of the drives was seen in all but one of my boots (one of the most recent). However, since then the icons haven't reappeared. I clicked on the icon and I received the following message:

> 
Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

More Details:
mount: wrong fs type, bad option, bad superblock on /dev/sdb,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so

I input **dmesg | tail** and received the following output:

> [ 5222.968000] sdb: Mode Sense: 21 00 00 00
[ 5222.968000] sdb: assuming drive cache: write through
[ 5222.968000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[ 5222.968000] sdb: Write Protect is off
[ 5222.968000] sdb: Mode Sense: 21 00 00 00
[ 5222.968000] sdb: assuming drive cache: write through
[ 5222.968000]  sdb: sdb1
[ 5223.592000] sd 3:0:0:0: Attached scsi disk sdb
[ 5223.592000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[ 5230.236000] EXT3-fs: Unrecognized mount option "uid=1000" or missing value


Any suggestions?

---

### Post by Yellow Pasque on 2008-02-04
> [ 5230.236000] EXT3-fs: Unrecognized mount option "uid=1000" or missing value
Oops, I guess that option doesn't work for ext3 filesyststems. My apologies. Try removing that from the /etc/fstab line I gave you. Does it now behave the way you want?

---

### Post by avai on 2008-02-05
I figured out two problems, but still haven't resolved the issue yet. 1) The icon indicating an external drive only appears when I boot the computer without the drive plugged in. 2) I entered a note in fstab in the line above the given code (with # in front as mentioned by **man fstab**). Since then, I removed the message and now get the following output from **dmesg | tail**:

> [   94.252000] sdb: Write Protect is off
[   94.252000] sdb: Mode Sense: 21 00 00 00
[   94.252000] sdb: assuming drive cache: write through
[   94.256000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[   94.256000] sdb: Write Protect is off
[   94.256000] sdb: Mode Sense: 21 00 00 00
[   94.256000] sdb: assuming drive cache: write through
[   94.256000]  sdb: sdb1
[   94.880000] sd 2:0:0:0: Attached scsi disk sdb
[   94.880000] sd 2:0:0:0: Attached scsi generic sg1 type 0

The error at the end of this output doesn't appear anymore, a very good thing. However, I still get the following message when I click on the external drive icon:

> Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

Show More Details
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       in some cases useful info is found in syslog - try
       dmesg | tail  or so


My revision to this post comes because I just noticed a page two (and subsequently, your response to my previous one).

---

