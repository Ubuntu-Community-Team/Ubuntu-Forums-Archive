---
title: "Ubuntu doesn't boot on my Amilo M1425 (other Linux distributions either)"
date: 2008-09-23
forum: Hardware
---

### Post by bluetooth on 2008-09-23
Hi everyone! I have really big problem. I cannot run Ubuntu on my M1425, it just doesn't boot. The problem appeared after I upgraded the BIOS with the version 1.08c which is the latest according to the Fujitsu-Siemens' website (it was released in 2007 though). The problem seems to be with the SMP ans ACPI (or at least with the information about them provided by BIOS to OS since the Windows runs without any problem) since it is possible to boot Ubuntu with flags "acpi=off nosmp noapic" but in this case network card and other devices function improperly.

I have also tried to boot openSUSE, Knoppix, Fedora, Debian but neither of them boot without flags. And as I said, Windows XP runs without any problem. I suspect that FS put a function in BIOS that recognizes the OS trying to boot and returns "No SMP, No ACPI" information to all OSs except Windows. I have read that the similar function was found in Foxconn's BIOS so I wouldn't be surprised if the same is true for FS.

---

### Post by bluetooth on 2008-09-24
So, no one knows how to fix this issue?? I really miss Linux...haven't worked on it for months :'(

---

### Post by bluetooth on 2008-09-28
OMFG, I tried to contact FS support, this is their reply... :

Dear Mr. ,

You don't need to take this tone with our agent he gave the correct answere to your question.

We don't support Linux on this computer as an operation system and we can't supply any bios settings for booting it eighter.

This computer is sertifyed only for windows os.

---

