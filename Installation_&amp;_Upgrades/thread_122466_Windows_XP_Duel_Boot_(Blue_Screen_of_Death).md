---
title: "Windows XP Duel Boot (Blue Screen of Death)"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by DJeX on 2006-01-27
Ok, I installed Ubuntu today and selected to duel boot with my Windows XP. Ubuntu and Windows Xp are on 2 different hard drives. I booted into Ubuntu fine, it loaded great I did the updates and was very pleased.  Then I wanted to boot into my XP so I restarted and made my selection (Windows XP) on the GRUB boot loader. The Windows XP loading screen come up and proceeded to load with the progress bar. But then a blue screen came up telling me that I should run check disk or unplug any newly installed hard drives. I also tried XP in safe mode but still the same problem.

How do I get my Windows XP Back, I have a lot of important files on the XP hard drive and I need to get into XP.

---

### Post by alex2325 on 2006-01-27
You can write a new Master Boot Record to your Windows XP drive and that will allow you to boot XP successfully.  Unfortunately you won't have access to Ubuntu via the bootloader.  I don't know how to address that issue - unless you can boot the Ubuntu CD and repair the bootloader program.

To write a new Master Boot Record you must have a floppy with the DOS program "FDISK" on it.  I use a Windows 98 boot floppy that has the FDISK program on it.  I believe you can create a boot floppy from another computer (be it Windows 98 or whatever), make sure the FDISK program is on it, boot to that floppy, and perform the following command from the DOS prompt:

fdisk /mbr

This will write a generic bootstrap program to the first sector on your hard drive where the bootloader should be.  It will write over the bootloader program.  And you will boot XP again.  Only you won't be able to boot the other hard drive with Ubuntu on it (as mentioned above).

Forgive me if my explanation is not too technical or could be wrong technically - but I guarantee you this procedure will allow you boot XP again - Been there, done that.

Cedric

---

### Post by Ted D. on 2006-01-27
[QUOTE=DJeX]Ok, I installed Ubuntu today and selected to duel boot with my Windows XP. Ubuntu and Windows Xp are on 2 different hard drives. I booted into Ubuntu fine, it loaded great I did the updates and was very pleased.  Then I wanted to boot into my XP so I restarted and made my selection (Windows XP) on the GRUB boot loader. The Windows XP loading screen come up and proceeded to load with the progress bar. But then a blue screen came up telling me that I should run check disk or unplug any newly installed hard drives. I also tried XP in safe mode but still the same problem.

How do I get my Windows XP Back, I have a lot of important files on the XP hard drive and I need to get into XP.[/QUOTE]
Others may have better solutions but I would follow the instructions at link below:
[http://ubuntuforums.org/archive/index.php/t-76095.html](http://ubuntuforums.org/archive/index.php/t-76095.html)
Then reinstall Ubuntu. I have never had this problem but I have the same set up as you.
However I hope someone has a easier solution.
Ted D.

---

### Post by DJeX on 2006-01-27
Thank You for the replies, I think I'll wait and see if any one else has any other ideas before I try your sugestion.

Also, if I format and reinstall Ubuntu is there a way not to use the GRUB boot loader? maybe use the Windows Boot loader for Ubuntu and Windows?

---

### Post by DJeX on 2006-01-29
Well… I tried your suggestion and no luck. So I’ll let you read my story :mrgreen: :

After hours of Googleing I finally come across someone else who had problems like mine. What I had to do to fix it was change my partition type to 07 (NTFS) which it was set at 44 (Unknown). Then I had to rewrite my boot sector and MBR. Then it finally booted into Windows XP, but this was after 5 hours of research and pulling my hair out. I was all happy I fixed it but then only to find out my backup hard drive was unrecognized. Just by the name Back Up hard drive you can probably guess that it might be the most important drive in my computer and I was pretty pissed to find out it didn’t work. So now after 24 hours of smashing my head off my desk I figure out that all my data on the backup drive is in a lost volume deep within the drive. And now as I type this I have a program trying to recover my information.

Will I ever install Linux again? humm hard to say. I really like Linux but since it has caused me all these problems it makes me think twice before installing it again. 

If anyone has a better way to install it with out destroying the rest of my computer I would love to hear how to do it. Maybe I’ll just get another computer and install on that.

---

### Post by bigken on 2006-01-29
ok boot from your winxp cd when it gets to install windows press r for repair
now your in the console type the number of the win partion and enter admin
password if there is 1 now type fixmbr enter then fixboot enter then exit if this fails go to console again and type bootcfg /rebuild ;)

---

### Post by DJeX on 2006-01-29
> **bigken]ok boot from your winxp cd when it gets to install windows press r for repair
now your in the console type the number of the win partion and enter admin
password if there is 1 now type fixmbr enter then fixboot enter then exit if this fails go to console again and type bootcfg /rebuild  said:**
> 

[QUOTE=DJeX]Then I had to rewrite my boot sector and MBR. 

So then how do you think I managed to do that ^

I must of used the recovery cd 5 times :-P Thanks for the reply though.

---

### Post by BenWilson on 2006-02-01
[http://dausha.net/Technical/WindowsDualBoot](http://dausha.net/Technical/WindowsDualBoot)

May help dual boot without overwriting "native" WinXP MBR.

---

### Post by fakie_flip on 2007-04-22
To get your files back from xp, you can mount the ntfs partition from Linux and copy the files over.

---

