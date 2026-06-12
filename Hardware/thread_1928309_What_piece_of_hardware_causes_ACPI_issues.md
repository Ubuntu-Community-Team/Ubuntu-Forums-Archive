---
title: "What piece of hardware causes ACPI issues?"
date: 2012-02-19
forum: Hardware
---

### Post by DukeBoxer on 2012-02-19
I built a computer last year, Asus P7P55d-e pro MoBo, core i5-760 proc, gskill ram, nvidia 460gtx video card and the only way I can boot it and keep it running is if I use ACPI=off in the grub config. Because of this problem I RMA'd just about everything I got except for the processor and it is still having the problem. The original install was 10.10, then I did a fresh 11.04 then an upgrade to 11.10...I also have tried daily builds of 12.04 on USB and still can't get it to even boot without a kernel panic.

My questions are these 1...is the ACPI issue with the processor itself like I think it is (because that's the only piece I never switched out to test) and 2...does anyone else who runs this same processor get it to boot without "ACPI=off"

Just for reference before anyone asks I did install Win7 on it (just testing of course) with zero problems, so this is a Linux only issue. The distros I tried are Debian 5 and 6, Ubuntu 10.04, 10.10, 11.04, 11.10, 12.04, Mint 10, 11, LMDE and Fedora 14 (I think) and all had problems. Thanks for any help

-Josh

---

### Post by ahallubuntu on 2012-02-19
Generally, ACPI is a function of the chipset (and CPU) used on the motherboard and also of the BIOS design and settings.

With issues like yours, I'd look in the BIOS Setup for any settings related to ACPI or power management.  Also, if you have a Windows installation going on it now, I'd download the latest BIOS version from Asus (usually best to install these updates from Windows unless the BIOS has a "direct update from USB" function to do it without an operating system).  It could fix issues you have having in Ubuntu.

You might also play with SATA and RAID settings.  Just because ACPI=off is required to boot doesn't mean ACPI itself is the PROBLEM.

---

### Post by DukeBoxer on 2012-02-21
Thanks for the reply, I am going to go home today and write down anything about power management and ACPI in the bios and report back. I do not have a windows installation now, I just installed it at first to see if the problem was universal. I do know I have my SATA set to AHCI (I think those are the letters) and not IDE. I'll let you know later on. Thanks again

---

### Post by roelforg on 2012-02-21
Try acpi=force
Mine won't shutdown without, don't know why.
Might work as well on your pc.

---

### Post by DukeBoxer on 2012-02-21
ok, here goes...There is a star next to the choices that are set right now in the BIOS and the BIOS is up to date v.1602

Power Management - 

Suspend Mode - Auto *
               S1 (POS) Only
               S3

ACPI 2.0 Support - Enabled *
                   Disabled

ACPI APIC Support - Enabled *
                    Disabled

EuP Ready - Disabled *
            Enabled
(Not really sure what this is but it seems it has something to do with powering on the computer and Wake on LAN)

Hard Drive Configuration

Configure SATA as - IDE
                    RAID
                    AHCI *

Just a note, I don't think I've tried turning off ACPI 2.0 support yet but I will try it if it seems to be the reason for this problem.

And to roelforg: I can send the shutdown command to the box and you can hear everything sort of stop but it doesn't finish powering it down, I need to hit the power button so it will power off. Is this the same problem you're having?

---

### Post by roelforg on 2012-02-22
> **DukeBoxer said:**
> ok, here goes...There is a star next to the choices that are set right now in the BIOS and the BIOS is up to date v.1602

Power Management - 

Suspend Mode - Auto *
               S1 (POS) Only
               S3

ACPI 2.0 Support - Enabled *
                   Disabled

ACPI APIC Support - Enabled *
                    Disabled

EuP Ready - Disabled *
            Enabled
(Not really sure what this is but it seems it has something to do with powering on the computer and Wake on LAN)

Hard Drive Configuration

Configure SATA as - IDE
                    RAID
                    AHCI *

Just a note, I don't think I've tried turning off ACPI 2.0 support yet but I will try it if it seems to be the reason for this problem.

And to roelforg: I can send the shutdown command to the box and you can hear everything sort of stop but it doesn't finish powering it down, I need to hit the power button so it will power off. Is this the same problem you're having?
Adding acpi=force to your kernel cmdline will cause the kernel to send the acpi commands even when the checks say your pc won't accept it.
I sounds as if the system just halts; the acpi=force should fix this.

---

### Post by DukeBoxer on 2012-02-22
ok, I'll try that when I get home. Thanks!

---

### Post by DukeBoxer on 2012-02-23
Nope, still locks up with acpi=force. Now I am having a different problem all together that started yesterday and it seems to be with nvidia drivers, making gnome-shell window switcher and unity flash and lock up with Xorg pinned at 100+% cpu. weirdness

---

