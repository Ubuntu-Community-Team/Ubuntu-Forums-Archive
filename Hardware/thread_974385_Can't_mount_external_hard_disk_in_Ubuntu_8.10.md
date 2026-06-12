---
title: "Can't mount external hard disk in Ubuntu 8.10"
date: 2008-11-07
forum: Hardware
---

### Post by commbba on 2008-11-07
Hello , there.Please help me at the following problem.
Recently I upgraded from 8.04 to 8.10 and I found out that the two (2) external hard drives those I was using in 8.04 can't be mounted , neither as root as I was mounted them so long.The ''fstab'' added lines for these two drives are:

UUID=F2D8C898D8C85D0B /media/wd ntfs-3g uid=1000,gid=1000,rw,force,noauto,locale=el_GR.utf8 00

UUID=40D02C04D02C02B0 /media/seagate/ ntfs-3g uid=1000,gid=1000,rw,force,noauto,locale=el_GR.utf8 00

and as I mentioned above I could mount them only as root.Now I'm seeing only two icons in the taskbar but when I press them answers me that I don't have the privileges to mount the volume.

---

### Post by cariboo on 2008-11-07
Nautilus has changed a bit concerning mounting drives. If yoo drives are listed in Palces-->Home Folder, just double click the drive in the left pane and it should ask you for a your password, I just click the option to permanently remember my password.

I don't like any icons on my desktop so I just mount the disks as needed.

Jim

---

### Post by commbba on 2008-11-07
No , unfortunately this didn't worked for me.Nothing changed double clicking upon the icon in the left pane.It shows a locker and reminds me that I don't have the privilege to mount this volume.

---

### Post by commbba on 2008-11-13
Problem solved.
I'm installing the disks manually by konsole with sudo mount command.
For example sudo mount /media/wd or media/seagate/.
For unistall I enter nautilus as root in konsole by typing sudo nautilus and I'm unmounting the disks by there.The sudo unmount command does not work.

---

