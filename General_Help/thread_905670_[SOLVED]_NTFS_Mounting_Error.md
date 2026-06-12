---
title: "[SOLVED] NTFS Mounting Error"
date: 2008-08-30
forum: General Help
---

### Post by Altay_H on 2008-08-30
Until recently, I could auto-mount my external [NTFS] hard drive without issues and read/write to it. Now I get the following error when I plug it in:



Cannot mount volume.

Unable to mount the volume 'SimpleDrive'.

Details:
$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g/dev/sdb1 /media/SimpleDrive -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1 /media/SimpleDrive ntfs-3g force 0 0


Here's the content of my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=55d8abe7-f46b-438a-bafd-7fc53bec4ca9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda5
UUID=1d685ee9-72e6-48d7-ba9f-4b95996a1c68 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#This line is to mount USB drives as hdb rather than disk
/dev/sdb        /media/hdb      user,noauto,exec 0 0
```

---

### Post by cariboo on 2008-08-30
> Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g/dev/sdb1 /media/SimpleDrive -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1 /media/SimpleDrive ntfs-3g force 0 0

The above pretty well tells you what to do

Jim

---

### Post by drs305 on 2008-08-30
Your best option to correct the problem is to go back to windows and accomplish a clean shutdown. If you don't want to do that or #2, another option, if you have ntfsprogs installed, is to run the following, which *may* eliminate minor problems. Only the first option actually repairs things...
```
sudo ntfsfix /dev/<device>
```

---

### Post by EmanresuusernamE on 2008-08-30
Third would be for you to use the following command:
mount /dev/<device partition> <mount point> -t ntfs-3g -o force

---

