---
title: "Dual boot, Windows XP/Ubuntu 7.10"
date: 2008-11-01
forum: General Help
---

### Post by gilloz on 2008-11-01
Hello: First of all, I hope I am not in the wrong forum to ask this. Well, I went and did it this time. My present configuration is dual boot with Ubuntu and Windows XP Pro. Drive C is 80GB and only has Windows XP Pro w/SP3, Drive D is also 80GB and half has Ubuntu 7.10. Windows XP Pro crashed and burned this morning and with all the procedures from Microsoft and different forums, I am unable to boot in Windows XP. My failure is that my system32/config is missing or corrupted. I also tried Repair using my Windows CD to no avail. Like I said, I tried everything. So, I am ready to do a clean install of Windows. Here is my question, what will I have to do, if anything, to get my boot menu back to select either Windows or Ubuntu after the clean install of Windows XP Pro? I haven't started as yet until I get some info, comments or whatever. Thanks guys.
    BTW, this configuration has been working for about 1.5 years with no problems.

---

### Post by logos34 on 2008-11-01
If windows overwrites Grub bootloader, simply reinstall grub from the live cd (see link my sig)

---

### Post by TeXtonyx on 2008-11-01
I dual boot XP and Ubuntu also. I installed Ubuntu to the /boot
partition during Step 7, Advanced, from the live cd. 

The reason is that if the XP partition fails, it does not impact
the booting of Ubuntu. If the Ubuntu partition is installed to the 
MBR and that partition fails then you lose both XP and Ubuntu. The
Ubuntu partition can still be booted with Super Grub disk.

Installing Linux to the MBR writes to the Windows boot sector. I
see no less than 50 problems a month on this forum related to :
'I uninstalled Ubuntu and I can't boot Windows. The Ubuntu partition
failed (it has grub boot files on it) so I can't boot Windows anymore.'
Quite a few have laptops which come with a Recovery cd and *not* 
the Windows install cd needed to fixmbr. Yet another problem. 

*In a Windows/Linux dual boot system* it is always better to keep
both OS separated as much as possible so that if one fails, both
don't fail. This makes it easier for troubleshooting too. I see
*hours* of diagnosis spent on grub's menu.lst to see if it is at
fault for XP not booting. When the OS's are installed independent
of each other's booting, you know right away whether the problem
is Windows is corrupted or whether grub's menu.lst is wrongfully
configured. You've apparently already figured that out, but there
are a few hundred posters a year on this forum that don't know
where the problem rests. 

One needs to copy the first 512 bytes of the Ubuntu boot sector
to the Windows root partition and then add it to boot.ini options. (dd)
Or one can use free Bootpart which functionally accomplishes much
the same thing, only automatically. If and when people graduate
to using Ubuntu only, so that they delete Windows, it's a piece 
of cake for them to reinstall grub to the MBR, whereas to the
average newcomer to dual booting Windows/Ubuntu, and that is 60%
of all Ubuntu users, figuring out how to configure grub takes
pages of posts reporting experimental results to an advice giver.
Why make the learning curve steeper? Windows users new to Ubuntu
have enough to do learning how install their nVidia drivers and
making Flash work.

---

