---
title: "Partition Recovery When USB Drive Doesn't Get Recognized/Mounted"
date: 2009-10-07
forum: Hardware
---

### Post by K.Graveson on 2009-10-07
Hey,

this is my first forum post and I couldn't find the answer in searches. 

My brother dropped his 1.5 TB external Seagate FreeAgent Desk HD. When plugged back in to windows, it showed up as an unpartitioned drive. I got excited, as I figured all I'd need to do is restore partition table or chkdsk it or something simple. :(

I'm trying to recover the original partition table without have to format.

Can anyone help force Ubuntu to assign the usb device to something like sdb?

Here is what I have so far. Let me know if you need more info.


Currently on Windows, it shows up as a usb device. Doesn't show up in my computer or the visual disk manager, so no windows tools through gui. (Can't get a drive letter for it.)

Currently in Ubutu, 
_[SIZE=3]**dmesg OUTPUT:**[/SIZE]_
[686898.335420] usb 2-3: USB disconnect, address 2 ***(<<< This was my 5GB jump drive being disconnected before I connected the 1.5TB)***
[687040.716517] usb 2-3: new high speed USB device using ehci_hcd and address 3
[687040.849145] usb 2-3: configuration #1 chosen from 1 choice

but the 1.5TB is not assigned a sbXY or sdXY

_**[SIZE=3]df OUTPUT:[/SIZE]**_
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             19228308    605376  17646180   4% /
tmpfs                  1030784         0   1030784   0% /lib/init/rw
varrun                 1030784       332   1030452   1% /var/run
varlock                1030784         0   1030784   0% /var/lock
udev                   1030784       164   1030620   1% /dev
tmpfs                  1030784     20504   1010280   2% /dev/shm
lrm                    1030784      2392   1028392   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda9             19525440  11989840   7535600  62% /JumpSpace
/dev/sda2               474472     23644    426329   6% /boot
/dev/sda8            896158628 863026192  33132436  97% /home
/dev/sda6              4806904    156408   4406312   4% /tmp
/dev/sda7              4806904   3011280   1551440  66% /usr
/dev/sda1             29294492  26577636   2716856  91% /media/500GB Store
/dev/sr0               3683516   3683516         0 100% /media/cdrom0

[SIZE=3]_**fstab OUTPUT:**_[/SIZE]
proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=d67dd2e1-27fa-4a68-849d-9b3f5672da6a / ext4 relatime,errors=remount-ro 0 1
# Entry for /dev/sda9 :
UUID=4055-F529 /JumpSpace vfat utf8,umask=007,gid=46 0 1
# Entry for /dev/sda2 :
UUID=fe18567e-bf92-4dcc-b077-e0fbe6435fe4 /boot ext4 relatime 0 2
# Entry for /dev/sda8 :
UUID=a1db6922-1ac0-4af0-a62e-4213ff481099 /home reiserfs relatime 0 2
# Entry for /dev/sda6 :
UUID=430ab861-972d-4356-8ec5-bbb77134f135 /tmp ext4 relatime 0 2
# Entry for /dev/sda7 :
UUID=20922d48-0f42-4f5b-bd61-f72b82c7dc66 /usr ext4 relatime 0 2
# Entry for /dev/sda5 :
UUID=c338112e-b2a8-4b8b-bb81-f7f8882b1163 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/500GB\040Store ntfs-3g defaults,locale=en_US.UTF-8 0 0

[SIZE=3]_**mtab OUTPUT:**_[/SIZE]
/dev/sda3 / ext4 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=755 0 0
/dev/sda9 /JumpSpace vfat rw,utf8,umask=007,gid=46 0 0
/dev/sda2 /boot ext4 rw,relatime 0 0
/dev/sda8 /home reiserfs rw,relatime 0 0
/dev/sda6 /tmp ext4 rw,relatime 0 0
/dev/sda7 /usr ext4 rw,relatime 0 0
/dev/sda1 /media/500GB\040Store fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/kenny/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=kenny 0 0
/dev/sr0 /media/cdrom0 udf ro,nosuid,nodev,utf8,user=kenny 0 0

---

### Post by K.Graveson on 2009-10-07
UPDATE:

I fixed my problem with updating ubuntu, allowing my to finally install testdisk. (Every attempt at updating led to it failing during the initial check.) I changed download servers and it fixed it immediately. 2 hours of updates to download!! Yes!

Anyway. testdisk showed that it too would not recognize that I had a second drive plugged in... It only saw sda and my cd0 drive. Sad face...

Any ideas on how to access the data on my brother's drive?

Thanks, community!

-Kenny-

---

