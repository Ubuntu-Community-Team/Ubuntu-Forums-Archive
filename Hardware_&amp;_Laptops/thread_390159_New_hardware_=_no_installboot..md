---
title: "New hardware = no install/boot."
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by Mats666 on 2007-03-21
Hardware:
Asus P5B-MX/WIFI-AP, 946GZ, Socket-775  [link]("http://www.asus.com.tw/products4.aspx?l1=3&l2=11&l3=182&model=1494&modelmenu=1")

Intel Pentium 4 641 3.2GHz Socket LGA775 

Crucial DDR2 PC5300 1024MB CL5 Unbuffered,1.8V,128Meg x 64

When trying to install a standard install (tried both dapper and breezy) I only get to "PCI: Probing PCI hardware (bus 00)" and then it hangs. :(

Tried to search but only find millions of lines of code and USB problems, nothing that help me. I have been running a couple of servers and feel reasonably comfortable within the system but these kind of problems really stop me dead. :|

I've searched around and other dists like Red Hat seems to have the same problem and the fix seems to be to be to add a boot parameter "pci=nommconf", is there something similar I can do in the grub menu? Changing settings in the BIOS won't do anything right?

---

### Post by Mats666 on 2007-03-22
After sleeping on it and some more searching I realized I might have done a huge beginners error when I tried to install from my IDE-CDROM... 
 I'll try my USB-CDROM later today when I get home.

I read these threads and they were helpful.
 
[http://www.ubuntuforums.org/showthread.php?t=343298](http://www.ubuntuforums.org/showthread.php?t=343298)
[http://www.ubuntuforums.org/showthread.php?t=326343](http://www.ubuntuforums.org/showthread.php?t=326343)

I'll continue to log my progress here, might help someone else (or show someone that knows anything that I actually do try to solve it myself... ;) ).

---

### Post by Mats666 on 2007-03-22
Ok, New SATA drive and installing from USB-CDROM, well, it halts. But it halts on the line below the one before. :|

ACPI: Assume root bridge [\_SB_.PC10] segment is 0

Well I'm out of ideas... :(

---

### Post by azemute on 2007-03-22
Would you mind posting a bit more information? You said you got new hardware, I assume you mean a new motherboard, processor and cpu? What were you using before? Can you perhaps give all of the halt-code information when it tires to boot?

Normally, in my experience, this is due to nasty issues with ACPI or IRQ handling... you may want to try booting with acpi=off as a kernel parameter [or, turn it on if it already is off], though a bit more information would probably be helpful.


\\-Zac

---

### Post by Mats666 on 2007-03-22
Funny you should say that, tried the acpi=off command just because I have had the same problem with it before and it booted right up!

It's installed and restaretd a couple of times now without even the slightest glitch. Man it's fast. :)

New hardware meant ALL new hardware but started with only the basics: PSU, mobo, CPU, memory and HDD to rule out all those other things that might happen.
 Now I'm going to start to add some more hardware and hopefully it just works. (fingers crossed)

Thanks.

---

