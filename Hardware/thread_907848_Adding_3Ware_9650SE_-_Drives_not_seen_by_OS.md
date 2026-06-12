---
title: "Adding 3Ware 9650SE - Drives not seen by OS"
date: 2008-09-01
forum: Hardware
---

### Post by ttyxzs on 2008-09-01
I am new to Ubuntu...
I have Ubuntu 8.04 LTS Desktop edition [kernel 2.6.24-19 generic] on a single hard drive.

I added a 3ware 9650SE PCI-E raid controller card that has 2 x 500GB drives attached (had to RMA the other 2 drives, but wanted to get everything set up as much as I can anyway).

My objective is to get this card working with Ubuntu, have the drives recognized by Ubuntu, and ultimately configure 4 drives attached to the 3ware card in RAID 5 [hardware raid, not "fake raid"].  Note:  I do not plan on booting from the raid, the OS will remain on the single sata drive where it is already installed.

According to the 3ware forums Ubuntu has native support in the server version for this card.  The desktop version is not mentioned by 3ware...

When the systems boots, after the BIOS loads, a message is displayed with the card name and firmware revision.  Information on the two connected drives follows.  There is then a notice that the 3ware bios is not installed (from what I have been able to determine, where I am not booting from the raid controller, this is a non-issue).

The "messages" log displayed from System --> Administration --> System Log includes these lines:

----   Log start --------------------------------------------------------
.... 
[SIZE="1"]Sep  1 18:06:50 MYPC1 syslogd 1.5.0#1ubuntu1: restart.
Sep  1 18:06:51 MYPC1 kernel: Inspecting /boot/System.map-2.6.24-19-generic
Sep  1 18:06:51 MYPC1 kernel: Loaded 28492 symbols from /boot/System.map-2.6.24-19-generic.
Sep  1 18:06:51 MYPC1 kernel: Symbols match kernel version 2.6.24.
....
Sep  1 18:06:51 MYPC1 kernel: [   33.003172] sata_nv 0000:00:07.0: Using ADMA mode
Sep  1 18:06:51 MYPC1 kernel: [   33.008939] scsi0 : sata_nv
Sep  1 18:06:51 MYPC1 kernel: [   33.021260] scsi1 : sata_nv
Sep  1 18:06:51 MYPC1 kernel: [   33.021444] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
Sep  1 18:06:51 MYPC1 kernel: [   33.021446] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
Sep  1 18:06:51 MYPC1 kernel: [   33.045641] 3ware 9000 Storage Controller device driver for Linux v2.26.02.010.
.....
Sep  1 18:06:51 MYPC1 kernel: [   35.853008] ACPI: PCI Interrupt 0000:04:00.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
Sep  1 18:06:51 MYPC1 kernel: [   36.076437] scsi7 : 3ware 9000 Storage Controller
Sep  1 18:06:51 MYPC1 kernel: [   36.076485] 3w-9xxx: scsi7: Found a 3ware 9000 Storage Controller at 0xc3000000, IRQ: 17.
Sep  1 18:06:51 MYPC1 kernel: [   36.412293] 3w-9xxx: scsi7: Firmware FE9X 3.08.02.005, BIOS BE9X 3.08.00.002, Ports: 4.[/SIZE]
....
----   Log End  ---------------------------------------------------

I am guessing that the log entries indicate that the 3ware card is being recognized by Ubuntu.  
I do not see anything in the log that looks like the drives are discovered.

The drives attached to the 3ware card are not shown in the partition editor, nor are they listed by the mount command.

I am at a loss as to how to proceed in troubleshooting this.  Any and all assistance is greatly appreciated!

Thank you

PS - My hardware is:
iStarUSA S-9-H35 case (5 Hot-Swappable SATA II Drive Bay)
ASUS A8N-SLI Premium Mobo
AMD Athlon X2 3800+
Nvidia 7600GT graphics card [BFG]
2GB RAM
the aforementioned 3ware 9650SE card

---

### Post by ttyxzs on 2008-09-02
:oops: doh!  rtfm!  The 3ware 9650 card for some reason doesn't display a message when the 3ware bios is loading to press ALT-3 to enter the 3ware bios to configure the attached drives....

---

### Post by dean123 on 2008-09-05
> **ttyxzs said:**
> :oops: doh!  rtfm!  The 3ware 9650 card for some reason doesn't display a message when the 3ware bios is loading to press ALT-3 to enter the 3ware bios to configure the attached drives....


You don't have to use 3ware bios. Download 3dm2 software from 
3ware site, install it. Use 3dm2 to create a raid array. 

It looks like Ubuntu did see the raid controller. 
Good luck.

---

### Post by lonejack on 2008-09-23
I've the same problem. The 9650SE is running well. It doesn't need a setup to start but with ubuntu desktop(8.04) isn't possible to check it. I know that on server edition it's allowed. Why developers didn't installed that option also on desktop release?
Thank you
lonejack

---

### Post by phillypete on 2008-10-04
> **lonejack said:**
> I've the same problem. The 9650SE is running well. It doesn't need a setup to start but with ubuntu desktop(8.04) isn't possible to check it. I know that on server edition it's allowed. Why developers didn't installed that option also on desktop release?
Thank you
lonejack

I plane to install a similar configuration as ttyxzs except using 9650SE SATA controller and 500GB drives. Lonejack are you running a desktop or server version of Ubuntu where you have this installed and running well?

---

### Post by cariboo on 2008-10-04
> I've the same problem. The 9650SE is running well. It doesn't need a setup to start but with ubuntu desktop(8.04) isn't possible to check it. I know that on server edition it's allowed. Why developers didn't installed that option also on desktop release?
Thank you
lonejack

I don't understand what you are trying to say, if there is a utility that allows you to monitor your raid array in the server version, you can install it on the desktop version. They are not installed by default, because you aren't expected to run a raid array on a desktop system. If you are, you can add the tools yourself.

Jim

---

### Post by phillypete on 2008-10-04
Thanks Jim,

I'm quite new to Ubuntu. What is the utility that you add to monitor the hardware controlled array? 

I appreciate these forums' help before I commit a lot of coin into a project:).

---

### Post by dragonrider on 2008-10-10
I have an 9650se too.

I have installed ubuntu system on a drive which belong to the RAID array : ubuntu work great. 

Now i try to install ubuntu on a sata disk which do NOT belong to the RAID array . The problem is that i can install ubuntu on it, but the RAID array is no visible any more. I think this is a problem bios configuration but i do not know how to solve the problem.

is there someone who can help me ? 

My hardware is : 
Motherboard : P5E3 deluxe edition wifi
HDD sata : Maxtor 200Go
and the raid card controler 3ware 9650se-4LMPM.

To conclude : 
1) I can boot on the system which is on the raid array, only if my hdd sata is not configured has primary, with this configuration i can see the hdd sata
2) If my hdd sata is configured has primary i can't see the raid array.

---

