---
title: "hard disk utilisation"
date: 2009-12-25
forum: Hardware
---

### Post by u_kapaley256 on 2009-12-25
Hi all,

I recently installed kubuntu 9.10.I have AMD 2.2 Ghz turion with 8 gb of ram on my hp-pavilion although i am using a 32 bit system

Recently i observe that the hard drive led is on all the time and processor utilisation is upto 62% while only firefox is running from my side
I also checked system monitor which shows upto 6% utilisation for only 2 processes 

This hard drive led is particularly unnerving.what could it be ?

-Udayan

---

### Post by taurus on 2009-12-25
Is it running at 62% the whole time you have the computer on or only a short period of time?  Next time the CPU spikes up, open a terminal and look at the output of the top command to see which processor is taking the load.

```
top
```

---

### Post by u_kapaley256 on 2009-12-25
Hi,

Thanks for your prompt reply.
Its actually something else but i still need help.

I noticed that my partitions don't get auto-mounted and i cant get one of them to mount by clicking on it with the dolphin file manager(not even as root)although i can the other one which automatically mounts the earlier one as well and the processor suddenly comes down to 8% and the hard drive activity dies as well.

I added uid=1000,gid=1000 (myself) into the fstab entry for the partition which didnt change anything

I find this line in the fdisk -l output :
"Partition 1 does not end on cylinder boundary"


Udayan

---

### Post by taurus on 2009-12-25
Post the outputs of these commands from a terminal.

```
df -h
cat /etc/fstab
sudo fdisk -l
```

---

### Post by cascade9 on 2009-12-26
BTW, why are you using 32bit on a 64bit capable system with 8GB of RAM?

---

### Post by u_kapaley256 on 2009-12-26
Hi,
Yeah i think i should rather install 64 bit 
But i would like to know first whether the partition table is screwed up
These are the outputs requested 
Thanks for the replies

udayan@udayan-pc:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              92G   27G   61G  31% /
udev                  1.8G  316K  1.8G   1% /dev
none                  1.8G     0  1.8G   0% /dev/shm
none                  1.8G   80K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw
udayan@udayan-pc:~$ cat /etc/fstab
#UUID=2E28959D2895649D /media/disk-1 ntfs-3g users 0 0
#UUID=73BB-481F /media/disk vfat users 0 0
UUID=d4842b84-a247-4721-bc32-445a47ddf83b swap swap sw 0 0
UUID=ee77acdb-fb3b-4008-8b79-1d62e02d714a / ext4 defaults 0 1
udayan@udayan-pc:~$ sudo fdisk -l
[sudo] password for udayan:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x762fb085

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       29905   240007112+   7  HPFS/NTFS
/dev/sda3           42133       60801   149958742+   b  W95 FAT32
/dev/sda4           29906       42132    98213377+   5  Extended
/dev/sda5           29906       29974      554179+  82  Linux swap / Solaris
/dev/sda6           29975       42132    97659103+  83  Linux

Partition table entries are not in disk order

---

