---
title: "[SOLVED] Stop at grub page after installation in a USB HDD"
date: 2008-10-19
forum: General Help
---

### Post by peril62 on 2008-10-19
I am absolute beginer in Linux. Only slight knowledge of MS-DOS. Running W XP in my HD, have installed wubi through it in an external USB HDD following instructions. Seems installation downloaded entirely and worked OK as now get boot options of XP or Ubuntu. No problem booting XP. However when selecting Ubuntu I get stopped at a black page with the grub> prompt instead of completing the procedure to get to username and graphic desktop and things working.

Have pressed Insert after the boot as suggested by respondants to similar threads and got the following:

Booting GRLDR…
Get upper memory…
hard drives:1, int13: F0007381, int15: F000F859
get_diskinfo(80), int13/41(80), version=AA210005, int13/48(80), err=0,
C/H/S=16383/16/63, Sector Count/Size=234375000/0, int13/08(80),
version=0, C/H/S=1023/255/63, int13/02(80), err=0, LBA, C/H/S=16383/255/63, Sector Count/Size=263192895/512
boot drive=80, int13/4B01(80), err=1, drive=80, Not CD
get_cdinfo(7F), int13/4B01(7F), err=1, drive=7F, cdrom_drive==FFFFFFFF.
Starting cmain()…Open /default…failure.

End of menu init commands. Press any key to enter command-line or run menu

Obviously my Dell does not allow boot from a USB-HDD and I do not know if this could be the problem but in principle the first part seems to work (OS option menu). I have no intention to install Ubuntu in my current XP HD but have read in other forums that with wubi I could install Ubuntu in an external USB-HDD and make it work to have a try and this is what I have done but does not work. 

My system:
Dell Dimension 8300 p4, 3,2Ghz, 1gb ram
HD NFTS 111Gb
USB-HDD FAT 32 186 Gb

Have no idea of what should I do next. Any help would be welcome but please consider I know nothing of Linux or Ubuntu.

Thank you.

---

### Post by ago on 2008-10-20
Yes it might be that grub4dos cannot access your drive. You should ask in the grub4dos forum for a definitive answer.

---

### Post by peril62 on 2008-10-21
Now solved. Have connected USB HDD trough a direct USB 2.0 root in PC rather than through USB in display screen (considered external and apparently not recognised) but although advanced from grub screen to busybox screen still did not work as stalled there. Then installed new Ubuntu 8.10 trough wubi again rather than previous 8.04 and now everything works fine.

---

