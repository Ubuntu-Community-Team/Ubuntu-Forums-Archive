---
title: "DMI, ACPI: Unable to locate RSDP"
date: 2005-12-07
forum: Hardware &amp; Laptops
---

### Post by Nopposan on 2005-12-07
[4294667.296000] Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e801: 0000000000000000 - 000000000009f000 (usable)
[4294667.296000]  BIOS-e801: 0000000000100000 - 0000000004000000 (usable)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 64MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 16384
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 12288 pages, LIFO batch:7
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI not present.
[4294667.296000] ACPI: Unable to locate RSDP
[4294667.296000] Allocating PCI resources starting at 04000000 (gap: 04000000:fc000000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] No local APIC present or hardware disabled

That's the beginning of my output for 'dmesg'.

I have no idea what DMI is or what RSDP is.

Please advise, I think that these things may have something to do with why I can't get sound or why I have to start X window system manually at the command line.

Thanks.

---

### Post by ranf on 2005-12-08
I at least found something about DMI:
[http://en.wikipedia.org/wiki/DMI](http://en.wikipedia.org/wiki/DMI)

Don't know what RSDP is.

---

### Post by Nopposan on 2005-12-08
Hmm. . . It says "Desktop Management Interface" so that sounds like a serious thing to go missing.  However, the WIkipedia stub also says that the DMI is to be used for enabling PCs to be monitored from a central management console in a network.  Since I'm not currently interested in this function, and may never be, can I safely ignore the message?

'Still wondering about RSDP.  It might help folks to know that I'm now running a Compaq Armada 7750.  Wireless is working!  I've got  a couple of 64MB RAM chips coming that will replace the current pair of 32MB.  This thing is funky; I've got a drive bay that I can use to swap a CD ROM with a floppy.

'Currently running Xubuntu, but I have a lot of work to do before I can hand this project over to my niece to do her schoolwork and e-mail her friends.

---

### Post by dsb on 2006-11-16
google seems to be a good friend; what I found is RSDP is [http://linux.about.com/cs/linux101/g/rsdp.htm](http://linux.about.com/cs/linux101/g/rsdp.htm)
something about Root System Description Pointer. 

My research and successful results were to disable the ACPI option. Ok next question what is ACPI? Again, google turns up this great page for more info: [http://www.acpi.info/](http://www.acpi.info/)

Apparently, there seems to be a cutoff to old hardware vs. new hardware.

The fix for me anyway is to disable ACPI in the boot options.

---

### Post by Nopposan on 2007-01-24
'Right.  The old laptop uses APMD for power management; newer computers use acpi.  I disabled acpi when I reinstalled with Xubuntu 6.06 using the noacpi option at the installer's boot prompt.

---

### Post by platypuss72 on 2007-07-21
hi i am having the same problems ....

but and tring to install xubuntu on an old laptop so using alterative install disk ... 

but i do not know how to do the boot with "noacpi" option ?????

could any tell me how please

cheers luke

---

