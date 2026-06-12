---
title: "Missing DVD drive in Ubuntu 12.10"
date: 2013-09-09
forum: Hardware
---

### Post by lomitelj on 2013-09-09
[FONT=trebuchet ms]Hi there,

I've been really trying to make my Ubuntu to recognize my laptop's CD / DVD drive but it is still not visible. 

This is what I've tried until now:

- **sudo mount**  and the result was

[/FONT][COLOR=#0000ff]/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/gruby/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=gruby)[/COLOR][FONT=trebuchet ms]

- **sudo mount /dev/sr0 /mnt**  (I've tried this one with a DVD movie, music CD and with an installation CD for Ubuntu)

[/FONT][COLOR=#0000ff]mount: special device /dev/sr0 does not exist[/COLOR][FONT=trebuchet ms]

- [B]ls /dev/disk/by-id
[/B]
[/FONT][COLOR=#0000ff]gruby@Gruby-HP:~$ ls /dev/disk/by-id
ata-Hitachi_HTS542525K9SA00_080228BB0F00WDCLXHLC
ata-Hitachi_HTS542525K9SA00_080228BB0F00WDCLXHLC-part1
ata-Hitachi_HTS542525K9SA00_080228BB0F00WDCLXHLC-part2
ata-Hitachi_HTS542525K9SA00_080228BB0F00WDCLXHLC-part5
scsi-SATA_Hitachi_HTS5425080228BB0F00WDCLXHLC
scsi-SATA_Hitachi_HTS5425080228BB0F00WDCLXHLC-part1
scsi-SATA_Hitachi_HTS5425080228BB0F00WDCLXHLC-part2
scsi-SATA_Hitachi_HTS5425080228BB0F00WDCLXHLC-part5
wwn-0x5000cca539c899ad
wwn-0x5000cca539c899ad-part1
wwn-0x5000cca539c899ad-part2
wwn-0x5000cca539c899ad-part5
gruby@Gruby-HP:~$[/COLOR][FONT=trebuchet ms]

But I can boot my Ubuntu from a CD, that's not an issue.

Where is problem? Why can not I use my CD / DVD?

Thank you for your help in advance.

*PS: I also apologize if I started this topic and it already exists somewhere on the page. If that's the case, then I ask you for a link.*
[/FONT]

---

### Post by lomitelj on 2013-09-12
[FONT=trebuchet ms]Öhm, kann mir da niemand bei den Fragen helfen...? [/FONT]:(

---

