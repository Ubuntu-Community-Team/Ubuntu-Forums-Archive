---
title: "Xubuntu 8.10 on Presario 1260 CD-ROM Problem"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by RealK7 on 2009-04-20
Trying to install Xubuntu 8.10 i386 Alternate Install CD on Presario 1260.

The CD boots and I come to the first menu, selecting acpi=off, then chooses install, the language screen and the keyboard layout works fine but after the screen "Detecting hardware to find CD-ROM drives" it says "Detect and mount CD-ROM : No common CD-ROM drive was detected". 

The cdrom is working in windows, dsl-n and puppy linux.

Found these topics:
[http://ubuntuforums.org/showthread.php?t=995200&highlight=install]("http://ubuntuforums.org/showthread.php?t=995200&highlight=install")
[http://ubuntuforums.org/showpost.php?p=6246318&postcount=3]("http://ubuntuforums.org/showpost.php?p=6246318&postcount=3")

But I only get the message "FATAL: Module ide_scsi not found."

Please help.

---

### Post by Partyboi2 on 2009-04-20
hi, try booting with '*all*-*generic*-*ide' *as a boot option. When you are at the main menu press F6 and at the end of the line add```
 all-generic-ide

```  and press enter.

---

### Post by RealK7 on 2009-04-20
The line ends with QUIET -- 

do i type the boot option before or after "--"?

---

### Post by Partyboi2 on 2009-04-20
Before the -- and after the word quiet.

---

### Post by RealK7 on 2009-04-20
I got the same result this time... any other suggestions?

---

### Post by Partyboi2 on 2009-04-20
You could try some other boot options like 'noapic nolapic pci=noacpi'
otherwise I have no other ideas, maybe someone else might be able to help.

---

### Post by RealK7 on 2009-04-20
No it didn't work but thanks anyway. I'll just go back to Win 2000.

---

