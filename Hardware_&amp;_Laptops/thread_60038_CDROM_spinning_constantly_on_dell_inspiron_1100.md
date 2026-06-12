---
title: "CDROM spinning constantly on dell inspiron 1100"
date: 2005-08-26
forum: Hardware &amp; Laptops
---

### Post by kubuntuuser on 2005-08-26
Hi 

I have a dell insprion 1100 running hoary with kde3.4.2

This problem has existed ever since i put ubuntu on there.

It seems that the cdrom drive never spins down when a cd/dvd is put into the drive.

I have tried the hdparm command that sends the drive to sleep but this means that a reboot is required when access is required. 

Any help would be appreciated

---

### Post by Lord Illidan on 2005-08-26
Try running Ksysguard from the menu to see if there is a program taking data from the cd..

Show us a screenshot, if possible...

---

### Post by s_p_a_r_k_y on 2005-08-26
can you unmount the drive? or is something accessing it. If you can't unmount it try sudo umount /dev/cdrom -l

which will umount anything : ) but its not recommended if we can just kill the program accessing the drive it should stop spinnning

---

### Post by kubuntuuser on 2005-08-29
Hello again.
Perhaps a better description of the problem might help.

If i insert a cd into the tray, shut the tray and do nothing else the drive will spin forever until the disc is ejected regardless of whether the disk has ever been mounted or not.

KubuntuUser

---

### Post by usacomp2k3 on 2005-09-17
[QUOTE=kubuntuuser]Hello again.
Perhaps a better description of the problem might help.

If i insert a cd into the tray, shut the tray and do nothing else the drive will spin forever until the disc is ejected regardless of whether the disk has ever been mounted or not.

KubuntuUser[/QUOTE]
My 5.04 did that as well, but this is a desktop

---

### Post by Triptol on 2008-04-30
Same problem here. Had it in Gutsy, see it now in Hardy. Still not found a fix.

---

### Post by redseventyseven on 2008-05-01
Same problem here (using Linux Mint XFCE Daryna Beta-008, based on Xubuntu Gutsy).
My temporary workaround solution is to just be more tidy with my cds and dvds and not leave them in the drive when they're not using them!

But seriously, I fear for the life of my poor DVD-drive!

---

