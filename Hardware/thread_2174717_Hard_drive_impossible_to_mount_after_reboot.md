---
title: "Hard drive impossible to mount after reboot"
date: 2013-09-15
forum: Hardware
---

### Post by robert14 on 2013-09-15
I have an internal hard drive (SDC1) which is impossible to mount or use after reboot. 

Upon my last reformatting attempt I have run "sudo blkid" with the following result
/dev/sda1: LABEL="Gamez-Steam" UUID="01CE96F0F2E56380" TYPE="ntfs" 
/dev/sda2: LABEL="HOME-WINDOWS7" UUID="01CE96DF95CDF7E0" TYPE="ntfs" 
/dev/sdb1: UUID="9EA1-1FFE" TYPE="vfat" 
/dev/sdb3: UUID="44E0ABEEE0ABE480" TYPE="ntfs" 
/dev/sdb4: UUID="fc53a5ec-63e9-415b-97ec-bdce1da4ddd8" TYPE="ext4" 
/dev/sdb5: UUID="86fab6c8-7db2-4dcb-8894-f5ed73d4d2d8" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="faa6ef04-38c3-46f2-8c49-40fb0142168f" TYPE="swap" 
/dev/sdc1: UUID="76c1a204-c34d-433e-8a0e-f2ec9c11badf" TYPE="ext4"

restart

Booting screen shows two error messages.

Drive is not mountable after getting into GUI.

When i attempt to mount the drive manually I get 'Error mounting system-managed device /dev/sdc1: Command-line `mount "/mnt/76c1a204-c34d-433e-8a0e-f2ec9c11badf"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

My Fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb4 during installation
UUID=fc53a5ec-63e9-415b-97ec-bdce1da4ddd8 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
#UUID=9EA1-1FFE  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sdb5 during installation
UUID=86fab6c8-7db2-4dcb-8894-f5ed73d4d2d8 /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
#UUID=3291cdd2-6d10-4624-9f23-4c845fd75c85 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=9EA1-1FFE    /boot/efi    vfat    defaults    0    1
LABEL=HOME-WINDOWS7 /mnt/HOME-WINDOWS7 auto nosuid,nodev,nofail,x-gvfs-show 0 0

LABEL=Media /mnt/Media auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/eb5bf390-4117-4681-8bb0-ce4be3a0b497 /mnt/eb5bf390-4117-4681-8bb0-ce4be3a0b497 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/76c1a204-c34d-433e-8a0e-f2ec9c11badf /mnt/76c1a204-c34d-433e-8a0e-f2ec9c11badf auto nosuid,nodev,nofail,x-gvfs-show 0 0

Can you help me get the drive to work, mount on startup, for all users?

My ultimate goal is to use this drive for my Home folder. 

Thanks in advance.

---

