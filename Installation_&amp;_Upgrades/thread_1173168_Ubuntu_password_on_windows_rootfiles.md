---
title: "Ubuntu password on windows rootfiles"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by Dawoodoz on 2009-05-29
I recently installed **Ubuntu 9.04** on a new ext3 partition with 6GB virtual memory on the same harddrive as **Windows 2000**. :D
 
The problem is that I now can't start **Windows 2000** without a **bluescreen** after the loadingscreen. :(
It seems to be because windows can't use it's harddrive according to the bluescreen message.
It seems to be because Ubuntu has my login's **password** on the windows partition.
Ubuntu seems to think that the **Windows partition** is a **personal media album** :o to protect from Windows users.
 
What should I do now? :(
 
David

---

### Post by mikewhatever on 2009-05-29
The thing is, when you start Windows, Ubuntu isn't loaded so that it can't possibly do things like thinking or having passwords. Since neither the question nor the explanation make much sense, why don't you just tell us what the error message is.

---

### Post by iponeverything on 2009-05-29
Can you see the files on your windows partition when you are in linux?  If you can, I would backup your files.

---

### Post by Dawoodoz on 2009-05-29
"Can you see the files on your windows partition when you are in linux? If you can, I would backup your files. "
 
I make backups to HDD, SSD and memory stick every evening. ;)
 
 
"The thing is, when you start Windows, Ubuntu isn't loaded so that it can't possibly do things like thinking or having passwords."
 
Windows XP has that to protect against access thru DOS but ubuntu goes around it. :)
 
 
"why don't you just tell us what the error message is"
 
Here is the relevant part of the message and the rest is in swedish.
"
*** STOP: 0x0000007B (0xF681B848,0xC0000034,0x00000000,0x00000000)
INACCESSIBLE_BOOT_DEVICE
"
 
Can it be ubuntu's automatic reference to the partition that's wrong? ](*,)
 
Does ubuntu have something like boot.ini for the menu? :p

---

### Post by coffeecat on 2009-05-29
> **Dawoodoz said:**
> Can it be ubuntu's automatic reference to the partition that's wrong? ](*,)
 
Does ubuntu have something like boot.ini for the menu? :p

This is nothing to do with Ubuntu; this is a startup problem with Windows 2000. However, googling "inaccessible_boot_device windows 2000" comes up with a very large number of hits. Much as it pains me to post links to the microsoft website on this forum, these two seem to be the most useful:

[http://support.microsoft.com/kb/822052](http://support.microsoft.com/kb/822052)

[http://support.microsoft.com/default.aspx?scid=kb;en-us;315396&sd=tech](http://support.microsoft.com/default.aspx?scid=kb;en-us;315396&sd=tech)

---

### Post by Dawoodoz on 2009-05-29
Thanks, but I still don't know where the reference is stored since I choose to start Windows 2000 from ubuntu's multiboot menu and I never see the menu in boot.ini who I recently wrote.

---

### Post by mikewhatever on 2009-05-29
I have to second coffecat, it has nothing to do with Ubuntu. The menu you see is GRUB (the boot loader), but blue screens and those kind of messages is Windows, which means the process has been passed on to the Windows boot loader.

---

### Post by Dawoodoz on 2009-05-30
I have now erased the ubuntu partition and Windows 2000 is working again.
Ubuntu seems to work better with windows when booting from the CD. :p

---

