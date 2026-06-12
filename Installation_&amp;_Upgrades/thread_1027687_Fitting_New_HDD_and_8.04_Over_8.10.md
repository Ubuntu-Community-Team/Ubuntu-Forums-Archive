---
title: "Fitting New HDD and 8.04 Over 8.10"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by Cheemag on 2009-01-01
Hello.

I have installed 8.10 on a smallish drive.

I now want to fit a brand new larger drive while retaining the drive I have. Machine will have two HDDs.

However, I want to install 8.04 rather than 8.10

The ISO I downloaded looks suspiciously like a Windows CD when burned. I don't have Windows on the machine I'm upgrading, only Ubuntu 8.10. Ideally I'd want to wipe 8.10 and install 8.04 to boot from the larger of the two discs (which will presumably not be formatted ?)

How do I proceed?

---

### Post by logos34 on 2009-01-01
> **Cheemag said:**
> 
The ISO I downloaded l**ooks suspiciously like a Windows CD** when burned. I don't have Windows on the machine I'm upgrading, only Ubuntu 8.10. Ideally I'd want to wipe 8.10 and install 8.04 to boot from the larger of the two discs (which will presumably not be formatted ?)


huh?  shouldn't look anything like a windows cd when you boot from it (unless you're talking about the programs preview when you open it on the desktop)

Just boot it and tell it to install to the larger drive...Use Guided--use largest continuous free space, or if that doesn't choose the right disk, select 'manual' partitioning and make a / and swap

---

### Post by Cheemag on 2009-01-01
> **logos34 said:**
> huh?  shouldn't look anything like a windows cd when you boot from it (unless you're talking about the programs preview when you open it on the desktop)

Just boot it and tell it to install to the larger drive...Use Guided--use largest continuous free space, or if that doesn't choose the right disk, select 'manual' partitioning and make a / and swap

I was looking at the disc on an XP machine. It looks very Windows. Probably a distro able to do a "live" or demo version of the distro on a Windows machine without installing.

So... I install Ubuntu on the larger drive and make the smaller drive a swap partition?

---

### Post by logos34 on 2009-01-01
> **Cheemag said:**
> I was looking at the disc on an XP machine. It looks very Windows. Probably a distro able to do a "live" or demo version of the distro on a Windows machine without installing.

So... I install Ubuntu on the larger drive and make the smaller drive a swap partition?

Still not sure what you mean by 'very windows'...Granted, Ubuntu Gnome or KDE IS a gui (desktop) with window manager and all, and it can even run many windows apps via Wine tolerably welll--they even look exactly the same as they do in windows--but beyond that it's rather different (i.e. infinitely BETTER).

Yes, you can if you want put the /swap on another hard disk.  But if you have  a gig+ of ram chances are you won't use it much, since linux has a much lighter footprint.

---

### Post by Cheemag on 2009-01-02
> **logos34 said:**
> Still not sure what you mean by 'very windows'...Granted, Ubuntu Gnome or KDE IS a gui (desktop) with window manager and all, and it can even run many windows apps via Wine tolerably welll--they even look exactly the same as they do in windows--but beyond that it's rather different (i.e. infinitely BETTER).

Yes, you can if you want put the /swap on another hard disk.  But if you have  a gig+ of ram chances are you won't use it much, since linux has a much lighter footprint.

This looks distinctly Windows:

Volume in drive G is Ubuntu 8.04.1 i3
 Volume Serial Number is A40D-39EA

 Directory of G:\

02/07/08  10:47    <DIR>          .disk
02/07/08  10:47    <DIR>          casper
02/07/08  10:47    <DIR>          dists
02/07/08  10:47    <DIR>          install
02/07/08  10:47    <DIR>          isolinux
02/07/08  10:47    <DIR>          pics
02/07/08  10:47    <DIR>          pool
02/07/08  10:47    <DIR>          preseed
02/07/08  10:47                40 autorun.inf
02/07/08  10:47             5,512 md5sum.txt
02/07/08  10:47               223 readme.diskdefines
02/07/08  10:47                 0 ubuntu
01/07/08  14:08           199,520 umenu.exe
30/06/08  15:33         1,083,932 wubi.exe
               6 File(s)      1,289,227 bytes
               8 Dir(s)               0 bytes free

But I expect it will run on the Ubuntu machine. In any case it's
pretty much the same as the 8.10 disc.

Thanks. New hardware hasn't arrived as yet so no further progress
to report.

---

