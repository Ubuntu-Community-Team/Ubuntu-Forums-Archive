---
title: "Corrupt Backup GPT file LVM RAID"
date: 2018-01-28
forum: Hardware
---

### Post by Dan Z on 2018-01-28
Hello-


Having a problem with a Corrupted back up GPT file. 

Computers is a refurbished Dell Opti-flex 990.

Here is drive set up , it is LVM

-OptiPlex-990:~$ df -h

Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.9G     0  3.9G   0% /dev
tmpfs                        786M  9.6M  776M   2% /run
/dev/mapper/ubuntu--vg-root  184G   75G  101G  43% /
tmpfs                        3.9G  7.1M  3.9G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop1                   7.7M  7.7M     0 100% /snap/gnome-easytag/11
/dev/loop2                    82M   82M     0 100% /snap/core/3887
/dev/loop0                    84M   84M     0 100% /snap/core/3604
/dev/loop4                    84M   84M     0 100% /snap/core/3748
/dev/loop3                    76M   76M     0 100% /snap/cubicsdr-casept/4
/dev/sda2                    473M  278M  171M  62% /boot
/dev/sda1                    511M  6.8M  505M   2% /boot/efi
tmpfs                        786M   60K  786M   1% /run/user/1000
/dev/sdb1                     30G   12G   18G  40% /media/dandell/Lexar



Tried this first:

~$ sudo gdisk /dev/sda
[sudo] password for 
GPT fdisk (gdisk) version 1.0.1

Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sda.
Warning: The kernel is still using the old partition table.
The new table will be used at the next reboot or after you
run partprobe(8) or kpartx(8)
The operation has completed successfully.
dandell@dandell-OptiPlex-990:~$ 
================================
Rebooted and tried again:

sudo gdisk /dev/sda
[sudo] password for dandell: 
GPT fdisk (gdisk) version 1.0.1

Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Command (? for help): 
=========================================
Issue still present-

So then did more research, it was suggested that BIOS may be set to RAID, I cheeked and it was.

checked BIOS, it is UEFI boot, from GRUB

Change BIOS to AHCI, no boot, ATA no BOOT, so back to set as RAID

SO --
If it is set as RAID, seems like I will always have the corrugated Backup GPT table?

This issue came up when I was trying to increase the boot partition SDA2 from 500MB (fills too fast),

But first I had to shrink SDA3

I was able to shrink SDA3 LV with LVM, but can't shrink the Physical size with Gparted presumably due to the corrupt GBT file?

Any help appreciated

thanks DAN

---

### Post by Dan Z on 2018-01-29
Forgot to say running 16.04
DAN

---

### Post by oldfred on 2018-01-29
I do not know LVM, but have a couple of links.
You have to use LVM tools to resize logical volumes and only then can shrink the partition the LVM is inside.

 How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724) 

 [http://askubuntu.com/questions/852019/i-wish-to-expand-my-lvm2-partition](http://askubuntu.com/questions/852019/i-wish-to-expand-my-lvm2-partition)
[http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume) 

But if /boot is 500MB is should be large enough. But you do need to regularly houseclean.
      
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
-s is simulate so you can see what it will do, then run without -s
sudo apt-get -s autoremove 

 I prefer synatic and keeping 2 kernels, current and one known working older on.

---

### Post by Dan Z on 2018-01-30
Thanks for the assistance.

To clarify-

I was able to shrink the Logical volume.

I did the steps to shrink it in the 3rd link you provided. All went as it should- until I tried to actually shrink it with Gparted.

I continue to get the Corrupted backup file error.[ATTACH=CONFIG]278378[/ATTACH]

Seems that need to be fixed before I can proceed. How to do that?

Thanks Dan

---

### Post by oldfred on 2018-01-30
I believe I have seen where LVM that spans more than one drive or RAID can confuse gpt which has a back up at the end of the drive.

But see what this says:
       repair gpt:
[URL="http://www.rodsbooks.com/gdisk/repairing.html"]http://www.rodsbooks.com/gdisk/repairing.html
[/URL]
 Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

May not want to do the w to update partition tables unless sure it is correct.


[URL="http://www.rodsbooks.com/gdisk/repairing.html"]
[/URL]

---

### Post by Dan Z on 2018-01-31
I used gdisk, all seemed ok, I did backup, but don't think it saved as I was off a CD. Did w. Now no boot. 

Tried boot-repair,no luck. It says it fixed it, but it didn't. On boot try screen says "volume group 'ubuntu-vg' not found.

Boot repair no longer even shows any grub or MBR choices. 

this is form this morning after my gdisk fiasco

[http://paste.ubuntu.com/26494777](http://paste.ubuntu.com/26494777) (seems to look ok)

after work I tried again

[http://paste.ubuntu.com/26497478](http://paste.ubuntu.com/26497478) (definitely not ok)

Thanks DAN

---

### Post by oldfred on 2018-01-31
You keep changing to LVM. I do not know LVM, someone that users servers a lot will have to help as they often use LVM.

---

### Post by Dan Z on 2018-02-03
I threw in the towel and re-installed 16.04 without LVM, but first turned off RAID in BIOS.

All is good now .

Thanks DAN

---

