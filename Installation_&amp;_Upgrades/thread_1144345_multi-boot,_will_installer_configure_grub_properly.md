---
title: "multi-boot, will installer configure grub properly?"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by itzfritz on 2009-04-30
I would like to install Ubuntu on an empty partition on a machine having both Vista 64bit and Windows 7 installed on it (single drive).
I understand that Ubuntu will configure grub on the mbr to properly boot an existing Windows installation; will it configure grub properly to boot *both* versions of Windows?

The answer is likely 'yes', but having invested so much time in this already I would be devastated if it broke...

Thanks!

---

### Post by Herman on 2009-04-30
No, probably Ubuntu's GRUB will only boot one of your Windows installations by chainloading your Windows bootloader, (BCD).  
But then from there you should be able to boot the other Windows installation from your BCD menu.

I'm only guessing, I haven't tried dual booting Windows Vista with Windows7, although I have tried Ubuntu with both of them separately.
I'm guessing if you installed Vista first, your Windows7 doesn't have any of it's own boot loader files.

GRUB does not boot Windows, it only chainloads Windows boot loader at the boot sector of a Windows partition, and Windows' own boot loader then can boot Windows.

Windows has a strange way of setting up a Windows-Windows dual boot, and normally one Windows operating system will give up its boot loader files to any existing Windows installation that has been previously existing in a hard disk.

That means there is no way for GRUB to boot whichever Windows you installed second, because probably it has no boot loader in it to boot with, but depends on the earlier Windows for the boot loader files.

Does each of your Windows installations contain boot loader files? 
Or only Vista? 

If I'm right, you can only boot Windows7 via Vista's boot loader.
As long as you keep Vista everything will be okay. :)

---

### Post by Herman on 2009-04-30
That's a bug built into Windows, not in Ubuntu or GRUB.  :)

---

### Post by itzfritz on 2009-05-02
In your opinion, will it be possible to configure grub after-the-fact to boot all three operating systems?  Or will the fact that "Windows7 doesn't have any of it's own boot loader files" make this impossible?

---

### Post by Herman on 2009-05-02
Well, check for yourself and see if it's true that Windows7 doesn't have its own boot loader, but I'm guessing probably it doesn't.

If that's so then there is no chance of getting it to boot directly from GRUB as it is now.
 
As far as I know, the only way to stop Windows Vista and Windows 7 from doing that (setting up a 'Microsoft Default Dual Boot'), is to install one OS to one hard disk and unplug that hard disk and then install the other OS to another hard disk. Then plug both hard disks in later and use GRUB or some other third party loader to choose between OSes at boot time.
With earlier versions of Windows is was possible to use a partition editor or GRUB boot loader to 'hide' and 'unhide' Windows partitions from each other to prevent that kind of undesirable behavior.
Further reading - [Understanding MultiBooting and Booting Windows from an Extended Partition]("http://www.goodells.net/multiboot/index.htm") - Dan Goodell.

I have read about people copying boot loader files from one Windows installation to another and reconfiguring them so they'll work.

There may be legal issues to consider before you go copying and pasting bits and pieces of a proprietary operating system around. I think I remember some clause in Microsoft's EULA that you probably agreed to that says you're not supposed to dis-assemble the software or something like that.
But on the other hand, Microsoft themselves advise people with boot loader problems in Windows XP to copy NTLDR, NTdetect.com and boot.ini from another computer to a floppy disc and use it to boot the disabled PC. There's a KB article about that, so I'm not sure. It seems like it's okay sometimes but maybe not all the time, or maybe it depends the circumstances or on how good your lawyer is, if Microsoft finds out and if they care.
I'm reluctant to advise you to copy Windows7 or Vista's boot loader although I do sometimes tell people they can copy the Windows XP loader because Microsoft already tells people they can. The rules for Windows Vista and Windows 7 could be stricter, I'm not sure. Maybe you should just check with Microsoft before you decide what to do.

An advantage in using Open Source operating systems and programs is we're free to do what we like without having to worry about being sued, but with proprietary software there are a lot of strings attached.

---

### Post by meierfra. on 2009-05-03
The same boot loader is  included on the Window 7 DVD,  so  I cannot believe there are any legal issues.
Also there are Vista recovery disks available on the EasyBCD and PCWorld website, which can be used to install the boot loader. So if it is legal to download the boot loader for free from a web site, I don't see any way how it could be illegal to copy  the boot loader from the Vista partition to the Win7  partition. 

I wrote  up a  HowTO earlier today which got accepted in the "Tutorials and  Tips" section:

 [URL="http://ubuntuforums.org/showthread.php?t=1146266"]HowTo: Boot Vista and Windows 7 directly from the Grub menu
[/URL]

If you are  concerned about copying the boot loader from the Vista to the Windows 7 partition, you can follows this [tutorial]("http://ubuntuforums.org/showthread.php?t=813628#4")  and use the Windows 7 DVD to install a boot loader onto the Win 7 partition.

---

### Post by meierfra. on 2009-05-03
[QUOTE=Herman]As far as I know, the only way to stop Windows Vista and Windows 7 from doing that (setting up a 'Microsoft Default Dual Boot'),[/QUOTE]

Actually one could  use "fdisk" to temporarily erase the Vista entry in the partition table, and  restore the partitions table after Windows 7 was installed.  That would even be faster than  installing a boot loader for Win 7.

But I usually don't recommend messing with the partitions table, if it can be avoided. And it would only work if Windows 7 is on a primary partition.

---

