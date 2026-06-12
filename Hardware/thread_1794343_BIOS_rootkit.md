---
title: "BIOS rootkit"
date: 2011-06-30
forum: Hardware
---

### Post by blweldon2 on 2011-06-30
Got a bios rootkit problem. Laptop won't boot off cd, usb, hard drive, or even floppy. I have no idea how to get rid of an infection this bad. Does anybody know how to get rid of it? I believe it is a strand of Alureon. I can't boot into linux on it in any way to fix it.

---

### Post by TechSupportx86 on 2011-06-30
Have you tried pulling the CMOS battery? If that doesn't fix it you probably need to re-flash the BIOS.

---

### Post by blweldon2 on 2011-06-30
Rootkit won't let me flash or update the bios, tried killcmos on a hirens bootcd.

---

### Post by Dangertux on 2011-06-30
Why do I feel like this is 2006 and I'm at Black Hat again? Oh...I know why lol..Sorry internal commentary ;-)

On a more serious note : A BIOS rootkit is an EXTREMELY rare thing to see, it's even more rare to see actually working. Many rootkits Alureon included utilize the Master Boot Record for their persistence, because of this they are easily detected.  Rarer still are virtualization based root-kits that install themselves as a hypervisor ; ala Blue Pill and the Black Hat reference. 

However, an older, yet more difficult to detect method is the BIOS root-kit. This method is extremely difficult to pull off ; and it usually only uses its BIOS code for the purpose of persistence and to reinfect the system. There isn't a whole bunch of room in the ACPI namespace for much else, including prevention of booting etc.

If you're REALLY concerned about this being the case, and I can't stress enough how unlikely it is that this is the case. You can start monitoring ACPI messages to the kernel. 

However, I would really consider spending time investigating potential hardware failure, unless of course you have some substantial evidence that it is this EXTREMELY rare form of rootkit.

---

