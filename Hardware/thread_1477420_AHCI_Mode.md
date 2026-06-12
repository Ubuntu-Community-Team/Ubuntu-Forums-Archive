---
title: "AHCI Mode"
date: 2010-05-08
forum: Hardware
---

### Post by MetalFanLiam on 2010-05-08
Hi guys I know this may not directly be related to Ubuntu itself however it is odd as this has never happened before.

I have Ubuntu 7.10 installed and it runs perfectly fine, all drivers etc work perfectly also. The computer itself is in RAID mode but with all 4 RAID channels disabled (I refuse to use any RAID arrays because I simply don't like them). However, my computer (Acer Aspire m3640/m5640, motherboard MCP73PV/630i) has greyed out the option for me to change the option from RAID mode to either IDE or AHCI. Since I do not use RAID at all, I want to change to AHCI but it is greyed out in the BIOS. This option wasn't greyed out before as far as I remember.

I also have Vista x64 installed on a SATA drive along with Debian and Ubuntu all partitioned. I also have an empty IDE drive attached which will be used for another operating system AFTER I have changed to AHCI mode. The SATA drive has the boot flag. I use GRUB to boot the operating system. My BIOS version from American Megatrends is R01-A3 (not the latest one, but the one I need to use).

My question is this, how could one possibly go about as to changing it to AHCI mode from RAID with the BIOS greying the option out. Or if not possible, how to make the BIOS ungrey the option (if there is another option preventing it from being changed or if the harddrives need configuring etc). I am not particularly concerned if the drives need to be wiped.

Thanks, Liam

---

### Post by seeker5528 on 2010-05-08
> **MetalFanLiam said:**
> I have Ubuntu 7.10 installed and it runs perfectly fine, all drivers etc work perfectly also. The computer itself is in RAID mode but with all 4 RAID channels disabled (I refuse to use any RAID arrays because I simply don't like them). However, my computer (Acer Aspire m3640/m5640, motherboard MCP73PV/630i) has greyed out the option for me to change the option from RAID mode to either IDE or AHCI. Since I do not use RAID at all, I want to change to AHCI but it is greyed out in the BIOS. This option wasn't greyed out before as far as I remember.

I don't see anything right off the bat on a quick search that shows what the bios options you have look like. My first thoughts would be...

A: The AHCI option is greyed out because you disabled ports. Don't know why this would be, but if SATA mode is set to something other than RAID, it's redundant to go in and disable ports.

B: Either you have some option selected that is not compatible with AHCI or there is another option that needs to be selected before AHCI can be selected. If this is the case it may be an option related to caching, the way the BIOS functions are accessed or something along those lines. 

Later, Seeker

---

### Post by MetalFanLiam on 2010-05-08
Thanks I will take another look.

The "Advanced chipset options" screen looks like this (with the SATA mode at the bottom):

[http://img186.imageshack.us/i/dsc00152lv.jpg/](http://img186.imageshack.us/i/dsc00152lv.jpg/)

Liam

---

### Post by seeker5528 on 2010-05-10
> **MetalFanLiam said:**
> The "Advanced chipset options" screen looks like this (with the SATA mode at the bottom):

[http://img186.imageshack.us/i/dsc00152lv.jpg/](http://img186.imageshack.us/i/dsc00152lv.jpg/)


Don't know looking at that, could be the memory remap feature that affects the ability to change the SATA mode.

Looking at google using "Acer Aspire m5640" as a search term as opposed to "Acer Aspire m3640/m5640", did produce a couple of results where people said they couldn't change the SATA mode. Didn't see anything indicating whether this was changed behaviour or whether it's just not an option.

If it was an option that was available before then I would expect hitting the 'F8' key to load the failsafe defaults would set it back to a configuration where it could be selected again.

BIOS updates may change how or if these options work as well.

Later, Seeker

---

