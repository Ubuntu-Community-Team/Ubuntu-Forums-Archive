---
title: "firewire external hard drive read only"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by bobbydale on 2008-02-25
My firewire external drive craps out after trying to write more than a few megs to it.  After blinking and acting stupid for a minute or two, it switches to read-only.  The only way I can read the drive again is to completely reboot my machine.  I am running the 2.6.22-14-generic kernel and Gutsy 7.10.  

Any ideas?

Here is an example:

root@laptop:/media/externaI# cp /home/user/somebig.file .

[sits and acts stupid for a minute]

root@laptop:/media/externaI# ls -l
ls: reading directory .: Input/output error
total 0

root@laptop:/media/externaI# dmesg
[SNIP]
[ 5471.956000] sd 0:0:0:0: scsi: Device offlined - not ready after error recovery
[ 5471.956000] sd 0:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 5471.956000] end_request: I/O error, dev sda, sector 101770247
[ 5471.956000] Buffer I/O error on device sda1, logical block 12721273
[ 5471.956000] lost page write due to I/O error on sda1
[ 5471.956000] Buffer I/O error on device sda1, logical block 12721274
[ 5471.956000] lost page write due to I/O error on sda1
[ 5471.956000] Buffer I/O error on device sda1, logical block 12721275
[ 5471.956000] lost page write due to I/O error on sda1
[ 5471.956000] Buffer I/O error on device sda1, logical block 12721276
[ 5471.956000] lost page write due to I/O error on sda1
[ 5471.956000] Buffer I/O error on device sda1, logical block 12721277
[ 5471.956000] lost page write due to I/O error on sda1
[ 5471.956000] Buffer I/O error on device sda1, logical block 12721278
[ 5471.956000] lost page write due to I/O error on sda1
[ 5471.956000] Buffer I/O error on device sda1, logical block 12721279
[ 5471.956000] lost page write due to I/O error on sda1
[ 5471.956000] Buffer I/O error on device sda1, logical block 12721280
[ 5471.956000] lost page write due to I/O error on sda1
[ 5471.956000] Buffer I/O error on device sda1, logical block 12721281
[ 5471.956000] lost page write due to I/O error on sda1
[ 5471.956000] Buffer I/O error on device sda1, logical block 12721282
[ 5471.956000] lost page write due to I/O error on sda1
[ 5471.956000] sd 0:0:0:0: rejecting I/O to offline device
[SNIP - it repeats this about a gajillion times]
[ 5600.848000] sd 0:0:0:0: rejecting I/O to offline device
[ 5600.848000] EXT3-fs error (device sda1): ext3_find_entry: reading directory #6344650 offset 0
[ 5600.860000] sd 0:0:0:0: rejecting I/O to offline device
[ 5600.860000] EXT3-fs error (device sda1): ext3_find_entry: reading directory #6344650 offs

Any ideas?  Side note:  I have another, newer laptop running the same kernel and version and it reads and writes to the drive fine.  This leads me to believe that the laptop I am getting the errors on should be reading and writing at a slower rate, but I am not sure how to adjust the Firewire rates like you can with USB.

---

### Post by hhhhhx on 2008-02-26
login as root, right click the HDD icon, preferences,  go to permissions tab, allow read and write. :)

---

### Post by Yellow Pasque on 2008-02-26
> login as root,
No need for this, just go to the terminal and enter **sudo nautilus**

xhhux's suggestion should work. If it doesn't go to the terminal and run this after you plug the drive in:
```
cat /etc/mtab
```
Paste output here.

---

### Post by bobbydale on 2008-02-26
oot@laptop:/media# cat /etc/mtab
/dev/hda8 / ext3 rw,errors=remount-ro,usrquota,grpquota 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/hda6 /home ext3 rw 0 0
/dev/hda5 /media/feisty ext3 rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdb1 /media/SEAGATE vfat rw 0 0
/dev/sda1 /media/vantec1 ext3 rw 0 0
/dev/sda2 /media/vantec2 ext3 rw 0 0
/dev/sda3 /media/vantec3 ext3 rw 0 0

---

