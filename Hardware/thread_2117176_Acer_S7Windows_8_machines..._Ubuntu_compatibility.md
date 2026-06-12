---
title: "Acer S7/Windows 8 machines... Ubuntu compatibility"
date: 2013-02-17
forum: Hardware
---

### Post by ryandushane on 2013-02-17
Hello!
I was wondering if the Acer S7 has the ability to run Ubuntu. I was at Staples the other day, and played with some of the new Windows 8 machines. I turned some off, and on again to see what the BIOS was like, if any. Non of them seemed to have a user accessible BIOS menu. It jumped straight to the Windows boot screen. Given, non of these were the Acer S7 specifically. Do any of you have new Windows 8 machines that have the tablet format, and newer over all design? How does Ubuntu run? Is even possible to install other OS's?

---

### Post by oldfred on 2013-02-17
This model worked.

       Acer V5-571P-6815 secure boot off worked
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

    
Windows does several work arounds to make it seem like it is a faster system. It turns off access to UEFI/BIOS so you load Windows and Windows is always hibernated so it can boot quickly. You have to turn these settings off. Some uninstall Windows without changing UEFI settings and then have major issues.
UltraBooks then add a small SSD to cache Windows. It seems Windows code is so large you have to have cache to speed things up even more than a fair amount of RAM.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

