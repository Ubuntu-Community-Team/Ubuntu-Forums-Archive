---
title: "How to mount a FAT32 partition under LiveCD"
date: 2008-08-23
forum: General Help
---

### Post by ryanraphael on 2008-08-23
Dear all, 
  I had been looking for a way to access my files on my hard drives if Windows was corrupted(can not boot).I came up with the decision using Ubuntu Live CD to do so. I took my first try recently, _what I found under "places" of the top bar was only 3 out of 5 partitions I have. _

  I have two physcial harddisks in total, one containing Windows and is divided into 3 partitions, while another drive contains two partition. I can access my content in the Windows partition and the 2 partitions in another physcial harddisk.
  
  Though I tried to search for help on Google before posting, as an absolute beginner, I have no idea what are the correct terms which describe my situation correctly. Why Ubuntu can automatically find out the 3 partitions and allow me to "mount"(correct term or not?) them and access them while it can't do so for the remaining 2? What should I do in order to
  -Instruct Ubuntu to do the same thing for the remaining 2 partitions
  or, if 1 is not possible
  -Manually "mount" the partitions?

  Thanks for you attention.

---

### Post by Patb on 2008-08-24
Ryan, to check whether both drives are actually being recognised by the computer in Ubuntu, open a terminal (Applications > Accessories > Terminal) and type 
```
sudo fdisk -l
```
That will give you a list of all partitions whether mounted or not. Let's say for example you see the two extra partitions listed as /dev/xxxx and /dev/yyyy.  Then you can try to mount them using the following commands (change the xxxx and yyyy as appropriate of course):
```
sudo mkdir /media/partn1
sudo mkdir /media/partn2
sudo mount /dev/xxxx /media/partn1 -t vfat -o nls=utf8,umask=0222
sudo mount /dev/yyyy /media/partn2 -t vfat -o nls=utf8,umask=0222
```
Then you can also use Gparted from the same terminal to get a gui view of the disks:
```
sudo gparted
```
This should get you started.  I hope this is at least approximately what you are after.  

Cheers, Pat.

---

### Post by ryanraphael on 2008-08-24
Thank you Pat, after following your instruction, I got the following message.
```
  ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e382300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3161    25390701    c  W95 FAT32 (LBA)
/dev/sda2            3162        7297    33222420    f  W95 Ext'd (LBA)
/dev/sda5            3162        7297    33222388+   b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49fd49fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4924    39551998+   c  W95 FAT32 (LBA)
/dev/sdb2            4925       19457   116736322+   f  W95 Ext'd (LBA)
/dev/sdb5            4925       12191    58372146    b  W95 FAT32
/dev/sdb6           12192       19457    58364113+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo mkdir /media/try1
ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /media/try1 -t vfat -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ dmesg | tail
[ 1154.986560] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[ 1160.982454] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[ 1166.978345] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[ 1172.462673] FAT: Unrecognized mount option "nls=utf8" or missing value
[ 1172.975236] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[ 1178.971136] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[ 1184.966057] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[ 1190.961933] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[ 1196.957821] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[ 1202.953704] ACPI: Unable to turn cooling device [f7c4a768] 'on'
```

When I used Gparted
  [IMG]http://farm4.static.flickr.com/3177/2791191887_1469f4691f_o.png[/IMG]

  I am sure that the sdb6 and sdb6 are those I am trying to mount. They are placed under "extended", I guess it has something to do with the message in terminal , saying that"" aren't you trying to mount an extended partition,instead of some logical partition inside?""
  However, for drive sda...
  [IMG]http://farm4.static.flickr.com/3057/2792051912_07d9744777_o.png[/IMG]
  There is only 1 partition under "extended", hmm..maybe Ubuntu can mount it because there is only 1 partition under extended, and for the 2 missing, sicne they are both extended partitions on the same physical drive and thus not working?
  Thanks for your help!
  Any idea

---

### Post by plucky on 2008-08-24
> ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /media/try1 -t vfat -o nls=utf8,umask=0222



You are trying to mount the extended partition.Change the **/dev/sdb2** to [color=blue]/dev/sdb5[/color]

/dev/sda and /dev/sdb are two different drives,see the output of "sudo fdisk -l",and partitions /dev/sda5 and /dev/sdb5 are also different partitions on different drives.


Good Luck

---

### Post by ryanraphael on 2008-08-25
Thank you Plucky! But I tried wat you said but it failed, these are the results
```
  ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e382300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3161    25390701    c  W95 FAT32 (LBA)
/dev/sda2            3162        7297    33222420    f  W95 Ext'd (LBA)
/dev/sda5            3162        7297    33222388+   b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49fd49fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4924    39551998+   c  W95 FAT32 (LBA)
/dev/sdb2            4925       19457   116736322+   f  W95 Ext'd (LBA)
/dev/sdb5            4925       12191    58372146    b  W95 FAT32
/dev/sdb6           12192       19457    58364113+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo mkdir /media/partn1
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /media/partn1 -t vfat -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/sdb5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ dmesg | tail
[  697.096628] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[  703.092242] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[  709.091195] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[  715.082969] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[  721.078754] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[  727.070479] FAT: Unrecognized mount option "nls=utf8" or missing value
[  727.074546] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[  733.070320] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[  739.066108] ACPI: Unable to turn cooling device [f7c4a768] 'on'
[  745.065892] ACPI: Unable to turn cooling device [f7c4a768] 'on'

```

   Thanks for everyone's warm suggestions!

---

### Post by plucky on 2008-08-25
> [  727.070479] FAT: Unrecognized mount option "nls=utf8" or missing value


That seems to be the problem with the command.I think that option is for "ntfs" file system not vfat.

Checkout the Psychocats website in my signature for mounting windows partitions.

Good Luck

---

### Post by ryanraphael on 2008-08-25
Thank you Plucky! I did visited that site before posting but I did not understand it, but now I do! Learning is such that funny!
  Now, the biggest part of the problem is solved, and my final questions are...
  1:As I see on Plucky's site, you are editing the /etc/fstab file so that you won't have to type the clumsy commands everytime. Is it possible for me to customize the /etc/fstab file on my LiveCD ? By the way, my /etc/fstab file looks strange
  ```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0


```
  2:After mounting the drives manually, Linux display them as "59.8GB media", but not their original name like "FAMILY" for my C drive.But I can see the original names of those drives, which can be recognized by the system itself and all I have to do is to press 'places-->Family' to mount it. What should I do?

  Once again, thanks for everyone's help!

---

