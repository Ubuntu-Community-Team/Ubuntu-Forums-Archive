---
title: "ACPI states trouble with WOL"
date: 2013-06-22
forum: Hardware
---

### Post by believe on 2013-06-22
Hello,

I am using a Foxconn NT-A3500 with an AMD Fusion E350 Processor with 2GB of RAM as a media and file server. It would be nice to be able to wake it up from standby or power down with a wake-up packet over ethernet. 

I tried one of the various tutorials on the internet that set up WOL with ethtool. This kind of works for the S3 (standby) state. Unfortunately, after waking the computer up, kswapd0 uses lots of cpu making the fan spin. What could lead to this behaviour? 

Alternatively I enabled S5 for LAN in the BIOS and tried to wake the computer after soft-off. However it appears that the computer is shut fully down, including the network interface, so waking up is not possible. Interestingly, /proc/acpi/wakeup always outputs the following status:
```
cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
SBAZ	  S4	*disabled  pci:0000:00:14.2
P0PC	  S4	*disabled  pci:0000:00:14.4
UHC1	  S4	*enabled   pci:0000:00:12.0
UHC2	  S4	*enabled   pci:0000:00:12.2
USB3	  S4	*enabled   pci:0000:00:13.0
USB5	  S4	*enabled   pci:0000:00:16.0
UHC6	  S4	*enabled   pci:0000:00:16.2
UHC7	  S4	*enabled   pci:0000:00:14.5
PE20	  S4	*disabled  pci:0000:00:15.0
PE21	  S4	*disabled  pci:0000:00:15.1
PE22	  S4	*disabled  pci:0000:00:15.2
UHC4	  S4	*enabled   pci:0000:00:13.2
```

Is there some kind of command to re-read the supported S-states? I even tried disabling S4 in the BIOS but the output was still the same. So this is probably a bug in the BIOS?

Thanks for your help!

---

