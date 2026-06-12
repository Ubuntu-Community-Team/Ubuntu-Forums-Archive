---
title: "USB drive - home partition - copy"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by pashby on 2006-03-18
Hello All

I have managed to get into a deep hole.

When I installed Breezy I did an 'expert' - not me in any way - install and made three partitions - root, home and swap. This has served me well because I have been able to do multiple installs of operating systems without losing my home partition.
I wanted to try Dapper and tried an update install but this blew my installation away. I reinstalled Breezy and all was well again.

I had another 40 GIG drive so I decided to do a clean 'expert' install of Dapper with the same three partitions of root, home and swap on the new drive. Not suprisingly this went without a hitch. Now I would like to get my home data back from the old Breezy installation.

I'm afraid this is where my limited Linux abilities run out. I have put the Breezy insalation in a USB drive and connected to the Dapper. The root folder reads fine but I can't get to the home partition on the USB drive.

fdisk -l gives
/dev/sda1 
/dev/sda2
/dev/sda5

sda2 I assume is my home partition and it appears as 'exended'.

How can I 'mount' this partition and read from it so that I can copy my data?

Regards

Peter

---

### Post by tuxcantfly on 2006-03-19
check your /etc/fstab file by typing:

sudo gedit /etc/fstab

and see if there is a the line that says /home/yourname
if there is none, add these lines:

/dev/sda1   /home/yourname   ext3   defaults   0   0

each of the values should be separated by a tab
if this doesn't work, try replacing the value ext3 with ext2

reboot and see what happens

---

### Post by tuxcantfly on 2006-03-19
that's for mounting on bootup
if you just want to mount it here and now, type:

sudo mount /dev/sda2 /home/yourname

---

### Post by pashby on 2006-03-19
Thanks for the help

I try

sudo mount /dev/sda2 /home/peter

It seems that it is OK except that the command wants me to specify a filesystem type.

I then try
sudo mount /dev/sda2 /home/peter ext3
and it give a whole lot of data - and the help page for mount 

Any Suggestions

Peter

---

### Post by pashby on 2006-03-19
Hello again

Here is something interesting.

I replaced th Breezy disk and put the Dapper disk into the USB caddy.

Breezy found the USB home partition on the Dapper disk automatically - no mounting etc.

Then I copied from Breezy to the Dapper disk - no problems and now I have my home data back again on Dapper.

Is this a problem with Dapper or nothing to worry about?

Peter

---

### Post by tuxcantfly on 2006-03-19
if you need to specify the filesystem type, type:

sudo mount -t ext3 /dev/sda2 /home/peter

---

### Post by pashby on 2006-03-20
Thanks tuxcantfly

I tied sudo mount -t ext3 /dev/sda2 /home/peter

and it gives this error

peter@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /home/peter
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This is what is seen with fdisk -l
peter@ubuntu:~$ fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        4864    38821072+   5  Extended
/dev/sda5              32        4864    38821041   8e  Linux LVM

I have no problems with Breezy mounting /home/peter on Dapper but not the other way.

Peter

---

