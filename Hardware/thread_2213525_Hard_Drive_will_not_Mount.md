---
title: "Hard Drive will not Mount"
date: 2014-03-27
forum: Hardware
---

### Post by mikee2 on 2014-03-27
I have  Western Digital Green 2TB hard drive that I installed and partioned NTFS today. Originally I had errors partioning it becuase of misalignment, but fixed the problem when aligned it to the cylinder.  After that the drive showed up in Nautilus, but was not mounted. The only way I was (and still am) able to mount the drive is to go into Gparted and mount the drive there. If I attempt to mount the drive from Nautilus I get a permissions error. 

What worked for me yesterday on another drive was to use the NTFS configuartion tool. It was almost magic, It just auto-detected the drives and then after htat they always booted on startup. But at this point this NTFS tool will not see my new WD drive. 


So far I have tried the following procedures in attempt to make this work:

**1** - edited the startup applications to launch this command:

**udisksctl mount --block-device /dev/disk/by-uuid/028c2dce-edab-4ae4-91b6-cbd7bc0ecc3d**

**2** - Launched the NTFS Configuration tool (as decribed above)

**3** - Mounted/unmounted the drive in GPARTED

Edited (with sudo) the /etc/fstab file. Here is the output with the drive in question being in [COLOR=#ff0000]red[/COLOR] text:[INDENT]
[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda1 :
UUID=43c09daf-08a5-44f2-89b0-fc7c6f0d1e67    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sde1 :
UUID=443AFBAD7FE50945    /media/DX100_    ntfs-3g    defaults,nosuid,nodev,locale=en_CA.UTF-8    0    0
#Entry for /dev/sdb1 :
UUID=FCE456F5E456B21E    /media/Galaxy\M83    ntfs-3g    defaults,nosuid,nodev,locale=en_CA.UTF-8    0    0
#Entry for /dev/sdd1 :
UUID=1CA057FDA057DBB8    /media/Holideck    ntfs-3g    defaults,nosuid,nodev,locale=en_CA.UTF-8    0    0
[COLOR=#ff0000]#Entry for /dev/sdc1 :
UUID=028c2dce-edab-4ae4-91b6-cbd7bc0ecc3d   /media/Planet_S    defaults,nosuid,nodev,locale=en_CA.UTF-8    0    0[/COLOR][/B]
[/INDENT]
[INDENT]
[/INDENT]

I am not sure if this has to do with how the volume was partioned as mentioned at the beggning of this post. One thing I did notice was that the UUID seems like a much longer string than all the other drives on my machine (not sure if this is relevant or not). The drive seems to work fine if I mount it in GPARTED. Att his point I am not sure what do. ANy help woudl be appreciated. 

Running UBUNTU 12.04

---

### Post by ajgreeny on 2014-03-27
We need to see your output from ```
sudo blkid -c /dev/null
sudo parted -l
``` and it would also be useful to know how you formatted the disk to NTFS; what utility or application did you use, because as you say, the UUID is unusual in length and formatting of the alphanumerics;  the UUID looks more like an ext4 version, so I wonder what's going on.

---

