---
title: "[SOLVED] fsck failure during boot up"
date: 2008-11-30
forum: General Help
---

### Post by manij on 2008-11-30
hi ,

I have hardy heron in good working condition. however during boot up it does a fsck and it fails on UUID : 7AE90F3F-7587-4612-99c4-3A44-976227DD

Unfortunately I have no block with that ID

Here is my blkid out put

[B][I]/dev/sda1: UUID="4788-51DC" TYPE="vfat" 
/dev/sdb2: TYPE="swap" UUID="a2c766b6-ebb8-493e-94d7-848c0210cef2" 
/dev/sdc1: UUID="12ff02c8-4e4b-403f-8ebd-5cea84fc3150" TYPE="ext3" 
/dev/sdb3: UUID="4931-04F8" TYPE="vfat" 
/dev/sdc4: UUID="3B49-C9BC" TYPE="vfat" LABEL="M-@iM-\b %M-^SM-9$M-Ta" 
/dev/sdc2: TYPE="swap" UUID="be99f8a1-41ea-4e20-8144-d91150cda82b" 
/dev/sdb1: UUID="245f02b9-730b-4130-acfe-67f3d95d439b" TYPE="ext3" SEC_TYPE="ext2" [/I][/B]


It goes into maintenance mode in the command line. So far I have been typing exit and ignoring this error.

What is happening? how do I fix this?

---

### Post by manij on 2008-11-30
here is my /etc/blkid.tab

[B][I]
<device DEVNO="0x0801" TIME="1228080114" UUID="4788-51DC" TYPE="vfat">/dev/sda1</device>
<device DEVNO="0x0812" TIME="1228080114" TYPE="swap" UUID="a2c766b6-ebb8-493e-94d7-848c0210cef2">/dev/sdb2</device>
<device DEVNO="0x0821" TIME="1228080114" UUID="12ff02c8-4e4b-403f-8ebd-5cea84fc3150" TYPE="ext3">/dev/sdc1</device>
<device DEVNO="0x0813" TIME="1228080114" UUID="4931-04F8" TYPE="vfat">/dev/sdb3</device>
<device DEVNO="0x0824" TIME="1228080115" UUID="3B49-C9BC" TYPE="vfat" LABEL="&#65533;i&#65533;b %&#65533;&#65533;$&#65533;a">/dev/sdc4</device>
<device DEVNO="0x0822" TIME="1228080114" TYPE="swap" UUID="be99f8a1-41ea-4e20-8144-d91150cda82b">/dev/sdc2</device>
<device DEVNO="0x0811" TIME="1228080114" UUID="245f02b9-730b-4130-acfe-67f3d95d439b" TYPE="ext3" SEC_TYPE="ext2">/dev/sdb1</device>[/I][/B]

---

### Post by taurus on 2008-11-30
Can you also post your /etc/fstab?

[ccode]cat /etc/fstab[/code]

---

### Post by manij on 2008-11-30
> **taurus said:**
> Can you also post your /etc/fstab?

[ccode]cat /etc/fstab[/code]

Ok I see it in the fstab. this fstab looks like an old fstab to me becos, I no longer have the ntfs partiton it is talking about!

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=12ff02c8-4e4b-403f-8ebd-5cea84fc3150 /               ext3    errors=remount-ro 0       1
# /dev/sda1
UUID=9CAC346AAC3440D6 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=470C-7C0D  /media/sda2     vfat    utf8,umask=007,gid=46 0       1
# /dev/sdb3
***UUID=7ae90f3f-7589-4612-99c4-3a44976727dd /media/sdb3     ext3    defaults        0       2***
# /dev/sdb4
UUID=3B49-C9BC  /media/sdb4     vfat    utf8,umask=007,gid=46 0       1
# /dev/sdc1
UUID=4788-51DC  /media/sdc1     vfat    utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=8405731e-d8db-4653-8373-11ccd95a94f6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=127,devmode=664 0 0

---

### Post by zeigfried on 2008-11-30
If you are sure you don't need that partition anymore run:
```
gksudo gedit /etc/fstab
```
Comment ("#" as the first character of the line) this UUID and save. You shall have no more problems while booting.

---

### Post by manij on 2008-11-30
> **zeigfried said:**
> If you are sure you don't need that partition anymore run:
```
gksudo gedit /etc/fstab
```
Comment ("#" as the first character of the line) this UUID and save. You shall have no more problems while booting.

I there a way to update the fstab to reflect the current partitions?

---

### Post by taurus on 2008-11-30
By the way, I recommend you change the last digit from 1 to 0 for all ntfs & vfat partitions.  You don't want Ubuntu to run fsck on those partitions.

---

### Post by mdurham on 2008-11-30
> **manij said:**
> I there a way to update the fstab to reflect the current partitions?

sudo mount -a

---

### Post by manij on 2008-11-30
> **mdurham said:**
> sudo mount -a

When I do this, I get this

ntfs-3g: Failed to access volume '/dev/disk/by-uuid/9CAC346AAC3440D6': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
mount: special device /dev/disk/by-uuid/470C-7C0D does not exist
mount: special device /dev/disk/by-uuid/7ae90f3f-7589-4612-99c4-3a44976727dd does not exist


Do I have to go back and edit my fstab at this point? Becos, I just checked it it still show the old partitions which no longer exist

---

### Post by mdurham on 2008-11-30
> **manij said:**
> When I do this, I get this

ntfs-3g: Failed to access volume '/dev/disk/by-uuid/9CAC346AAC3440D6': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
mount: special device /dev/disk/by-uuid/470C-7C0D does not exist
mount: special device /dev/disk/by-uuid/7ae90f3f-7589-4612-99c4-3a44976727dd does not exist


Do I have to go back and edit my fstab at this point? Becos, I just checked it it still show the old partitions which no longer exist
Have you tried rebooting?

---

### Post by manij on 2008-11-30
> **mdurham said:**
> Have you tried rebooting?

Yes, I tried. It didn't help!

SO how do I update my fstab to reflect my current partitons w/o manually editing it?

---

### Post by zeigfried on 2008-11-30
Don't be afraid of doing it manually (it is just a # in the end), welcome to Linux... You will get the hang of it.

Cheers

---

### Post by aboud on 2008-12-08
hello, 
hope you all enjoying using ubuntu! 

I'm facing the same problem, fsck is telling me : 

```

Log of fsck -C3 -R -A -a 
Mon Dec  8 23:26:01 2008

fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Unable to resolve 'UUID=9378714f-f4f9-4494-9149-2332e8c8f87c'

fsck died with exit status 8

Mon Dec  8 23:26:01 2008
----------------

```

while my UUID is different, i have only one ext3 partition. 
what would happen if replace this uuid by the usual /dev/sda in fstab ?
our what can i fix the uuid in fstab according to what vol_id gives or blkid gives ? 
how do i do the manual check while booting ? 
some time fsck tells me it's dangourse to check mounted partition while umount tells me the value is not mounted, 
and some time when i successed to do the check fsck do it very quickly and past "clean" how do i do manually the usual long check that happen usually ?

---

