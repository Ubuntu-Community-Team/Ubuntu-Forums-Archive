---
title: "Laptop won't detect new battery.  Suggestions?"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by oldsmobile_mike on 2008-02-19
Hi,

I had a laptop with a bad battery in it.  Each time I powered up, I would be greeted by the usual messages "Your battery has a very low capacity (28%) which means that it may be old or broken", etc., and, true to form, as soon as I unplugged the AC adaptor, the laptop would cut off.

Today, however, I got a new battery (yay!), but it's not being detected.  Battery Charge Monitor, Power Prefs, and kpowersave all report "no battery present".

Additionally, dmesg shows "ACPI: Battery Slot [BAT0] (battery absent)".

I have tried the sequence of commands that I found here in the forums:

sudo rmmod acpi_sbs
sudo rmmod battery
sudo modprobe battery

but on the first line I get the error "ERROR: Module acpi_sbs does not exist in /proc/modules"

I also tried booting from the LiveCD, just to see if that made any difference, but it didn't - it still said "No battery present".

Of course, as you can guess - the laptop runs fine on the new battery, if I unplug the AC adaptor, and at that point all those programs report that it's running on battery, with "0% charge remaining".

I see these other instructions for rebuilding the kernel, but that seems extreme, and my particular laptop, a Sager 5600P, isn't even listed on the ACPI-DSDT page ( [http://acpi/sourceforge.net/dsdt/view.php](http://acpi/sourceforge.net/dsdt/view.php) ).

I have already updated to the latest firmware that's supposed to solve any battery-related problems.

FYI, I also followed these steps:  cat /proc/acpi/dsdt > dsdt.aml and iasl -d dsdt.aml > dsdt.asl , and got a lot of information, if you suggest I post it, I can.

Please help!

Hummm....  I am beginning to think that it may just be that the new battery is defective, somehow...  :-/

---

### Post by tuque on 2008-02-19
I agree this is more than likely to be a hardware related problem. Can you find someone with the same laptop who will let you try their battery in your machine?

---

### Post by oldsmobile_mike on 2008-03-27
I meant to go back and close this thread out...  turned out to be a defective battery (the new one was pretty much DOA).  Replaced it with a different one, and it worked fine!

---

