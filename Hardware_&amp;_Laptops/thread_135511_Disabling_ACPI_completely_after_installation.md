---
title: "Disabling ACPI completely after installation"
date: 2006-02-24
forum: Hardware &amp; Laptops
---

### Post by r8dhex on 2006-02-24
I've successfully installed Ubuntu5.10 on an old laptop.

When ACPI is on, after a few minutes of use, the laptop will just crash hard or use 100%cpu or just lockup. This was a known issue when I was using Gentoo on it before. As a workaround, I added "acpi=off" to the kernel lines in the grub.conf, but I'm afraid that when the Update Manager updates the kernel, it will add a new grub entry that uses ACPI.

Another small problem is that the boot process tries to load some drivers for fancontrol, and other powersaving features.

How do I properly and completely turn off ACPI and just have Ubuntu be a completely APM-based system?

Thanks

---

### Post by handy on 2006-02-24
I have had to install Breezy 5.10 on an older machine using the acpi=off parameter, or I could not even get through the installation!

So, surely you can manually configure a machine not to use acpi & it will stay that way.

Some knowledgable Ubuntonian will verify how for you I am sure.  :)

---

### Post by codejunkie on 2006-02-24
[QUOTE=handy]I have had to install Breezy 5.10 on an older machine using the acpi=off parameter, or I could not even get through the installation!

So, surely you can manually configure a machine not to use acpi & it will stay that way.

Some knowledgable Ubuntonian will verify how for you I am sure.  :)[/QUOTE]
you add the entry you need to the /boot/grub/menu.lst file and it will load it at boot.

---

### Post by r8dhex on 2006-02-25
[QUOTE=handy]I have had to install Breezy 5.10 on an older machine using the acpi=off parameter, or I could not even get through the installation!

So, surely you can manually configure a machine not to use acpi & it will stay that way.

Some knowledgable Ubuntonian will verify how for you I am sure.  :)[/QUOTE]

Well, I was able to go through installation just fine. But now that it's installed, I'd like to know if there's a global setting somewhere that says "I don't ever want to use ACPI again, and when Ubuntu adds a new entry to my menu.lst file, it will not assume that I want ACPI, because I don't". The laptop's BIOS doesn't have a setting to turn off ACPI, so I'm looking for a way to turn it off at the OS level.

[QUOTE=codejunkie]you add the entry you need to the /boot/grub/menu.lst file and it will load it at boot.[/QUOTE]

I did write in my post that I did this. Now how do I, if possible, set it so that next time update manager updates my kernel and adds a new entry, it will know that I don't want ACPI and add the appropriate option for it?

Now, if it's not possible to set ACPI off completely AFTER installation, is using "linux acpi=off" during booting of the install cd enough? Will it stay off even after the installation is finished?

---

### Post by ranf on 2006-02-25
[QUOTE=r8dhex]
I did write in my post that I did this. Now how do I, if possible, set it so that next time update manager updates my kernel and adds a new entry, it will know that I don't want ACPI and add the appropriate option for it?
[/QUOTE]
/boot/grub/menu.lst _is_ the place. Look for a line 
```
# kopt=
```
and add acpi=off at the end.
Run 
```
sudo update-grub
```
then look at menu.lst again and you should see your setting added to every kernel listed.

---

### Post by r8dhex on 2006-02-28
Thanks, I'll try this tonight.

---

