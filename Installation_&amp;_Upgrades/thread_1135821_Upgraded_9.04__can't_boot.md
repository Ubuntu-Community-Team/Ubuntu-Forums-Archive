---
title: "Upgraded 9.04  can't boot"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by frevh on 2009-04-24
[COLOR="Red"]Upgraded 9.04  can't boot[/COLOR]


the upgrade went very easely onlin like i did with previous 2 versions without big problems
but this time ;
Bug Int 14 CR2 ffffb0f0
Edi 0000000...
Eby 000000046
errr 000000...
Stack c011a26e...

can work with linux old = 8.10

foud some explanation : it seems to be a regression ... I really don't understand this and what can I do ?
thanks
Fre

can tis help ?
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       lvm2pv
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: onbekende bestandssysteemsoort 'lvm2pv'

sda3: _________________________________________________________________________

    File system:       lvm2pv
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: onbekende bestandssysteemsoort 'lvm2pv'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 250.0 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders, totaal 488397168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x000f2386

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     2,923,829     2,923,767  82 Linux swap / Solaris
/dev/sda2    *      2,923,830    32,226,389    29,302,560  8e Linux LVM
/dev/sda3          32,226,390   488,392,064   456,165,675  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7fa80d9e-73a3-4135-a925-f857eb9d4f9a" TYPE="swap" 
/dev/sda2: UUID="2eif6K-1Zdg-mnJf-1ch8-9TCP-e4Ub-RPkN0X" TYPE="lvm2pv" 
/dev/sda3: UUID="o3VNpP-ijqV-afFY-BWfK-fS4j-zg1W-MIyJ9W" TYPE="lvm2pv" 
/dev/mapper/lvmdata-root: UUID="a55ecdc0-6d70-445b-99e5-2677832e0b5b" TYPE="ext3" 
/dev/mapper/lvmhome-home: UUID="1379887b-6816-4823-a8ce-fda673fa407d" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/mapper/lvmdata-root on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/mapper/lvmhome-home on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fvh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fvh)

=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by meierfra. on 2009-04-24
> can you folow me on this new thread?

Well, I followed you to the new thread, but I'm afraid I won't be able to assist you. The error messages might be caused by a bug in the new kernel, but I don't really know. 
The boot_info_script is not able to read LVM partitions, so  RESULTS.txt  only provided very limited information.

I don't have any experience with LVM, so I can only hope that someone with experience in LVM can give you some  advice.

---

### Post by frevh on 2009-04-24
thanks for trying...

i learned to work a bit in this forum i'll do better..

---

### Post by frevh on 2009-04-24
> **meierfra. said:**
> Well, I followed you to the new thread, but I'm afraid I won't be able to assist you. The error messages might be caused by a bug in the new kernel, but I don't really know. 
The boot_info_script is not able to read LVM partitions, so  RESULTS.txt  only provided very limited information.

I don't have any experience with LVM, so I can only hope that someone with experience in LVM can give you some  advice.

fine to have been followd-up ...
thanks

---

