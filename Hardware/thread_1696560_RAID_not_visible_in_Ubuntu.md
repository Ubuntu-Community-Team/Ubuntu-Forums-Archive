---
title: "RAID not visible in Ubuntu"
date: 2011-02-27
forum: Hardware
---

### Post by vat3r on 2011-02-27
Hello all,

I am inexperienced with Ubuntu as was looking for some guidance in getting Ubuntu to detect my RAID. 

I set up the RAID5 using my onboard RAID device (mobo: GIGABYTE p55m-ud2). 
I then converted it to a GUID partition table in Windows 7.
I just recently installed Ubuntu on a new partition. What must I do to access my RAID from Ubuntu?

Let me know what other information I can provide for support.

Thanks.

---

### Post by fjgaude on 2011-02-27
As I remember you can install **dmraid** and from there mount the assay.

```
sudo apt-get install dmraid

```

Then do a **man dmraid** to understand how to use it.

---

### Post by vat3r on 2011-02-27
I messed around with *dmraid* and *mount* with no luck..

[I]jesse@jesse-UBUNTU:/dev$ sudo dmraid -r
/dev/sdc: isw, "isw_cjbgaghgib", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sdb: isw, "isw_cjbgaghgib", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sda: isw, "isw_cjbgaghgib", GROUP, ok, 3907029166 sectors, data@ 0[/I]

There are my three drives that make up the RAID, 

[I]jesse@jesse-UBUNTU:/dev$ sudo dmraid -a y
RAID set "isw_cjbgaghgib_RAID5" already active
[/I]
Shows it as active even thought its inaccessible.
I tried mounting it but no luck.

I also went to DiskUtility and it shows the RAID5, as a GPT. However shows it completely unallocated (even though its half full).
It lists the device as *dm-0*

Still am not sure what to do.

---

### Post by fjgaude on 2011-02-27
```

```In Disk Utility can you mount the array? You have studied the man pages for all the options?

I haven't used **dmraid** in so many years I forget how to mount the arrays. Most folks who use Linux use **mdadm** for software raid.

If you can't find out how to use the array in Ubuntu you can always off load all the files and then create a raid5 array using mdadm.


Okay, do remember a little more.

```
sudo mount -t ext3 /dev/mapper/sil_ahahbhbjaddg /raid
```

The ext3 is to be replaced by the format the array has been made in. The /raid is the mount point you create. The sil_nnnn is name that dmraid gives to the array. Anyone of the three you showed is the array. i.e., isw_cjbgaghgib.

Do you know what the array's format is?

---

### Post by vat3r on 2011-02-27
No i cannot mount the array in disk utility. I think the issue is that Ubuntu is seeing the RAID as completely unformatted (no partitions). I can create a new partition but that seems like a really bad idea considering the raid is actually half full (when viewed from Windows7).

In Windows 7, I formatted the RAID as NTFS. I tried the command you mentioned with ntfs:

[I]jesse@jesse-UBUNTU:/dev/mapper$ sudo mount -t ntfs /dev/mapper/isw_cjbgaghgib_RAID5 /raid
NTFS signature is missing.
Failed to mount '/dev/dm-0': Invalid argument
The device '/dev/dm-0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/I]

I'm not sure if Ubuntu has issues interpreting GPTs?

---

### Post by fjgaude on 2011-02-27
Beats me... it should work... try ntfs-3g instead of ntfs.

---

### Post by ronparent on 2011-02-27
If your partitions are recognized by dmraid, you will find the symbolic links for them in /dev/mapper. Generally the convention is that the first item in the list after control is the overall raid array which is not mountable. The items following with numbers at the end are the actual partitions. In 10.10 when the raids are activated They will automatically show in nautilus,

If the raid partitions don't show there may be a problem with GPT and you would have to get to the bottom of that before you could use the drives in Ubunto.

---

