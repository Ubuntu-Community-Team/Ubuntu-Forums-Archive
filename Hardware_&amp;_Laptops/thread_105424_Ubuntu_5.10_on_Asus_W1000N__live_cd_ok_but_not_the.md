---
title: "Ubuntu 5.10 on Asus W1000N : live cd ok but not the installation :-("
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by Greguti on 2005-12-18
Hi all,

i tried a live cd of Ubuntu 5.10 and everything workeg great. My wi-fi cheapset was identified and working, the screen resolution was ok (1680x1050), everything was running smoothly... Well I was very impressed by the distribution indeed.

Then I downloaded and burned the install iso of Ubuntu 5.10. Booted on the cd and launched the installation process with the following commands:

linux boot vga=771 
linux boot vga=771 acpi=off
linux boot vga=771 noapic nolapic

But each time I got the same trouble during the insall of the "systeme de base": the pacakge initrd-tools can't be copied to the partition... 

That's very annoying, especially since the Live CD runned quite well, so I know that Ubuntu 5.10 is working on my computer... excepted from the error during the install!

Any help?

Regards

Gregory
Paris, France

---

### Post by brainkilla on 2005-12-18
You obviously have a bad sector on the install CD, or your CD/DVD drive is not clean enough to read it. I would also check the MD5 sums of the downloaded Ubuntu ISO, but I my bet is still on media being faulty in some way. Try burning at lower speed for a start...

---

### Post by jml on 2005-12-18
I agree with brainkilla.  Since the live CD worked, we know its not an issue with your hardware.  If you have a broadband connection, download the iso again and burn a fresh copy using a slower writing speed on the CDROM drive.  If that fails, you can contact the developers through the web site to request a pressed CD.

Joe

---

