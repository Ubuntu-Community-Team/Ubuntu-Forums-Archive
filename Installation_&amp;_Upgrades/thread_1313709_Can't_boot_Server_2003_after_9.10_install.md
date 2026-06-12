---
title: "Can't boot Server 2003 after 9.10 install"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by justjustin on 2009-11-04
I can't boot into Windows Server 2003 after installing 9.10. 2003 has been running quite a while and there were no problems dual-booting with my old 9.04 install.

Grub loads Windows Bootloader fine but I just get a black screen after that and nothing happens. I'm getting to grasps with grub2 right now, but grub2 seems to be loading ntldr, just not windows, so not sure what to do. 

desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a0a33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21672   174080308+   7  HPFS/NTFS
/dev/sda2           21673       23967    18434587+  83  Linux
/dev/sda3           23968       30019    48612690   83  Linux
/dev/sda4           30020       30401     3068415   82  Linux swap / Solaris


/boot/grub/grub.cfg - windows entry

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 3690cefa68cc9651
	drivemap -s (hd0) ${root}
	chainloader +1

Just to add, I installed over my old partitions, using the installer to format them, sda2 is mounted at / and sda3 is my home. 

Any help is much appreciated as i really do need server for educational purposes and use ubuntu for everything else.

Thanks in advance
Justin

---

### Post by justjustin on 2009-11-04
Problem solved... sort of, 
Windows won't get past NtLoader if External Usb Hdd is connected at boot-time. Not a major problem, more of an inconvenience

Has anyone else experienced this or is it a known problem with 9.10? Hard to search for threads, just get lots of results regarding installs on external Hdd's. Will keep looking

---

