---
title: "Power Management &amp; Dell Latitude CPx"
date: 2005-01-18
forum: Hardware &amp; Laptops
---

### Post by 8oluf7 on 2005-01-18
Installing Ubuntu Warty on my Dell CPx J650GT (dual boot with Win98SE) was a breeze, once I'd worked out how to prevent the installer destroying my Windows partition. 

Everything worked except power management. The battery state was reported as 0% and the machine wasn't switched off at the end of shutdown. 

Intel state that the 440BX chipset includes ACPI but trying the various suggestions elsewhere in the Ubuntu forums about ACPI and APM didn't work. 

So, in case anyone out there is using a similar machine, the solution in my case was to flash the BIOS with the latest version from the Dell website (going from version A05 to A16). Apparently, Dell held back ACPI functionality to maintain compatibility with Win98. This is only revealed in the text file that comes with the update!

BTW I also put pciehp and shpchp on the hotplug blacklist, as suggested in other postings, to get rid of the modprobe error messages during startup. Does this mean that I won't be able to hotswap the floppy and DVD drives? (Not that I'm in the habit of doing it because it doesn't work well in Windows on this machine.)

---

### Post by Deusiah on 2005-02-12
Hi, I have a Dell CSx, Like yours mine does not shut down or disply the remaining battery power.

I have also tried Ubuntu on another laptop and it did shut down correctly but it wouldn't display the remaining battery power so perhaps this an Ubuntu problem?

Don't you have a problem with Hotplug freezing your machine at startup? Also how are you for getting your CD/DVD/Floppy drive working, I have had no luck with mine whatsoever.

---

### Post by Deusiah on 2005-02-14
OK 8oluf7 I owe you a REALLY big thank you. Thanks to you my Laptop now powers down properly, the battery indicator works AND a problem I was having with a startup hotplug crash is gone!

After you talked about updating your BIOS for your CPX I wondered if there were any updates for my CSx. Sure enough there were so I flashed my BIOS and all of my problem were solved in an instant.

Thanks ever so much for putting the notion into my head. I very much doubt I would have considered updating the BIOS otherwise.

---

