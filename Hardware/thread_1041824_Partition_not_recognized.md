---
title: "Partition not recognized"
date: 2009-01-17
forum: Hardware
---

### Post by arnov007 on 2009-01-17
Dear Friends,

I have just installed Ubuntu Linux 8.10 Desktop Edition in my COMPAQ V6307TU Notebook. I have installed it along with Windows XP SP2, with Windows having 3 partition and Linux installed on the 4th Partiton with approx 10GB allocated to it in EXT3 format. I have also made a swap partition of 97MB. The problem is that our of three sda6 (i.e. the third partition, Linux is not able to mount(open) and it's giving me an error message: "mount: wrong fs type, bad option, bad superblock on / dev/sda6, missing codepage or helper program, or other error    In some cases useful info is found in syslog - try  dmesg | tail or so"

followed by Error message: Heading: Unable to mount 19.4GB Media 
Message: "DBus eeror.org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the reply timeout expired, or the network connection was broken."

I just want to say that Network and WiFi connection is fantastic but i don't know why it's not recognizing..

Please Help Me......

---

### Post by Rohan Kapoor on 2009-01-17
> **arnov007 said:**
> Dear Friends,

I have just installed Ubuntu Linux 8.10 Desktop Edition in my COMPAQ V6307TU Notebook. I have installed it along with Windows XP SP2, with Windows having 3 partition and Linux installed on the 4th Partiton with approx 10GB allocated to it in EXT3 format. I have also made a swap partition of 97MB. The problem is that our of three sda6 (i.e. the third partition, Linux is not able to mount(open) and it's giving me an error message: "mount: wrong fs type, bad option, bad superblock on / dev/sda6, missing codepage or helper program, or other error    In some cases useful info is found in syslog - try  dmesg | tail or so"

followed by Error message: Heading: Unable to mount 19.4GB Media 
Message: "DBus eeror.org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the reply timeout expired, or the network connection was broken."

I just want to say that Network and WiFi connection is fantastic but i don't know why it's not recognizing..

Please Help Me......
What is the partition type that you are trying to mount?

---

### Post by arnov007 on 2009-01-17
All the 3 partitions are on NTFS Format having a cluster size of 4K. C Drive is a Primary Drive and rest 2 are logical...

---

### Post by chronographer on 2009-01-17
you can type "dmesg | tail" at the command prompt, which will tell you what is going on (hopefully) but I reckon there is something wrong in your fstab. Try typing "sudo mount /dev/sda[X] /mnt/tmp" (you may have to create /mnt/tmp by "sudo mkdir /mnt/tmp") where the [X] is replaced by the number representing the partition you want to mount (having errors with).

If this works, then it is most likely fstab related, and you should post it here. (/etc/fstab) ...(its a text file)

p.s. the error above says its /dev/sda6 ... so try that first

---

### Post by arnov007 on 2009-01-17
It's showing me the following message:

arnov@PRN07020741014:~$ demsg | tail
bash: demsg: command not found
arnov@PRN07020741014:~$ dmesg | tail
[  135.762988] type=1503 audit(1232166839.085:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5764 profile="/usr/sbin/cupsd"
[  135.762995] type=1503 audit(1232166839.085:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5764 profile="/usr/sbin/cupsd"
[  135.763002] type=1503 audit(1232166839.085:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5764 profile="/usr/sbin/cupsd"
[  135.763067] type=1503 audit(1232166839.085:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5764/net/dev" pid=5764 profile="/usr/sbin/cupsd"
[  302.378997] EXT3-fs error (device sda6): ext3_check_descriptors: Block bitmap for group 128 not in group (block 4278255615)!
[  302.381506] EXT3-fs: group descriptors corrupted!
[ 1212.929170] EXT3-fs error (device sda6): ext3_check_descriptors: Block bitmap for group 128 not in group (block 4278255615)!
[ 1212.931384] EXT3-fs: group descriptors corrupted!
[ 1766.411849] EXT3-fs error (device sda6): ext3_check_descriptors: Block bitmap for group 128 not in group (block 4278255615)!
[ 1766.414067] EXT3-fs: group descriptors corrupted!
arnov@PRN07020741014:~$ sudo mount/dev/sda6/mnt/tmp
[sudo] password for arnov: 
sudo: mount/dev/sda6/mnt/tmp: command not found
arnov@PRN07020741014:~$ sudo mkdir/mnt/tmp
sudo: mkdir/mnt/tmp: command not found
arnov@PRN07020741014:~$ sudo mkdir /mnt/tmp
arnov@PRN07020741014:~$ sudo mount /dev/sda6/mnt/tmp
mount: can't find /dev/sda6/mnt/tmp in /etc/fstab or /etc/mtab

---

### Post by Rohan Kapoor on 2009-01-17
you need a space between /dev/sda6 and /mount/tmp

so the proper command;

```
sudo mount /dev/sda6 /mnt/tmp
```

---

### Post by chronographer on 2009-01-17
> **arnov007 said:**
> It's showing me the following message:

arnov@PRN07020741014:~$ demsg | tail
bash: demsg: command not found
arnov@PRN07020741014:~$ dmesg | tail
[  135.762988] type=1503 audit(1232166839.085:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5764 profile="/usr/sbin/cupsd"
[  135.762995] type=1503 audit(1232166839.085:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5764 profile="/usr/sbin/cupsd"
[  135.763002] type=1503 audit(1232166839.085:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5764 profile="/usr/sbin/cupsd"
[  135.763067] type=1503 audit(1232166839.085:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5764/net/dev" pid=5764 profile="/usr/sbin/cupsd"
[  302.378997] EXT3-fs error (device sda6): ext3_check_descriptors: Block bitmap for group 128 not in group (block 4278255615)!
[  302.381506] EXT3-fs: group descriptors corrupted!
[ 1212.929170] EXT3-fs error (device sda6): ext3_check_descriptors: Block bitmap for group 128 not in group (block 4278255615)!
[ 1212.931384] EXT3-fs: group descriptors corrupted!
[ 1766.411849] EXT3-fs error (device sda6): ext3_check_descriptors: Block bitmap for group 128 not in group (block 4278255615)!
[ 1766.414067] EXT3-fs: group descriptors corrupted!
arnov@PRN07020741014:~$ sudo mount/dev/sda6/mnt/tmp
[sudo] password for arnov: 
sudo: mount/dev/sda6/mnt/tmp: command not found
arnov@PRN07020741014:~$ sudo mkdir/mnt/tmp
sudo: mkdir/mnt/tmp: command not found
arnov@PRN07020741014:~$ sudo mkdir /mnt/tmp
arnov@PRN07020741014:~$ sudo mount /dev/sda6/mnt/tmp
mount: can't find /dev/sda6/mnt/tmp in /etc/fstab or /etc/mtab

you need some spaces in there champ! try this (copy and paste):
```

sudo mkdir /mnt/tmp
sudo mount /dev/sda6 /mnt/tmp

```

and I reckon that you are trying to mount the partition as ext3 when it should be ntfs. paste your /etc/fstab in here.

---

### Post by Rohan Kapoor on 2009-01-17
> **chronographer said:**
> you need some spaces in there champ! try this (copy and paste):
```

sudo mkdir /mnt/tmp
sudo mount /dev/sda6 /mnt/tmp

```

and I reckon that you are trying to mount the partition as ext3 when it should be ntfs. paste your /etc/fstab in here.
Didn't I just say that?

---

### Post by arnov007 on 2009-01-17
I just got this message after I typed your suggested command:

arnov@PRN07020741014:~$ sudo mount /dev/sda6 /mnt/tmp
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What should I now do...

---

### Post by vanadium on 2009-01-17
/dev/sda6 might as well be your swap partition. Use the command "sudo blkid" to have a listing of all partitions your system knows about, along with theyr "type". Chances are you will discover sda6 is not a partition you should attempt to mount.

---

### Post by arnov007 on 2009-01-17
I tried using the above mentioned command, I got this message:

arnov@PRN07020741014:~$ sudo blkid
/dev/sda1: UUID="86386D2E386D1E85" LABEL="PRIMARY" TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="54903e60-b20b-4e07-b910-890d4ccbc4e7" 
/dev/sda4: UUID="f61de2ff-3c95-45f6-b73b-9667b731502d" TYPE="ext3" 
/dev/sda5: UUID="4C24753A2475285A" LABEL="MOVIES" TYPE="ntfs" 
/dev/sda6: UUID="149EFFB189205C99" LABEL="MUSIC" TYPE="ntfs"

---

### Post by vanadium on 2009-01-17
Your /dev/sda6 indeed is reported as an ntfs drive. However, your manual mount attempt reveals that the mount command does not automatically recognize a file system.

First of all, can you (still) see that partition from Windows? Try first of all checking and repairing the partition from within Windows.

---

### Post by caljohnsmith on 2009-01-17
You might be able to recover the NTFS sda6 partition using testdisk to repair its boot sector. To try that, how first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the sda6 NTFS partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, then try again:
```
sudo mount /dev/sda6 /mnt
```
And please post the output, or let me know if you run into problems.

---

