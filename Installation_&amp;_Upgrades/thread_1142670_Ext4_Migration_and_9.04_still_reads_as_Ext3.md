---
title: "Ext4 Migration and 9.04 still reads as Ext3?"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by silentknyght on 2009-04-29
Short story: I used one of the various (identical) guides to attempt to migrate my existing ext3 file system to ext4.  After what I believed to be a success, I rebooted, and for good measure, checked in the System Monitor after login, which read the filesystem as ext3.  What did I do wrong?

Stepwise process:
1) Upgraded to 9.04 from 8.10 (64bit) using the recommended "network upgrade" method ([http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)). Everything seems to work just fine.

2) Downloaded & burned the 9.04 live CD (ubuntu-9.04-desktop-amd64.iso.torrent).

3) Booted to the live CD.  I'm not sure how else to use the tune2fs commands, since they need the filesystem to be unmounted; I assume this is the correct procedure.

4) used the following command... I didn't include the "#", as I though it was a comment item; if I should include it, what does it do?
```
tune2fs -O extents,uninit_bg,dir_index /dev/sda5
```
where sda5 is the filesystem with 9.04.  (I have a dual-boot system, and if I'm reading the partitioner correctly, grub & the and the boot are sitting on the ntfs partition).  I checked the partitioner, which now read sda5 as ext4.  Seemed like a success...

5) I followed up with the command (again no "#")
```
e2fsck -pDf /dev/sda5
```
It found and autofixed the file system discrepancies.

6) After the fsck check finished, I rebooted, removed the live CD, and logged into 9.04 just fine, but the system monitor still shows the filesystem as ext3.


Suggestions?
~Sk

---

### Post by dox_drum on 2009-04-29
Any installed program on ext3 remains ext3... only the new installed are ext4 powered.

That's why the fresh installations is recommended.

---

### Post by alphacrucis2 on 2009-04-29
> **silentknyght said:**
> Short story: I used one of the various (identical) guides to attempt to migrate my existing ext3 file system to ext4.  After what I believed to be a success, I rebooted, and for good measure, checked in the System Monitor after login, which read the filesystem as ext3.  What did I do wrong?

Stepwise process:
1) Upgraded to 9.04 from 8.10 (64bit) using the recommended "network upgrade" method ([http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)). Everything seems to work just fine.

2) Downloaded & burned the 9.04 live CD (ubuntu-9.04-desktop-amd64.iso.torrent).

3) Booted to the live CD.  I'm not sure how else to use the tune2fs commands, since they need the filesystem to be unmounted; I assume this is the correct procedure.

4) used the following command... I didn't include the "#", as I though it was a comment item; if I should include it, what does it do?
```
tune2fs -O extents,uninit_bg,dir_index /dev/sda5
```
where sda5 is the filesystem with 9.04.  (I have a dual-boot system, and if I'm reading the partitioner correctly, grub & the and the boot are sitting on the ntfs partition).  I checked the partitioner, which now read sda5 as ext4.  Seemed like a success...

5) I followed up with the command (again no "#")
```
e2fsck -pDf /dev/sda5
```
It found and autofixed the file system discrepancies.

6) After the fsck check finished, I rebooted, removed the live CD, and logged into 9.04 just fine, but the system monitor still shows the filesystem as ext3.


Suggestions?
~Sk

You have to update your fstab as well.

---

### Post by xx58 on 2009-04-29
I download and burn 9.04 and when I made clean installation there I was not seeing Ext4 file system , but it was made partition Ext3, so where and how I can make clen 9.04 installation with file system Ext4? Thanks

---

### Post by silentknyght on 2009-04-29
> **alphacrucis2 said:**
> You have to update your fstab as well.

Is it as simple as the following?
```
gedit /mnt/etc/fstab
```
Just changing the "3" in "ext3" to "ext4" ?

...from [http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)

---

### Post by alphacrucis2 on 2009-04-29
> **silentknyght said:**
> Is it as simple as the following?
```
gedit /mnt/etc/fstab
```
Just changing the "3" in "ext3" to "ext4" ?

...from [http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)

I believe so. You can update fstab from the running OS as I think it only gets looked at during the boot up. 

gedit /etc/fstab

and change ext3 to ext4 for the partition you ran tune2fs & efsck against. Save & reboot.

---

