---
title: "No Ubuntu or Linux Mint LiveCDs boot at all"
date: 2008-08-01
forum: General Help
---

### Post by 1002285 on 2008-08-01
I bought a used desktop computer and wanted to see how it works, using Linux Mint or Ubuntu LiveCDs. None of them could start up a system at all. I tried many, and they do work on my other machine. I tried two GNU-based distros, too.

All the CDs seem to "shut down" after loading the Linux kernel. Damn Small Linux, for example, said "kernel panic" after that. Several of Ubuntus and Mints said "CRC error".

The machine has a Windows XP installed which seems to work fine.

What is it?

---

### Post by shamusl on 2008-08-01
> **1002285 said:**
> I bought a used desktop computer and wanted to see how it works, using Linux Mint or Ubuntu LiveCDs. None of them could start up a system at all. I tried many, and they do work on my other machine. I tried two GNU-based distros, too.

All the CDs seem to "shut down" after loading the Linux kernel. Damn Small Linux, for example, said "kernel panic" after that. Several of Ubuntus and Mints said "CRC error".

The machine has a Windows XP installed which seems to work fine.

What is it?

Do you get to the "Start or install ubuntu" page?
If you do I would consider running ubuntu in safe graphics mode, maybe that would help.

---

### Post by bjb.butler on 2008-08-01
one thing to check is to update your computer's firmware. check for updates to the BIOS and the pc's chipset. 

when i built my pc last year, no live cd would boot on it. I then got then flashed the pc with the updated drivers, and its been great ever since.

---

### Post by oldos2er on 2008-08-01
What are the machine's specs? Did you run 'Check CD for Defects'?

---

### Post by 1002285 on 2008-08-02
> **oldos2er said:**
> What are the machine's specs? Did you run 'Check CD for Defects'?
I did not run "check cd", but I tried so many of them, and I have used some of them a couple of days before with success.

Machine's specs from the sale description:
*Intel Pentium 2,4GHz HT Technology
*AsRock P4Dual-880 Pro - [http://www.asrock.com/mb/overview.asp?Model=P4Dual-880Pro](http://www.asrock.com/mb/overview.asp?Model=P4Dual-880Pro)
*SEAGATE Barracuda  7200.7 200GB SATA NCQ - [http://www.amoscomputer.com/estore/control/Amos/productdetails?id=58802](http://www.amoscomputer.com/estore/control/Amos/productdetails?id=58802)
*Sapphire Atlantis Radeon 9700 PRO Ultimate Edition - [http://www.tomshardware.com/reviews/zalman-zm80a,594-6.html](http://www.tomshardware.com/reviews/zalman-zm80a,594-6.html)
*1GB (2x512MB) PC3200 DDRAM CL 2,5 VData
*THERMALTAKE S-Viking - [http://www.tweaknews.net/reviews/sviking/index2.php](http://www.tweaknews.net/reviews/sviking/index2.php)

---

### Post by 1002285 on 2008-08-02
> **shamusl said:**
> Do you get to the "Start or install ubuntu" page?
If you do I would consider running ubuntu in safe graphics mode, maybe that would help.
Yes, I do get to that page. I have not yet tried the safe mode. I will.

---

### Post by 1002285 on 2008-08-02
> **bjb.butler said:**
> one thing to check is to update your computer's firmware. check for updates to the BIOS and the pc's chipset. 

when i built my pc last year, no live cd would boot on it. I then got then flashed the pc with the updated drivers, and its been great ever since.
Thanks, I now have the BIOS drivers and I'll go and try.

---

### Post by 1002285 on 2008-08-02
Nothing helped.
Updating BIOS just did not work
[INDENT][/INDENT]Error: File ROM ID incorrect.
Safe Graphics Mode was not different at all from other options.

I tried different boot options with SystemRescueCD 1.04.
Most times I get this error after loading kernel and initram: Invalid compressed format.

---

### Post by oldos2er on 2008-08-02
"I did not run "check cd""

 That's asking for trouble. Also consider running md5sums: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by 1002285 on 2008-08-02
> **oldos2er said:**
> "I did not run "check cd""

 That's asking for trouble. Also consider running md5sums: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

I'll check the md5sums subject further and try to understand what it's about.
But, really - can it be a coincidence that all the CDs I tried had the same problem? There were about 10 of them, several Ubuntus, several Mints, OpenSuse, Mandriva, SystemRescueCD. And these are the very same CDs that I have actually used with success on other machines.
I don't understand how that could be. But if this is possible - how can this problem be solved by writing the CDs again?

---

### Post by 1002285 on 2008-08-03
I think it's about the boot sector, or wherever the boot.ini is.
When trying Windows install cd, the answer by the system is "incorrect file boot.ini" *or whatever the first word is, my current Windows setup is Russian).

Ultimate Boot CD does not boot either, no particular answer, just a blank screen with the machine making no sounds at all.

I cannot do anything with the system I just bought! Is there no solution? Of course, I could turn to an expert and pay for it, but I thought there must be something that even a non-expert like me could do.

---

### Post by 1002285 on 2008-08-06
I ultimately got the install CDs working fine. I think it had sth to do with RAID. Linux CDs started working when I changed - in BIOS boot options - the 1st boot device from the RAID:ASUS[the model number of the DVDRW-device] to just CD/DVD, and turned the SATA settings to non-RAID. Windows did not start working right after that, but at some point later, it did - somehow.
So the systems have been installed now. I do have one important problem, though - the keyboard does not work at the stage where I need to choose which system to start (Grub): I started a new thread on that - [http://ubuntuforums.org/showthread.php?t=881690](http://ubuntuforums.org/showthread.php?t=881690)

---

