---
title: "Ubuntu + Windows 7 = ???"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by linel90 on 2009-09-13
Hey guys...


I want to install ubuntu.. but the problem is that i have windows 7 and all my software installed... the only problem is that every guide or info i found on the internet, "google" here in the forums.. Said that i should install ubuntu first.. Any chance that i can install ubuntu without reinstalling windows 7?.. 

Thanks :)

---

### Post by pythonscript on 2009-09-13
You should always install Ubuntu second... I don't know what guides you found, but installing Windows (any version) after Ubuntu will overwrite the master boot record of your hard drive with Windows data and stop you from booting into Linux. You should be fine dual-booting Ubuntu and Windows 7. Just insert the Ubuntu CD and follow the instructions during the installation process to dual boot.

---

### Post by linel90 on 2009-09-13
```
http://www.bauer-power.net/2009/06/how-to-dual-boot-windows-7-and-ubuntu.html
```

Thats the article i read.

---

### Post by bumanie on 2009-09-13
I don't know where you found that information...It is a well accepted that it is far easier getting a dual boot windows/linux system going by installing windows first and linux second (unless you use something like easybcd or GAG bootlader)- it is possible to do it the other way around, but is more difficult to configure. If I were you I would keep windows 7 as the first OS and install ubuntu as the second OS and grub will configure a dual boot system for you. There are three options at the partitioning stage. I always choose manual and allocate 10gb to / ; /home as large as I like and 1-2gb to /swap. There are loads of tutorials around - [here's one]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") from a couple of years ago, the basic principle is still the same, even though this is for xp...and there are many more. Have a read of a number of them, there is no right and wrong way to do it. It comes down to your personal preference.

---

### Post by Marlonsm on 2009-09-13
As others said, it's better to have Windows installed first, and then, install Ubuntu.
While Ubuntu was made to work side-by-side with other OS in the same HD, Windows was not.
So if you have Ubuntu installed first and then install Windows, every time you boot your computer it'll start Windows without asking anything. Ubuntu will still be installed, but not accessible, you'll have to fix it manually.
But if you have Windows and install Ubuntu, and during the installation you choose  to dual boot, Ubuntu will set up the boot manager for you.

---

### Post by running_rabbit07 on 2009-09-13
I have both and Windows 7 has to be first. Windows is that kids that pushes his way to the front and messes everyone else up on the way. So yeah, that said, Windows first then Ubuntu.

Have fun.

---

### Post by presence1960 on 2009-09-13
> **pythonscript said:**
> You should always install Ubuntu second

that is not true. You can install windows after ubuntu. see here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You can install windows after Ubuntu, but windows should be on a primary partition. Windows will write it's bootloader to MBR, overwriting GRUB. All you need to do after installing windows is a 45 second procedure to restore GRUB to MBR like this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

The OP already has windows so back up your data, defrag windows at least once or twice. maybe even turn off system restore until Ubuntu is installed. Windows 7 RC is like Vista. As such I would use windows disk management utility to shrink windows partition to create space for Ubuntu. Question this? here is a [link]("http://bugzilla.gnome.org/show_bug.cgi?id=379482") to an as yet unresolved bug in resizing Vista with anything (including gparted) but it's disk management utility. Sometimes it works ok, but other times it renders Vista unbootable.  Win 7 RC is still very similar to Vista, maybe that will change with it's official release. After creating space with the windows disk management utility boot the Ubuntu Live CD and install using the "use largest continuous free space" option. or do as bumanie suggested creating partitions from the free space and then install Ubuntu using the manual option. Either way will work.

P.S bumanie is correct in saying it is easier to install windows first- for a noob! But the fact remains we should not be telling people they **must install windows first because it simply is not true.** What if someone already has Ubuntu installed? Are you going to tell them they have to uninstall a perfectly good Ubuntu OS to install Windows? Would you want to do that? Especially since you can install windows to a primary partition and then restore GRUB to MBR which will give you your dual boot option menu when you start your machine. Windows does not have to be on the first primary partition. All it needs is a primary partition. I had windows 7 on sda4 until I removed it. Now I have XP on sda2.

---

