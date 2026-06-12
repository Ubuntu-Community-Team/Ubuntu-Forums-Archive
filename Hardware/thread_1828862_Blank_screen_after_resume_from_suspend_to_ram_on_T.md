---
title: "Blank screen after resume from suspend to ram on Thinkpad X31."
date: 2011-08-19
forum: Hardware
---

### Post by noteventime on 2011-08-19
I am having issues getting a Thinkpad X31 running narwhal to resume after a suspend to ram. I tried pinging the machine without response, suggesting the system hangs or at least doesn't resume wifi. I tried turning the system off "blindly" (meaning I tried executing "sudo poweroff") without success, which also suggests the system actually hangs.

Doing the usual suspend debugging got me two "hash matches", one pci device which turned out to be a "Ricoh Co Ltd R5C552" Firewire device. I tried unloading "firewire_ohci" and "firewire_core", which did not change anything.

The second one was a "acpi LNXVIDEO:00", which I am not sure what it means (there is an old thread on kerneltrap about a similar issue with LNXVIDEO:00, but nothing that helped here). As the name suggested it might be related to video I tried stopping gdm/X and running s2ram, with the same result as before.

These tests were run on a ~ppa-kernel/mainline 2.9.39 kernel, though the original 2.9.38 had identical issues (though I did not do pm_trace on 2.9.38). lspci/glxinfo report the IGP as ATI Radeon Mobility M6/R100 RV100 4C59 (I just realised I had been working under the assumption that it was an Intel IGP, I'll start looking into this). 

The suspend process is generally somewhat wonky, with the backlight turning off some of the time and sometimes, rather than a blank screen, one has a screen with some spotted white vertical stripes. 

Thanks in advance for any suggestions.

---

