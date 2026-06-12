---
title: "SATA HDDs suddenly won't mount"
date: 2008-06-27
forum: Hardware
---

### Post by herorev on 2008-06-27
I have four hard disks, 3 SATA and 1 PATA. I'm running Kubuntu 8.04 64-bit.

After Ubuntu did an upgrade yesterday, I restarted my computer (due to an upgraded kernel), but one of my SATA HDDs wouldn't mount. I restarted and selected an older kernel, but then none of my SATA HDDs would mount. I tried a Kubuntu 8.04 32-bit live CD, thinking my Ubuntu install was funked, but I still couldn't mount any of my SATA HDDs. Everything was working fine before I restarted (though that may not be related).

The live CD gave me error messages like these:
**ata5.00 revalidation failed (errno=-5)**
*(same as above with ata5.01 and ata6.01)*
**Buffer I/O error on device sda1, logical block 0**
*(same as above with various devices and blocks)*
**ata6.01: status: { DRDY }**

At first I was afraid one of my HDDs went out. Then I was afraid my OS install was ruined. But now I'm guessing something like the motherboard is at fault. But I don't know how to figure out what it is that has the problem. What should I do?

---

### Post by Odrodzona-Sarmacja on 2008-06-27
My guess would be that BIOS is leaving hardware configuration up to plug&play OS. I would go into BIOS and check if BIOS has any issues detecting hard drives correctly. Baby steps ;)

---

### Post by ukripper on 2008-06-27
> **herorev said:**
> I have four hard disks, 3 SATA and 1 PATA. I'm running Kubuntu 8.04 64-bit.

After Ubuntu did an upgrade yesterday, I restarted my computer (due to an upgraded kernel), but one of my SATA HDDs wouldn't mount. I restarted and selected an older kernel, but then none of my SATA HDDs would mount. I tried a Kubuntu 8.04 32-bit live CD, thinking my Ubuntu install was funked, but I still couldn't mount any of my SATA HDDs. Everything was working fine before I restarted (though that may not be related).

The live CD gave me error messages like these:
**ata5.00 revalidation failed (errno=-5)**
*(same as above with ata5.01 and ata6.01)*
**Buffer I/O error on device sda1, logical block 0**
*(same as above with various devices and blocks)*
**ata6.01: status: { DRDY }**

At first I was afraid one of my HDDs went out. Then I was afraid my OS install was ruined. But now I'm guessing something like the motherboard is at fault. But I don't know how to figure out what it is that has the problem. What should I do?

Boot using live cd 
Can you first post your fdisk output:
```
sudo fdisk -l
```

and fstab:
```
cat /etc/fstab
```

---

### Post by herorev on 2008-06-27
Strangely, I got things working with the irqpoll kernel option. (The noapic and acpi=off options weren't enough.) I should have tried it before posting here, but why would I suddenly start needing this now? The only thing I can imagine is if the firmware for something was silently updated, but that seems pretty unlikely.

Thanks for the replies.

---

### Post by zyxnull on 2008-07-30
I've just discovered while installing a Toshiba Laptop that if the option "set hdd user password" is set in the BIOS, you'll not get access to the information on the partitions on harddisk, you won't be able also to modify the harddisk partitions.

---

