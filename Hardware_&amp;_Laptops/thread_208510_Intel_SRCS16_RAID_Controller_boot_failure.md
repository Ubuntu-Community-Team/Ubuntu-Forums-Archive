---
title: "Intel SRCS16 RAID Controller boot failure"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by lordelph on 2006-07-03
I've done a server install on a system using an Intel SRCS16 RAID Controller. 

The system installs OK, using the "LAMP Server" installation method, but on booting I get these messages on the console

[LIST]
[*] [42949380.070000] sda: asking for cache data failed
[*] [42949380.070000] sda: assuming drive cache: write through
[*] [42949380.070000] sda: asking for cache data failed
[*] [42949380.070000] sda: assuming drive cache: write through
[*] [42949383.660000] request_module: runaway loop modprobe binfmt-0000
[*] [42949383.660000] request_module: runaway loop modprobe binfmt-0000
[*] [42949383.660000] request_module: runaway loop modprobe binfmt-0000
[*] [42949383.660000] request_module: runaway loop modprobe binfmt-0000
[*] [42949383.660000] request_module: runaway loop modprobe binfmt-0000
[/LIST]

The system then locks up.

I've installed the latest available bios for the card (713R), but now I am at a loss how to proceed...any pointers welcome.

---

### Post by ssjoholm on 2006-09-02
Hi,

I don't have that RAID controller, but I found following info;

Intel SRCS16 and SRCS28X Serial ATA RAID Controller PCI cards — real hardware RAID. These are six-port PCI and eight-port PCI-X cards (respectively) for servers, based on an LSI Logic MegaRAID chipset, driving SATA-I output using Silicon Image SiI3112A SATA-I chips (one for each channel pair) and an Intel GC80302 or IOP331 (respectively) dedicated I/O processor with 64MB or 128 MB of ECC SDRAM (respectively) for processing XOR logic. Use the kernel's "megaraid2" driver (For LSI Logic MegaRAID). The Silicon Image chips are not the system-facing chipsets (1 2), and so don't determine driver support. An optional battery-backup daughterboard is available.

source:[http://linuxmafia.com/faq/Hardware/sata]("http://linuxmafia.com/faq/Hardware/sata") 

It's seem that "megaraid2" has to be inserted to the kernel, maybe this should be checked if it's loaded correctly.

---

### Post by lordelph on 2006-09-04
I wound up switching to Debian stable for this box, which worked fine, even with the megaraid driver. The megaraid2 driver was required to see the current drive status though. I did this to ensure it was available at boot

echo megaraid2>>/etc/mkinitrd/modules
mkinitrd -o /boot/initrd.img-megaraid2 

(see [http://wiki.debian.org/LinuxRaidForAdmins](http://wiki.debian.org/LinuxRaidForAdmins))

---

