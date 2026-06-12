---
title: "Boot order resets if external drive isn't powered on"
date: 2014-10-09
forum: Hardware
---

### Post by qyot27 on 2014-10-09
I recently installed a SATA host card with eSATA ports (Vantec UGT-ST310R), and yesterday I migrated the content of my Ubuntu partitions from my main drive to the larger partitions on the drive in my eSATA enclosure.

I have no problems actually booting Ubuntu from the external drive.  That's not the problem.

In my BIOS (Phoenix LTD 6.00, 10/17/2001), I can adjust the boot order so it looks like this:
```
-Hard Drives
    Bootable Add-in Cards
    [External SATA drive with Ubuntu]
    [Internal IDE/PATA with Windows]
```

And this works fine and does everything I'm used to.  So long as the external is powered on before POST.

If, however, I don't turn the external on first, it won't find the SATA drive, and just go ahead and boot Windows (as expected).  But regardless of whether I turn the external on while booted into Windows (as the external also has a 72 GB NTFS partition on it for extra storage), or if I shut down and decide to turn the external on first the *next* time I boot, the BIOS will not find it, because not seeing it before POST the *last* time reset the boot order to this:
```
-Hard Drives
    Bootable Add-in Cards
    [Internal IDE/PATA drive with Windows]
    [External SATA drive with Ubuntu]
```

So I have to go back into the BIOS and put the drives back in the proper boot order again, after just *one* time choosing not to bother to power on the external first.


Has anyone else experienced something like this?  Is this normal behavior when a bootable external drive can't be found before POST?  Unfortunately, there's nothing I can do in the way of BIOS updates, as there weren't any provided through the manufacturer. It's an old [Trigem Anaheim-3](http://www.motherboards.org/mobot/motherboards_d/Trigem/Anaheim%2B3/) board; neither eMachines (it's an eMachines T1110) nor Trigem had available updates for the board on their sites (which is kind of to be expected; the core of the computer is from 2001).

---

### Post by sudodus on 2014-10-09
It seems to me that you have checked the options of the BIOS thoroughly, and it works like that. I think several BIOS systems work like that. A solution would be to put a grub bootloader and a small /boot partition in the internal drive, where you can select between Windows and Ubuntu. (You can make Windows the default boot option, so that it will boot properly also without your external drive.)

---

