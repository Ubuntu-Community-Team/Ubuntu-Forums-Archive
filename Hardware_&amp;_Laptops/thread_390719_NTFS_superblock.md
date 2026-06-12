---
title: "NTFS superblock"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by laurensH on 2007-03-22
hello,

first, the general situation. i had an XP/Ubuntu dual boot machine that worked perfectly fine. I wanted to really switch to Linux, and decided to resize my XP partition, so i could create FAT32 partitions for all my media files and documents. in the end, i wanted to keep the windows-installation as well (you never know when it might come in handy).
however, during the partitioning (with Partition Magic), it blocked at about 30 percent. I had to do a hard reboot, and when i tried to load the XP partition in Grub, it automatically rebooted after a few seconds.
i still had ubuntu left, and i, foolishly, decided to mess around with TestDrive. this program suggested to change the number of cylinders per head (?), i did so, and as a result, i got a grub error.
when i loaded ubuntu from the LiveCD, i saw the entire linux partition was gone. i urgently needed my computer for university, so i decided to reinstall linux in the "unallocated space" that used to be my / en /home partitions.
i'm currently running Kubuntu, which works fine, but i can't load my NTFS partition. i'd really like it back, because my e-mail address book is on there (this was lost on the ubuntu-install that i lost, i have a outdated version on my windows-partition), as well as music, video, documents, etc... the most important stuff is backed up, but i'd really like it all back :-).

when i run sudo fdisk -l the output is:

Schijf /dev/hda: 100.0 GB, 100030242816 bytes
255 koppen, 63 sectoren/spoor, 12161 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1   *           1       10785    86630481    7  HPFS/NTFS
/dev/hda2           10786       11550     6144862+  83  Linux
/dev/hda3           11551       11648      787185   82  Linux-swap / Solaris
/dev/hda4           11649       12161     4120672+  83  Linux

when i try to mount the ntfs partition, this is the output:

laurens@laurens-laptop:~$ sudo mkdir /media/windows
Password:
laurens@laurens-laptop:~$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=ut       f8,umask=0222
mount: slecht soort bestandssysteem, slechte optie, slecht superblok op /dev/hda       1, ontbrekende codepagina of andere fout
In sommige gevallen wordt er nuttige informatie gevonden in syslog
- probeer dmesg | tail ofzo

[translation:
mount: bad type of filesystem, bad option, bad superblock on /dev/hda/1, missing codepage or other error
in some cases usefull information can be found in syslog - try dmesg | tail]

when I enter dmesg | tail this is the output:

[17189873.168000] Unknown OutputIN= OUT=tun0 SRC=157.193.2.232 DST=157.193.40.42 LEN=59 TOS=0x00 PREC=0x00 TTL=64 ID=10628 DF PROTO=UDP SPT=32946 DPT=53 LEN=39
[17189873.168000] Unknown OutputIN= OUT=tun0 SRC=157.193.2.232 DST=157.193.71.1 LEN=59 TOS=0x00 PREC=0x00 TTL=64 ID=10628 DF PROTO=UDP SPT=32946 DPT=53 LEN=39
[17189873.168000] Unknown OutputIN= OUT=tun0 SRC=157.193.2.232 DST=157.193.40.42 LEN=59 TOS=0x00 PREC=0x00 TTL=64 ID=10628 DF PROTO=UDP SPT=32946 DPT=53 LEN=39
[17189873.168000] Unknown OutputIN= OUT=tun0 SRC=157.193.2.232 DST=157.193.71.1 LEN=59 TOS=0x00 PREC=0x00 TTL=64 ID=10628 DF PROTO=UDP SPT=32946 DPT=53 LEN=39
[17189873.168000] Unknown OutputIN= OUT=tun0 SRC=157.193.2.232 DST=157.193.40.42 LEN=59 TOS=0x00 PREC=0x00 TTL=64 ID=10628 DF PROTO=UDP SPT=32946 DPT=53 LEN=39
[17189873.168000] Unknown OutputIN= OUT=tun0 SRC=157.193.2.232 DST=157.193.71.1 LEN=59 TOS=0x00 PREC=0x00 TTL=64 ID=10628 DF PROTO=UDP SPT=32946 DPT=53 LEN=39
[17189873.168000] Unknown OutputIN= OUT=tun0 SRC=157.193.2.232 DST=157.193.40.42 LEN=59 TOS=0x00 PREC=0x00 TTL=64 ID=10628 DF PROTO=UDP SPT=32946 DPT=53 LEN=39
[17189873.168000] Unknown OutputIN= OUT=tun0 SRC=157.193.2.232 DST=157.193.71.1 LEN=59 TOS=0x00 PREC=0x00 TTL=64 ID=10628 DF PROTO=UDP SPT=32946 DPT=53 LEN=39
[17191129.528000] NTFS-fs error (device hda1): load_system_files(): Failed to load $Bitmap.
[17191129.528000] NTFS-fs error (device hda1): ntfs_fill_super(): Failed to load system files.


Can someone please help me recover my data? i don't need windows to work again, I just want the 'My Documents' folder back...
Any help would be greatly appreciated, I've read through the forum, but I can't seem to find a solution. I'm a complete newbie, so it could be something stupid I'm forgetting or doing wrong...

thanks!

grtz

laurens

---

