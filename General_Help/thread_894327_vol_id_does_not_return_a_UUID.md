---
title: "vol_id does not return a UUID"
date: 2008-08-19
forum: General Help
---

### Post by cgent on 2008-08-19
I have 4 SATA disks plugged into a Silicon Image 3114R RAID controller on my motherboard. I don't want to use them in a RAID array, just as individual disks mounted using fstab. udev does not map them consistently to /dev/sdX devices so I want to use UUID to mount the drives. The problem is vol_id does not return a UUID for the drives: 
> vol_id  /dev/sdi
ID_FS_USAGE=raid
ID_FS_TYPE=silicon_medley_raid_member
ID_FS_VERSION=0.0
ID_FS_UUID=
ID_FS_UUID_ENC=
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

Is there a way to get vol_id to report a UUID for disks plugged into this controller?

Chris.

---

### Post by cgent on 2008-08-19
After a bit more google work I have found that I can identify the drives in fstab using the the /dev/disk/by-id/ata-SAMSUNG_HD103UJ_S13PJ1KQ303676 link created by udev. According to udev documentation the by-id is a persistent naming scheme, so unless anyone knows otherwise, I will use this by-id rather than UUID in my fstab file.

---

### Post by fjgaude on 2008-08-19
Using the **blkid** should show all UUIDs, if you are still interesed.

---

### Post by drs305 on 2008-08-19
You could also label each partition/drive and mount them via the label.

To label an ext3 partition:
```
sudo tune2fs -L <label> <dev> # sudo tune2fs -L mylabel /dev/sdb1

```

To check labels/uuids:
```

sudo blkid

```

To mount via label in fstab:
```
LABEL=mylabel /media/mountpoint ...
```

---

### Post by coffeecat on 2008-08-19
> **fjgaude said:**
> Using the **blkid** should show all UUIDs

> **drs305 said:**
> To check labels/uuids:
```

sudo blkid

```

One point of information: blkid creates a cache the first time it is run (somewhere in /etc iirc). If you run it a subsequent time it reads from the cache rather than rescanning the drives, which means that if you have reformatted any partitions, you'll get erroneous results. What the blkid devs were smoking when they dreamt up that daft default behaviour is a question I've never found the answer to. What I do to get round this - particularly as I frequently reformat partitions on my multi-boot setup - is:

```
sudo blkid -c /dev/null
```See man blkid for more.

---

### Post by drs305 on 2008-08-19
> **coffeecat said:**
> One point of information: blkid creates a cache the first time it is run (somewhere in /etc iirc). If you run it a subsequent time it reads from the cache rather than rescanning the drives, which means that if you have reformatted any partitions, you'll get erroneous results. 

I've read that and thought I was fortunate that in my frequent reformattings I hadn't been burned. I read the man pages and they don't contradict anything you say.

Using gparted:
I just reformatted two partitions (fat and ntfs), resized an ext3 and created a new ext3 out of the new space. I then ran the 'sudo blkid' command and it correctly identified the changed uuids. Interestingly, the reduced ext3 partition retained it's orginal uuid (perhaps because I reduced it from the end). I then ran the command again with the '-c /dev/null' option but the results were the same.

I would guess that over time the process has changed for the better and it just hasn't been documented.

---

### Post by coffeecat on 2008-08-19
> **drs305 said:**
> I would guess that over time the process has changed for the better and it just hasn't been documented.

I guess you're right. I was certainly getting wrong results from blkid a year or more ago. At first I used to delete the /etc/whatever cache, but then I got round to reading the man pages (:wink:) and settled for the -c /dev/null option. Thanks for going to the trouble to investigate. Next time I'm reformatting a partition, I'll see what I get.

**Edit:** there was a spare partition on this multiboot. I've just reformatted it in Gparted and a simple 'sudo blkid' did report the changed UUID. The default behaviour of blkid **has** changed, and for the better, so thanks for pointing that out. I remember wasting hours with a wrong UUID when I used blkid for the first time - I mean the second time. :wink: Pity the documentation is still suggesting the old behaviour. :sigh:

---

### Post by cgent on 2008-08-20
Thanks for the comments, I failed to mention that the drives only have a single xfs partition and tune2fs is only for ext2/3 partitions. Is there a similar tool for xfs partitions?

blkid does return a UUID for the drives, so my next question is how do I rewrite the udev rule file so that the uuid links get created in /dev/disk/by-uuid?

It does not appear that blkid has a similar option to vol_id --export?

---

### Post by drs305 on 2008-08-20
> **cgent said:**
> Thanks for the comments, I failed to mention that the drives only have a single xfs partition and tune2fs is only for ext2/3 partitions. Is there a similar tool for xfs partitions?

blkid does return a UUID for the drives, so my next question is how do I rewrite the udev rule file so that the uuid links get created in /dev/disk/by-uuid?

It does not appear that blkid has a similar option to vol_id --export?


Download:
```
sudo aptitude install xfsprogs
```
Labeling an xfs partition:
```

sudo umount <device>     # sudo umount /dev/sdb2
sudo xfs_admin -L <Label> <device>    # sudo xfs_admin -L mylabel /dev/sdb2

```

---

### Post by cgent on 2008-08-22
Thanks for the pointer to xfs_admin.

I have labelled all my XFS partitions. However vol_id still returns the same information:
ID_FS_USAGE=raid
ID_FS_TYPE=silicon_medley_raid_member
ID_FS_VERSION=0.0
ID_FS_UUID=
ID_FS_UUID_ENC=
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

It appears that regardsless of what disks/partitions are attached to the Silicon Image controller the information returned by vol_id is the same. I assume this is a sata_sli driver/hardware issue. 

Since udev by-label and by-uuid links are created based on the output from vol_id: 

/etc/udev/rules.d/60-persistent-storage.rules:
# by-label/by-uuid (filesystem properties)
IMPORT{program}="vol_id --export $tempnode"
ENV{ID_FS_USAGE}=="filesystem|other|crypto", ENV{ID_FS_UUID_ENC}=="?*", SYMLINK+="disk/by-uuid/$env{ID_FS_UUID_ENC}"
ENV{ID_FS_USAGE}=="filesystem|other", ENV{ID_FS_LABEL_ENC}=="?*", SYMLINK+="disk/by-label/$env{ID_FS_LABEL_ENC}"

It looks like I am back to trying to write a udev rule that uses another util such a blkid.

---

