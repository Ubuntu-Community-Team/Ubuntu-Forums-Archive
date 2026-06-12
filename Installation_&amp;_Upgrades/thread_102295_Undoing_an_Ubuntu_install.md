---
title: "Undoing an Ubuntu install"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by Felipejane on 2005-12-11
I'm giving an old PC to a friend who's not technically minded at all. I first suggested putting Ubuntu on it because the price was right, but she was not at all enthusiastic. She's purchased Windows 98 (the machine won't handle XP), and now I need to load it on the hard drive so I can turn this machine over to her. (I know, I know: zillions of reasons why this is terrible, but it has to be this way.)

My problem is that when I put the Win98 CD in the drive and boot the machine, even though it's set to boot from the CDROM first, GRUB starts and it ends up booting Ubuntu before the CD can spin up to full speed. If I stop it I can get to a GRUB> prompt, but I don't know enough Linux command line lingo to tell it to boot from the CD.

Any suggestions for how best to proceed (not including talking the friend into making her peace with Linux)?

---

### Post by aysiu on 2005-12-11
There should be some BIOS setting that will choose to boot from CD instead of the hard drive. You can enter the BIOS settings usually by pressing one of the following keys (Esc, Del, F2), and this occurs before Grub even appears.

---

### Post by codejunkie on 2005-12-11
[quote=Felipejane]I'm giving an old PC to a friend who's not technically minded at all. I first suggested putting Ubuntu on it because the price was right, but she was not at all enthusiastic. She's purchased Windows 98 (the machine won't handle XP), and now I need to load it on the hard drive so I can turn this machine over to her. (I know, I know: zillions of reasons why this is terrible, but it has to be this way.)

My problem is that when I put the Win98 CD in the drive and boot the machine, even though it's set to boot from the CDROM first, GRUB starts and it ends up booting Ubuntu before the CD can spin up to full speed. If I stop it I can get to a GRUB> prompt, but I don't know enough Linux command line lingo to tell it to boot from the CD.

Any suggestions for how best to proceed (not including talking the friend into making her peace with Linux)?[/quote] the windows98 cd is not a bootable cd like XP, you have to have a windows 98 boot floppy instert that first and boot from it. it will have a option to startup computer with cdrom support choose that then insert the windows 98 cd, change directorys to the cd drive that contains the cd for example e:  and type setup.exe that is if you have already partitioned and formated the harddrive first hope this helps.

---

### Post by Felipejane on 2005-12-11
[QUOTE=aysiu]There should be some BIOS setting that will choose to boot from CD instead of the hard drive. You can enter the BIOS settings usually by pressing one of the following keys (Esc, Del, F2), and this occurs before Grub even appears.[/QUOTE]

Indeed there is, and I've done that. But as I said, the CD drive starts to spin, and before it can get up to speed, GRUB takes over and boots Ubuntu.

---

### Post by Felipejane on 2005-12-11
[QUOTE=codejunkie]the windows98 cd is not a bootable cd like XP, you have to have a windows 98 boot floppy instert that first and boot from it. it will have a option to startup computer with cdrom support choose that then insert the windows 98 cd, change directorys to the cd drive that contains the cd for example e:  and type setup.exe that is if you have already partitioned and formated the harddrive first hope this helps.[/QUOTE]

Would that be true even for a Win98 CD that was bought for a new install? A Win98 boot disk would only help if Win98 were already on the hard drive, right? And the only thing that's on the hard drive is Ubuntu. I don't see how a Win98 boot disk could get anywhere.

---

