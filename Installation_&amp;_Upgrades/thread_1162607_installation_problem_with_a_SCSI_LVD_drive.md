---
title: "installation problem with a SCSI LVD drive"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by banoptic on 2009-05-17
Greetings,
 
I'm having a real problem getting Ubuntu tto install properly on my old Intellistation workstation. It is a 6850 series; it sports 2 Xeon hyperthreadable processors at 2.8GHz on a 400MHz FSB and 2 gigs of PC 800 ECC RDRAM. Although it has an integrated dual-channel LVD 160 SCSI host adapter on the motherboard, I have added a dual-channel Adaptec 39320 LVD 320 host adapter card into one of the dual "64-bit" PCI-X slots that are on it. In the past, Windows always profited from the extra hard disk speed and I see no reason that Unbutu won't as well. However, I can't get Ubuntu to boot after it's installed.
 
I think I've tried everything: I tried turning back on the intergrated SCSI circuitry and physically removing the additional card, but the same thing happens - on BOTH channels. Same with the add-in card; using either of the channels results in the same problem. The documentation with the add-in card recommends booting with the "B" channel, even though the default setting highlights the "A" channel as the boot device; nevertheless, I tried it both ways to no avail.
 
I really would like to get Ubuntu up and running on the this old workstation now that I've replaced it with a new(ish) workstation with 2 quad-core Xeons in it. I recognise that I HAVE to have a Windows machine for my work, but I don't have to like it - and I don't. The old machine runs Ubuntu off the CD-ROM like lightning; off the hard drive it'll probably be faster than Windows on a dual quad-core Xeon machine with a 1333MHZ FSB, I'll bet.
 
Anyway, here are the details of the error, so one of you kind and gentle Ubuntu uber-geeks can suggest what will fix it for me. I'm not much good at Linux yet, but I intend to be, mainly becasue Windows is really starting to annoy the thing-a-ma-jig out of me.
 
Ubuntu (v. 9.04) seems to install well enough and everything goes well until the re-boot and then it just halts at:
 
**GRUB Hard Disk Error**
 
If I put the disk back in a use the "Boot to the First Hard Drive" option it seems to start to load but it times-out waiting for the root device, and ends up giving some "common problems" to consider.
 
I did some reading around these forums and located a tool called **Super Grub Disk **and ran in **Auto MBR **repairmode and then re-boot in the **Recovery Mode **and managed to display the following error messages:
 
**[ 21.870754] sd 2:0:0:0: [sda] Write Protect is off**
**[ 21.872603] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, support DPO and FVA**
**[ 21.872675] sda: sda1 sda 2 <sda5 >**
**[ 21.894226] sd 2:0:0:0: [sda] Attached SCSI disk**
**[ 21.894685] sd 2:0:0:0: Attached scsi generic sg1 type 0**
**Done.**
**Gave up waiting for root device. Common problems:**
**- Boot args (cat /proc/cmdline)**
**- Check rootdelay= (did the system wait long enough?)**
**- Check root= (did the system wait for the right device?)**
**- Missing modules (cat /proc/modules; ls /dev)**
**ALERT! /dev/disk/by-uuid/randomlygeneratedalphanumericindentity does not exist. Dropping to a shell!**
 
**BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)**
**Enter 'help' for a list of built-in command.**
**(initramfs) [ 33.388032] scsi3 : Adaptec AIC79XX PCI-X SCSI HBA DRIVER, Rev 3.0**
**[ 33.388035] <Adaptec 39320 Ultra320 SCSI adapter>**
**[ 33.388036] aic7902: Ultra320 Wide channel B, SCSI Id=7, PCI 33 or 66 MHz, 512 SCB's**
 
Anybody have any ideas on how to fix this installation?
 
TIA,
 
- Geoff

---

