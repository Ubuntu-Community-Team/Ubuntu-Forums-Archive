---
title: "Radeon Graphics and Ver. 12.10 Crash During Installation"
date: 2013-04-04
forum: Hardware
---

### Post by tm-hart on 2013-04-04
**Radeon Graphics and Ver. 12.10 Crash During Installation**

A new HP Compaq desktop computer, description follows, replaced a computer that failed.  A problem installing Ubuntu version 12.10 on the new computer was apparently due to its inability to use Radeon integrated graphics.  The background, hardware modification and successful installation are described.  In short, a PCI Express card replaced the integrated graphics.

**Part 1.  Desktop Computer Description:**
HP Pavilion desktop computer model P6-2316S  (Purchased March 2013).

**Motherboard:**
AAHD2-HY (Holly2) with Radeon HD Graphics - Manufacturer: Pegatron
AMD A4 3420 Processor
Memory 4 GB – installed in slot A1-DIMM0 

**Video graphics:**
Integrated – Radeon HD Graphics

**Additonal graphics Info (per HP Web Site):**
“Integrated video is not available if a graphics card is installed.
[The computer] Supports PCI Express x16 graphics cards
DVI and VGA ports (Can be used at the same time)”
I assumed a PCI Express card would over-ride the integrated graphics.

**SATA Socket Usage:**
HD to SATA socket #1
CD / DVD to SATA socket #3

**Devices:**
Hard drive: 500 GB 
CD/DVD Super-Multi Burner drive

**Part 2. HP System Tests Performed:**
During boot-up, the computer passed all HP Startup Menu hardware diagnostic tests (HP Menu option F-2).

[B]Part 3. HP Menu option F-10: The bios settings to install Ubuntu 12.10 as “Legacy Hardware”, not “UEFI Settings Hardware" were:
[/B]

(1) Legacy Devices enabled; DVD & USB boot before HD.
(2) Virtualization disabled.
(3) Secure Boot disabled; Fast Boot disabled.
(4) HD passed the DPS Self Test.
(5) Emulate “AHCI” for HD.

Original Problem Summary:  The Ubuntu 12.10 Live DVD ISO was burned to a DVD to boot the computer.  The software loaded the purple screen (indicating non-UEFI start-up).  A second purple screen with the name “Ubuntu” then appeared.  Five dots under the name cycled through red and white colors.  Finally, the orange swirled desktop appeared.  At that point, the system froze.  No menus, launchers or mouse pointers appeared.

A second bootable CD was prepared for GPARTED ISO (GPARTED-LIVE-0.15.0-1-486.ISO).  This disk started the computer, loaded the low resolution selection menu, scrolled text and then froze.

At this point, the integrated video appeared to be the problem.  A third boot-up test, using a CD-ROM with KDE Partition Manager, was made.  The computer started normally and loaded the KDE menu.  I created a single disk partition (/dev/sda) with the “ext3” file system as a test.  It worked without a problem.  Apparently, the Radeon video does not work with all bootable software.  A check on the Ubuntu website disclosed several reports of Radeon video problems. 

**Part 4. Resolution:**

My solution was to insert a PNY PCI Express video card with Nvidea Graphics into the mother board.  The Samsung monitor moved from the Radeon connector to the PNY connector.  I was then able to boot the Ubuntu 12.10 64-bit Live DVD and install the operating system without any problems.  After loading all updates, I shut down and rebooted with  the GPARTED DVD.  It loaded normally and displayed program's start screen.  I inspected the partitions created by the Ubuntu install DVD as a test.

From that point, everything worked properly.  I will continue to use the PNY PCI Express video card until I determine if a future version of Ubuntu works with the integrated Radeon video hardware.  A decision will then be made to stay with the PNY video or shift back to Radeon.

---

