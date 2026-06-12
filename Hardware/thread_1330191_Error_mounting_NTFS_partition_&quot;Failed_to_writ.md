---
title: "Error mounting NTFS partition: &quot;Failed to write lock&quot;"
date: 2009-11-18
forum: Hardware
---

### Post by eveld on 2009-11-18
On my dual-boot ThinkPad T400s (running Ubunutu 9.10 and Vista), I today suddenly got an error when mounting an NTFS partition. When trying to mount the partition via Nautilus, I get the following message:

[I]Error mounting: mount exited with exit code 18: Failed to write lock '/dev/sda2': Resource temporarily unavailable
Error opening '/dev/sda2': Resource temporarily unavailable
Failed to mount '/dev/sda2': Resource temporarily unavailable
[/I] 
Trying to force mount from the command line:

[I]~$ sudo mount -t ntfs /dev/sda2 /media/SW_Preload -o force
Failed to write lock '/dev/sda2': Resource temporarily unavailable
Error opening '/dev/sda2': Resource temporarily unavailable
Failed to mount '/dev/sda2': Resource temporarily unavailable
[/I]
After a spending the morning googling for similar cases, I'm still pretty much emtpy-handed. If any one has a clue as to how I can fix this I would be very grateful! 

I include the output of `*df -h*',  `*sudo fdisk -l*' and `*cat /etc/fstab'*, hoping that someone can make some more sense out of it than I can. Thanks a million in advance for all help!! 

:~$ df -h
[I]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              21G  9.3G   11G  48% /
udev                  2.9G  312K  2.9G   1% /dev
none                  2.9G  272K  2.9G   1% /dev/shm
none                  2.9G  196K  2.9G   1% /var/run
none                  2.9G     0  2.9G   0% /var/lock
none                  2.9G     0  2.9G   0% /lib/init/rw
/dev/sda1             1.5G  806M  695M  54% /media/SERVICEV003
[/I]


~$ cat /etc/fstab
[I]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=5fce3a2c-fe73-4b85-a061-719faf1b6351 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a388e944-b030-49ff-8217-88eeb9dc4a31 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Windows NTFS partition
UUID="7050ADBA50AD8784"    /media/SW_Preload    ntfs    relatime    0    2
[/I]


:~$ sudo fdisk -l
[I]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b87409d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       25863   206205944    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           29127       30402    10240000    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           25864       29100    25991280    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           25864       28602    21992008+  83  Linux
/dev/sda6           28602       29100     3999208+  82  Linux swap / Solaris

Partition table entries are not in disk order
[/I]

(BTW; I've tried booting into Windows and that works fine. Going back to Ubuntu again, the mounting error for */dev/sda2* persists. Note that the other NTFS partitions mount fine, however.)

-e

---

### Post by armandorl on 2009-12-04
Hi I had a similar problem today and now it is solved I am not sure if this will work for you

1. I changed to command line view CTRL+ALT+F6
2. Login as root
3. When I typed mount /dev/sda5 /media/disk, I've got the same error as you did

But then I just created the folder manually

mkdir /media/disk

and tried again

mount /dev/sda5 /media/disk
exit

I returned to the Gnome environment CTRL+ALT+F7

And it was solved, some of my links are not working but I can access all my files on my NTFS Partition trough /media/disk and I have already created new links that work.

Hope it works for you!

---

### Post by FariAzz on 2009-12-07
Hi,

I got the same error with Ubuntu 9.10, one of my NTFS partitions suddenly disappeared.

I fixed it by creating the disk folder in the media folder, from Nautilus (using "open as administrator" to enter the media folder). After creating the folder the lost partition magically appeared.

---

### Post by eveld on 2009-12-08
Thanks for replying.

Replacing "ntfs" in the mount command above with "ntfs-3g" solved the problem for me.

(This fix was suggested to me by SlimG in [this thread]("http://forum.ubuntu.no/viewtopic.php?f=28&t=2859&sid=79a1029a6b4bfa302c032bdfb3550e70&p=13270") in a Norwegian Ubuntu forum.)

---

### Post by H.Trebusz on 2011-06-10
I had the same problem in LinuxMint and I have simply installed ntfs-config package. It started working even before I checked "enable write support for external devices". So try it first.

---

