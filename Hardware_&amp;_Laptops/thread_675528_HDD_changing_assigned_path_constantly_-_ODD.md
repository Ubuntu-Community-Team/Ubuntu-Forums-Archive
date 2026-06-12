---
title: "HDD changing assigned path constantly - ODD"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by rslrdx on 2008-01-22
I have 2 hard drives on my system, one sata another pata, the odd thing is that whenever i reboot my system, at least most of the time, the drives will change their "assigned" location (missing the proper word here).

for example, i boot up and the secondary HDD is not mounted, when i look in the FSTAB, my secondary HDD might be listed as sda, and the partition I need mounted is sda5, and the path should be /media/disk. Problem is, the primary HD is mounted as sda, with its partion as sda5. So i change the secondary HDD partition to sdb5, run a "sudo mount -a" and the HDD is available again.

Its really odd to me why its doing that.

The Primary HDD is sata, and the secondary pata. 

If I open nautilus, I see the drive listed, but not mounted, if i double click it, it asks me for the administrator password, and mounts the drive a path it can use.

Any help/Tips would be apreciated, its not really that big of deal to me, since no data harm is being done, but its starting to be annoying.

Rodrigo.

---

### Post by Yellow Pasque on 2008-01-22
In your /etc/fstab file, mount by UUID instead of the /dev/path.
```
cd /dev/disk/by-uuid; ls -l
```
Should give you something like this:
> lrwxrwxrwx 1 root root 10 2008-01-21 10:48 196c7c15-ca90-492f-a140-1957cfb65bfe -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-01-21 10:48 2f6d87e5-609f-4f5c-b37e-5f3f4e6a3f84 -> ../../sdb4
lrwxrwxrwx 1 root root 10 2008-01-21 10:48 4e9cc037-6ea3-4756-9d70-bcb5a407bed2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-01-21 10:48 **7a119114-4fd7-4ee0-922f-a7d03a5b4b3e -> ../../sda1**
lrwxrwxrwx 1 root root 10 2008-01-21 10:48 92f2f224-df2a-4d89-8ddc-ff9eadc4b554 -> ../../sdb3
lrwxrwxrwx 1 root root 10 2008-01-21 10:48 dd683755-8ce8-4c3f-88aa-8340869a64d9 -> ../../sdb1

Now run **sudo lshw -businfo -C disk** to figure out what disk corresponds with the path. It'll look like:
> Bus info          Device      Class       Description
=====================================================
scsi@2:0.0.0     ** /dev/sda    disk        298GB SAMSUNG HD321KJ**
scsi@3:0.0.0      /dev/cdrom  disk        CDDVDW SH-S203B
scsi@4:0.0.0      /dev/sdb    disk        37GB WDC WD400BEVS-22

Now in your /etc/fstab file, change the first column to read UUID=<number from the ls command>

For example, if I always wanted to mount the first partition on my Samsung drive (currently sda1) as /mnt/sammy
```
#This line is vulnerable to path changes
/dev/sda1  /mnt/sammy  ext3   defaults   0  0
```
--->```
#This line is not
UUID=7a119114-4fd7-4ee0-922f-a7d03a5b4b3e   /mnt/sammy  ext3   defaults  0  0
```

---

### Post by rslrdx on 2008-01-22
Thank you.

---

### Post by rslrdx on 2008-01-26
I did this and it seems that i have to run "sudo mount -a" everytime i reboot now. Is there something else i need to do to stop this from working like this?

---

### Post by Yellow Pasque on 2008-01-26
Maybe in your /etc/fstab
> UUID=7a119114-4fd7-4ee0-922f-a7d03a5b4b3e   /mnt/sammy  ext3   **defaults**  0  0
---->
> UUID=7a119114-4fd7-4ee0-922f-a7d03a5b4b3e   /mnt/sammy  ext3   **rw,auto,exec,user,uid=1000**  0  0

---

