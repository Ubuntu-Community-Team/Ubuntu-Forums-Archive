---
title: "System won't boot without acpi =off, noapic, and nolapic"
date: 2020-03-04
forum: Hardware
---

### Post by dloszewski on 2020-03-04
Hello,

I'm running Kubuntu 18.04 on a Dell Precision 7530 ([https://www.dell.com/support/home/us/en/04/product-support/servicetag/0-UURxeEFEeDRqZXBwQ09jblNOVVJXdz090/overview](https://www.dell.com/support/home/us/en/04/product-support/servicetag/0-UURxeEFEeDRqZXBwQ09jblNOVVJXdz090/overview)) and have been having issues with every flavor of Ubuntu thus far including trying Fedora/Red Hat.

Previous to today with the Kubuntu installation which I plan on using as that is my primary Ubuntu flavor, when rebooting the system I would get a black screen when shutting down.   I was able to deal with that as I don't reboot my system much but today I had a power outage and my system powered off.   When I attempted to power back on I was not able to boot, it would get to the grub screen and then go to a black screen.   

I had originally though it was a display driver issue because I have Nvidia Optimus which I have disabled via the BIOS but even after putting nomodeset it would not boot.  I then started going through the different boot options and found that the combination of acpi=off, noapic, and nolapic would allow me to boot the system properly although only after getting a bunch of ACPI errors.  I found this out after trying to boot my ISO stick which would also not boot without choosing these options, previous to today however I had no problem booting off a usb ISO stick.  

Can anyone tell me how I can further troubleshoot this?  This is pretty much a brand new laptop.   I had some luck with Fedora but after running through updates that also stopped booting.   Not sure if I'm looking at a hardware issue here or some kind of driver issue. 

Let me know if there's any further information I can provide.  

Thanks,
Dave

P.S. Oddly enough it only seems to boot with the above settings if legacy boot is enabled.

---

### Post by EuclideanCoffee on 2020-03-05
Hi, I supported this exact model in production. I have notes that I can send you, but I'll have to find them.

Essentially what I did was go into BIOS, set the device from RAID to ahci and secure boot. I disable legacy and enable UEFI. Then I enabled Nvidia (this is the feature of the model you're using, I'm surprised you would disable it).

Once Nvidia is enabled, I would install Ubuntu on a secure boot and set to install Nvidia drivers upon install. I would set the key and be able to boot without kernel parameters.

Now the trick is once Nvidia drivers are installed, they have conflicts with acpi. So I set acpi kernel parameter to something. I think it's either off or another setting. You can check for yourself, or I can send you my notes later today,

---

