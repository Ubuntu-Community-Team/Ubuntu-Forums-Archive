---
title: "Tri-Boot Vista-Win7-Ubuntu 9.04"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by NickArcifa on 2009-08-09
Hi Guys,

I Currentley have a laptop running Windows Vista. The hardrive is partitoned already with a recovery partition. I Have Installed Windows 7 Beta on my computer on another partition. I tried to install ubuntu on a new partition, it went smoothly, but grub came up with 2 vista boot options that both lead to my recovery partition. I then managed to get rid of ubuntu. which then gave me a grub error. fixed that with a system restore via recovery partition. How can i tri boot vista, windows 7 and ubuntu 9.04 and have them all bootable via GRUB or windows boot manager. Vista must be on my computer first as i do not have installation discs only the recovery partiton. 

Thanks in advance,
Nick Arcifa

---

### Post by presence1960 on 2009-08-09
you didn't have to remove Ubuntu. All you needed to do was edit the Windows entries in menu.lst so they point to the correct partitions. Reinstall Ubuntu and post back here for help to get your Windows entries booting from GRUB.

You also didn't need to restore your system to get vista to boot. You have a recovery partition so you don't have access to recovery console. You can download this [CD]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and can use that to restore Vista's bootloader instead of restoring your machine which wipes everything off your hard disk. Boot from the CD and follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Vista.

You could have saved yourself a lot of work if you posted here prior to restoring your vista.

---

### Post by NickArcifa on 2009-08-10
Okey Dokey,

Reinstalled Ubuntu :)

Just need help getting the menu.lst or whatever pointing to the right spot..

I didn't reinstall vista, just restored it to before ubuntu installation, which got rid of it but kept vista. this also fixed the MBR to not show up GRUB

Didn't really involve a lot of work, just a lot of swearing.. me realiseing that i couldn't access windows!

Ok did some more research 
Vista is on /dev/sda1
Recovery is on /dev/sda2
Windows 7 is on /dev/sda3
Ubuntu is on /dev/sda4

Im not sure how this helps, but thats what they showed up as when i opened up GParted

How do i fix my grub now?

cheers,
Nick Arcifa

---

### Post by presence1960 on 2009-08-10
open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

scroll down to the bottom to your windows entries. Don't be alarmed if you have 2 or 3 Vista entries there. Windows 7 shows as Vista also. Try editing and/or adding these 3 entries:

```
title          Microsoft Windows Vista
rootnoverify   (hd0,0)
chainloader     +1
```

```
title          Microsoft Windows 7 RC
rootnoverify   (hd0,2)
chainloader    +1
```

```
title          Vista Recovery
rootnoverify   (hd0,1)
chainloader    +1

```

Because of the way windows works when having more than one windows version installed either Vista or win 7 entry might not work. But if that is the case when you choose the other your windows boot.ini will give you a choice between both versions. if this happens just remove the entry of the version that doesn't work from menu.lst

P.S. I just noticed you said you need GRUB to be restored. Do this first, then follow the above instructions:

> 1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,3)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,3)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by NickArcifa on 2009-08-11
Hey Presence,, i followed your things but got a error for windows 7, error 13 i beleive, then later it changed to BOOTMGR missing, press ctrl alt delete to restart. So i deleted the Windows 7 entry from the menu.lst, Vista works well though. Vista comes up with the Boot Manager which i can then boot into Vista or Windows 7 fine. it is not ideal but it works. thanks anyway. 

Nick Arcifa

---

### Post by NickArcifa on 2009-08-11
When say 9.10 of ubuntu comes out, will this screw up my menu.lst. is their anyway to upgrade the distro from a bootable live cd of 9.10 if i get it or would i have to download of the web through synaptic or upgrade manager to upgrade the system.

 Also if you have the time, what is the difference between a primary and an extended / logical partition?

Cheers Again,
Nick Arcifa

---

### Post by merlinus on 2009-08-11
There is a limit of 4 primary partitions per hdd, and windows needs to be on one.  An extended partition can contain numerous logical partitions, however, so it is always useful to create one for future flexibility.  Linux lives happily on a logical.

In your case, for example, it seems the limit of 4 primaries is already used up.

In terms of operation, there is no difference between primaries and logicals.

---

### Post by presence1960 on 2009-08-11
> **NickArcifa said:**
> Hey Presence,, i followed your things but got a error for windows 7, error 13 i beleive, then later it changed to BOOTMGR missing, press ctrl alt delete to restart. So i deleted the Windows 7 entry from the menu.lst, Vista works well though. Vista comes up with the Boot Manager which i can then boot into Vista or Windows 7 fine. it is not ideal but it works. thanks anyway. 

Nick Arcifa

Unfortunately that is how windows works when you have more than one version installed on a machine. One version takes over booting for both versions by giving you a menu to choose. I didn't know which one would take over so I gave you the entries to add to menu.lst for all of them. That is a microsoft quirk, contact Redmond, WA to complain. Glad you got it working.

---

### Post by presence1960 on 2009-08-11
> **NickArcifa said:**
> 

 Also if you have the time, what is the difference between a primary and an extended / logical partition?

Cheers Again,
Nick Arcifa

check [this]("https://help.ubuntu.com/community/HowtoPartition") out.

---

### Post by NickArcifa on 2009-08-11
:)meh thanks presence

Screw complaining to microsoft,, like trying to win an unwinnable battle 

Cheers again,
Nick Arcifa

---

### Post by Mark Phelps on 2009-08-12
> **NickArcifa said:**
> When say 9.10 of ubuntu comes out, will this screw up my menu.lst. 

Yes, it might.  I've had some upgrades that overwrote the menu.lst and removed my custom entries; I've had others that simply updated it.

Best thing to do is make a backup copy of the menu.lst file before you do any Version or Kernel upgrades.  That way, if it does get overwritten, you can always open the saved version and make the changes needed to the new version.

---

