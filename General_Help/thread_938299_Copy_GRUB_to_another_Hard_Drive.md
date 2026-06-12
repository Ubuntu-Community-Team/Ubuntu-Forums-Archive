---
title: "Copy GRUB to another Hard Drive"
date: 2008-10-04
forum: General Help
---

### Post by locorecto on 2008-10-04
Hello my ubufriend. I have an issue that is giving me a lot of problems. I had installed Ubuntu in an external hd because my internal hd is only 40gb. I have XP on the internal hd. I have GRUB dual-booting XP and Ubuntu. The problems is that when I installed Ubuntu, the GRUB file went to the Ubuntu partition in the external hd. Every time I turn on the computer, the external hd have to be on in order to boot or it gives me an error 21 even if I don't want to boot Ubuntu and I don't want that. 

I want to know a way to copy the GRUB file into the internal hd as well as configure it, so I don't have to turn on the external HD to boot XP.

External HD - 500GB with 24GB for Ubuntu and 1GB for Swap
Internal HD - 40GB with XP.

Thanks in advance.

---

### Post by Trevster on 2008-10-04
I have used [supergrubdisk]("http://www.supergrubdisk.org/") to do this awhile ago. It can install grub on the internal disk for you. You then would select that as your boot hardrive.

I am sure there are command line ways of doing this but I can't help you with that.

---

### Post by Herman on 2008-10-04
[How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").-  contains only GRUB, no other files  are required.

---

### Post by caljohnsmith on 2008-10-04
[QUOTE=locorecto]I want to know a way to copy the GRUB file into the internal hd as well as configure it, so I don't have to turn on the external HD to boot XP.[/QUOTE]
Actually, I don't think you need to install Grub to your Windows drive to do what you want; that's assuming your BIOS will allow you to boot from your external Ubuntu drive on start up--is that true? If it is, all you have to do is make sure your Windows drive has a Windows MBR (Master Boot Record), so that when your external drive is off or disconnected, your BIOS can boot the Windows drive no problem and without using Grub. It sounds like the problem is that Grub got installed to the MBR (Master Boot Record) of your Windows drive at some point, so when you try to boot the Windows drive with the external drive disconnected/off, you get a Grub error. 

If you want to restore the Windows MBR to the Windows drive, just boot your Windows Install CD, press "r" at the first main menu to get the recovery console, and run:
```
fixmbr
```
If I understand your problem correctly, that's all it should take to boot the Windows drive when the Ubuntu drive is disconnected/off. But it also sounds like your Ubuntu drive may not have Grub in the MBR, or Grub's menu may not be configured for booting from the Ubuntu drive; so if you have problems with that, let me know. Otherwise let me know how it goes.

---

### Post by louieb on 2008-10-04
> **Herman said:**
> [How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").-  contains only GRUB, no other files  are required.

+1 I've used Herman's  how to. Just make a small partition on the hard drive. Copy the grub files from /boot/grub to it. Do a little modification to the menu.lst file.  Then set up the hard drive to boot to GRUB on the hard drive.  Herman has a good expatiation of doing all that on his site.

---

