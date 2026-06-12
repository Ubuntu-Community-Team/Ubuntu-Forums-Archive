---
title: "Grub restore failed on Dell System (please help!)"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by bpont on 2009-01-18
i've just borked my system and could use some help.  i reinstalled grub using an ubuntu livecd and this advice: [http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)  ...essentially, i ran the command to find my existing stage one, which is located at: (hd0,0), then i set my root folder to tell grub where my grub files were located, 'root (hd0,0), lastly, i installed grub to my other hard drive, which contains my xp installation, 'setup (hd1)'  ...everything proceeded without a hitch...no error messages.  then i rebooted and all that was displayed was the word 'GRUB' repeated over and over across my screen, and scrolling down endlessly until i rebooted with the livecd.  what the hell happened??  keep in mind that this is a dell pc, so there is a dell partition located at (hd1,0) or sdb1 and my xp partition is located at (hd1,1)...i don't know if that has anything to do with anything.  anyone know what i could have done wrong??

---

### Post by ajgreeny on 2009-01-18
If you are trying to install grub to the windows MBR, as is normal in a dual boot system you need to use "setup (hd1,1)" or at least I think that is what you need to do.  Give it a try;,it won't matter if you have got it wrong as you can install grub on several partitions without problem, only the one which is your boot partition will be read.

---

### Post by caljohnsmith on 2009-01-18
> **ajgreeny said:**
> If you are trying to install grub to the windows MBR, as is normal in a dual boot system you need to use "setup (hd1,1)" or at least I think that is what you need to do.  Give it a try;,it won't matter if you have got it wrong as you can install grub on several partitions without problem, only the one which is your boot partition will be read.
I would not recommend doing "setup (hd1,1)", or arbitrarily doing "setup (hdX,Y)", because if you install Grub to the boot sector of the Windows partition, the Windows partition will not be mountable, readable, or bootable until you fix the boot sector. I don't think that is what bpont wants. 
[QUOTE=bpont]i've just borked my system and could use some help. i reinstalled grub using an ubuntu livecd and this advice: [http://ubuntuforums.org/showthread.p...highlight=grub](http://ubuntuforums.org/showthread.p...highlight=grub) ...essentially, i ran the command to find my existing stage one, which is located at: (hd0,0), then i set my root folder to tell grub where my grub files were located, 'root (hd0,0), lastly, i installed grub to my other hard drive, which contains my xp installation, 'setup (hd1)' ...everything proceeded without a hitch...no error messages. then i rebooted and all that was displayed was the word 'GRUB' repeated over and over across my screen, and scrolling down endlessly until i rebooted with the livecd. ~what the heck~ happened?? keep in mind that this is a dell pc, so there is a dell partition located at (hd1,0) or sdb1 and my xp partition is located at (hd1,1)...i don't know if that has anything to do with anything. anyone know what i could have done wrong?[/QUOTE]
Unfortunately, the problem is with "setup (hd1)". If you use anything other than (hd0) or (hdX) where X is the same as "root (hdX,Y)", then that tells Grub to look on another drive for its stage1.5 file, but the stage1.5 file is always installed to the same drive as Grub. If you can change your BIOS to boot the Ubuntu drive, I would recommend doing that, and then just install Grub to the MBR of your Ubuntu drive. That way your drives will be independent of each other, so if anything happens to either drive (like even disconnecting it), you should still be able to boot the remaining drive. If you want to give that a try, how about first posting:
```
sudo fdisk -lu
```
And please identify your partitions. If you have no way of booting your Ubuntu drive on start up, it is possible to install Grub to your Windows drive and have it correctly point to the Ubuntu drive for Grub's boot files, so I can help you do that if that is your only option. Let me know what you would like to do, and we can work from there if you want.

---

### Post by bpont on 2009-01-18
Thanks for your quick replies.  I solved the problem by unplugging the first hard drive (the drive that came with the computer and had XP on it) and added that drive to the first position of my controller card and moved my second hard drive (the one I brought over from my previous system...and had Ubuntu installed on) and moved it to the second position of my controller.

I tweaked my bio to set master (of my now driveless mobo) to 'off', then changed hard drive sequence to boot first hard drive (XP) from controller.

I rebooted into livecd, opened a terminal, became root:

```
sudo su
```

then:

```
grub

root (hd1,0)
```

Where my grub files were located

then:

```
setup (hd0)
```

Installed grub bootloader on first hard drive.

Successfully rebooted into XP and Ubuntu.

Thanks for your help and advice!

---

