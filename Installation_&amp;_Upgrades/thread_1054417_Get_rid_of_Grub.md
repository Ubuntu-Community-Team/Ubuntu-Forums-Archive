---
title: "Get rid of Grub"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by twodayslate on 2009-01-29
I deleted my Linux partition (actually replaced).
But I am getting a Grub error (Error 22)

I would like to delete grub so I can boot into XP or OSX
I have no way of going into terminal (could use a live CD but... eh) so I need a auto-fix CD or something. 
If you suggest fixing GRUB let me know - I still would like to option of booting to OSX or winblows. 

Thanks!

edit://
[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php) only fixes?

---

### Post by icheyne on 2009-01-29
[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

---

### Post by twodayslate on 2009-01-29
Thanks but XP and OSX are already installed (OSX replaced Ubuntu). Same steps though?
Note: Would rather boot to OSX than XP. If I have to choose between the two ;)

---

### Post by LinuxGuy1234 on 2009-01-29
> **twodayslate said:**
> I deleted my Linux partition (actually replaced).
But I am getting a Grub error (Error 22)

I would like to delete grub so I can boot into XP or OSX
I have no way of going into terminal (could use a live CD but... eh) so I need a auto-fix CD or something. 
If you suggest fixing GRUB let me know - I still would like to option of booting to OSX or winblows. 

Thanks!

edit://
[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php) only fixes?

Install a new bootsector of your OS you want to boot. For multi-boot, I suggest to borrow a friend's computer and burn [GAG]("http://gag.sourceforge.net/") (in archive of the latest version: gag4.01/cdrom.iso) as a *ISO image* to a CD. I would suggest a computer with Ubuntu, so you can simply right-click the ISO and choose to burn it to a CD. Otherwise, reinstall the OS you want to boot into.

---

### Post by twodayslate on 2009-01-29
> **LinuxGuy1234 said:**
> Install a new bootsector of your OS you want to boot. For multi-boot, I suggest to borrow a friend's computer and burn [GAG]("http://gag.sourceforge.net/") (in archive of the latest version: gag4.01/cdrom.iso) as a *ISO image* to a CD. I would suggest a computer with Ubuntu, so you can simply right-click the ISO and choose to burn it to a CD. Otherwise, reinstall the OS you want to boot into.
Burning GAG now. Seems like GRUB (but way more advanced)?

---

### Post by twodayslate on 2009-01-29
GAG didn't work. 
I did get into Winblows via super grub disk. **How do I get into OSX?**

I found this in my C:\ drive
```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```
How would I add OSX?
Found these links but I don't understand :(
[http://forum.insanelymac.com/index.php?showtopic=44974](http://forum.insanelymac.com/index.php?showtopic=44974)
[http://forum.insanelymac.com/index.php?showtopic=85508](http://forum.insanelymac.com/index.php?showtopic=85508)
[http://forum.insanelymac.com/index.php?showtopic=3622](http://forum.insanelymac.com/index.php?showtopic=3622)

edit:// Made a thread at the mac site since this looks like a OSX issue and not a Ubuntu issue
[http://forum.insanelymac.com/index.php?showtopic=150136](http://forum.insanelymac.com/index.php?showtopic=150136)
seems like grub has been removed - default boot is too XP though :(

thanks :)

---

### Post by LinuxGuy1234 on 2009-01-31
> **twodayslate said:**
> GAG didn't work. 
I did get into Winblows via super grub disk. **How do I get into OSX?**

I found this in my C:\ drive
```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```
How would I add OSX?
Found these links but I don't understand :(
[http://forum.insanelymac.com/index.php?showtopic=44974](http://forum.insanelymac.com/index.php?showtopic=44974)
[http://forum.insanelymac.com/index.php?showtopic=85508](http://forum.insanelymac.com/index.php?showtopic=85508)
[http://forum.insanelymac.com/index.php?showtopic=3622](http://forum.insanelymac.com/index.php?showtopic=3622)

edit:// Made a thread at the mac site since this looks like a OSX issue and not a Ubuntu issue
[http://forum.insanelymac.com/index.php?showtopic=150136](http://forum.insanelymac.com/index.php?showtopic=150136)
seems like grub has been removed - default boot is too XP though :(

thanks :)

:lolflag: Booting OS X and Windows all requires chainloading :D

---

