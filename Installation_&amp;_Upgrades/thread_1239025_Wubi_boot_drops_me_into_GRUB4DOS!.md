---
title: "Wubi boot drops me into GRUB4DOS?!"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by starbase1 on 2009-08-13
Probaby best to describe how I got here...

I did have a partition for Ubuntu Studio.
I formated this and then had boot problems.
I fixed these with fixmbr from an XP disk.
I then tried a WUBI install of Ubuntu 9.04,64 bit, with the big file going to the old Studio partition.

I tried a boot, but it drops out into a prompt for GRUB4DOS

In case it helped clear any mess from the previous install, in windows I uninstalled Ubuntu, then added it again.

Same result.

Any ideas?

---

### Post by ottosykora on 2009-08-27
same to me.

tried to install first:
9.04 with wubi 9 , the disk creation takes for ever??, the settings for the grub seem to be correct, still when I boot to ubuntu I end up in the grub 'bash' since the grub does not find the kernel etc.

Searching for help on this too. 

Same happened when I tried to uninstall and then install 8.10 with its wubi.

---

### Post by Mark Phelps on 2009-08-27
> **starbase1 said:**
> Probaby best to describe how I got here...

I did have a partition for Ubuntu Studio.
I formated this and then had boot problems.
I fixed these with fixmbr from an XP disk.
I then tried a WUBI install of Ubuntu 9.04,64 bit, with the big file going to the old Studio partition.

I tried a boot, but it drops out into a prompt for GRUB4DOS

In case it helped clear any mess from the previous install, in windows I uninstalled Ubuntu, then added it again.

Same result.

Any ideas?
Wubi uses GRUB4DOS to handle GRUB because it installs Ubuntu to an MS Windows-formatted partition as if it were an application when, in fact, it is a file that Ubuntu treats as an installation.

Personally, I don't use Wubi because MS Windows is flaky enough as is without injecting another OS into it.  Seems all you have to do sometimes is breath hard and you get a filesystem fault in MS Windows.  I prefer the stability of having Ubuntu in it's own native filesystem.

Since you already removed Wubi, there's no way to get it to clean up after itself.

Is the option for Ubuntu still showing up when you boot? If so, you can remove the Ubuntu line from the boot.ini file. You should then be able to reinstall Wubi without problems.

Also, what MS Windows version are you using? XP? Vista? Seven?  Either of the first two should work fine; the third is not certified to work with Wubi yet.

---

### Post by dpawl31 on 2009-08-27
Wow, this is very similar to what happened to me, and I am screwed from what I can tell.


GRUB comes up, select windows or ubuntu.
Windows loads fine.

Ubuntu -NOT.

It goes right to GRUB4DOS... and no idea what to do from there.
I can't get into my UBUNTU.

I did NOT uninstall WUBI though. Everything sits as is.

Basically the PC was ON and running Ubuntu - and we lost power overnight.

When I came in the next day - my uncle, who is using this computer, told me he tried to get in and couldn't. I am not sure what happened between the time it rebooted and when I got there, but generally he won't touch it if he doesn't know what it is.

So - can I use grub4dos to at least get into my ubuntu, save my files, and reinstall fresh?

Otherwise, is there ANY WAY to get my files back? They are stored in a folder under my documents inside Ubuntu, but I can't use the LIVECD to access it because it's a WUBI install, correct?

Can I access my files via windows somehow?

This is my menu.lst from c:\ubuntu\winboot
```
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

```

---

### Post by starbase1 on 2009-08-30
> **Mark Phelps said:**
> Wubi uses GRUB4DOS to handle GRUB because it installs Ubuntu to an MS Windows-formatted partition as if it were an application when, in fact, it is a file that Ubuntu treats as an installation.

Personally, I don't use Wubi because MS Windows is flaky enough as is without injecting another OS into it.  Seems all you have to do sometimes is breath hard and you get a filesystem fault in MS Windows.  I prefer the stability of having Ubuntu in it's own native filesystem.

Since you already removed Wubi, there's no way to get it to clean up after itself.

Is the option for Ubuntu still showing up when you boot? If so, you can remove the Ubuntu line from the boot.ini file. You should then be able to reinstall Wubi without problems.

Also, what MS Windows version are you using? XP? Vista? Seven?  Either of the first two should work fine; the third is not certified to work with Wubi yet.

Thanks for the suggestions. I installed Wubi from inside Windows XP. (I sometimes use XP64, but did not use it for this).

This is the contents of the boot.ini file:
[I][B]
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /3GB
C:\wubildr.mbr = "Ubuntu"
[/B][/I]

c:\wubildr.mbr does not exist.

Seems like it might be a good idea for me to remove the reference to the non-existent wubi file...

---

