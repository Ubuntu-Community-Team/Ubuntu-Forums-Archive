---
title: "Boot problem"
date: 2008-09-24
forum: General Help
---

### Post by _Mike on 2008-09-24
Hi, I recently installed Ubuntu 8 (alternative CD) for the first time, (the live CD didn't work). After selecting Ubuntu from the grub menu, the screen freezes like [this.]("http://img246.imageshack.us/my.php?image=dscn0295om8.jpg")
I've never properly used linux before, so any help would be really appreciated.

I don't know if this is related, but just after I select from the grub menu, "MP-BIOS bug: 8254 timer not connected to IO-APIC" flashes for a second before moving on (it freezes a couple of seconds after this).

---

### Post by porchrat on 2008-09-24
It could be an ACPI problem I suppose, that might explain why the normal liveCD didn't install.

Try running the liveCD and once you get to the menu after you've selected your language press F6.

You then add "noapic" and "acpi=off" to the end of the line.  If it boots the liveCD you then need to add those options to the end of the line containing your ubuntu information (the line should end with "quiet splash" in your /boot/grub/menu.lst file, but we can deal with that if this actually works.

I hope this helps.

---

### Post by _Mike on 2008-09-25
I tried adding 'noapic' and 'acpi=off' to boot options (on the live CD) but it kept repeating:
> ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 Frozen
ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384
in
ata1.00: status { DRDY }


It would constantly output that every 30 secs. Every now and then it would also output
> 
Buffer I/O error and device sda, logical block 0
Buffer I/O error and device sda, logical block 1
Buffer I/O error and device sda, logical block 2
Buffer I/O error and device sda, logical block 3


So, no luck :(

I alos tried adding those options on the alternate CD, but it ended up not doing anything.

---

### Post by oilchangeguy on 2008-09-25
> **_Mike said:**
> Hi, I recently installed Ubuntu 8 (alternative CD) for the first time, (the live CD didn't work). After selecting Ubuntu from the grub menu, the screen freezes like [this.]("http://img246.imageshack.us/my.php?image=dscn0295om8.jpg")
I've never properly used linux before, so any help would be really appreciated.

I don't know if this is related, but just after I select from the grub menu, "MP-BIOS bug: 8254 timer not connected to IO-APIC" flashes for a second before moving on (it freezes a couple of seconds after this).

computer specs please.

---

### Post by _Mike on 2008-09-25
OS: Windows XP (On another partition)
RAM: 2gb
HDD: 300GB
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
ATI Radeon HD3650

---

### Post by _Mike on 2008-10-23
I've decided to start trying again. I can get Ubuntu 7 to install and run from the live CD, so it must be something in Ubuntu 8. I've read that there might be some compatability issues between Ubuntu 8 and ATI, could that be what's causing it?

---

### Post by _Mike on 2008-10-23
I've discovered that the exact same problem (look at the picture in the first post) happens with the latest version of Fedora, but Fedora 8 works fine. So could it be a kernal error or something?

---

