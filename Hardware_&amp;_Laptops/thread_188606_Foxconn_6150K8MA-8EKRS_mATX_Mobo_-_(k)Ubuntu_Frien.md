---
title: "Foxconn 6150K8MA-8EKRS mATX Mobo - (k)Ubuntu Friendly?"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by Xaeos on 2006-06-04
Hello all, I was perusing the HCL and saw no mention of this particular board.  I would like to know if anyone has experience with this Foxconn mATX mobo. [http://www.newegg.com/Product/Product.asp?Item=N82E16813186086](http://www.newegg.com/Product/Product.asp?Item=N82E16813186086) as it is currently on my to-buy list. I know it is a fairly new product, but it runs on the Nforce 430 platform and has a Marvell GigE ethernet chip. 

I'm not really interested in the onboard video, as I have a GeForce 7900GTX instead.   Think this board will play nicely with Linux?  Thanks

---

### Post by mips on 2006-06-04
Hard to say but my guess is that it would work.

---

### Post by cocoyriv on 2006-09-18
i use the same board. i wanted to install ubuntu 6.06 lts server into it using raid 5 but it won't boot or i would encounter errors. no problems when using raid 1. if any of you guys know how to install ubuntu on a raid 5 using this board, please share with me. thanks.

---

### Post by MJSOnline on 2006-09-18
It should work as I have the samish mb.  I too would like to know how to setup raid in Dapper.M

---

### Post by cocoyriv on 2006-09-19
guys, i got ubuntu server running on this board. my /boot is on raid 1 and the rest is on lvm on raid 5. pretty cool.

---

### Post by 36Joules on 2007-09-19
Another success story with this mobo, but only after a lot of gymnastics.  Briefly:

AMD Athlon 64 3400+ 2.2GHz
WinFast/Foxconn 6150K8MA mobo
Seagate 120GB PATA HDD x 2
Pioneer 8X DVDRW
1.25GB RAM
Using on-board nVidia GeForce 6150B + nForce 430

Had originally installed Dapper (6.06.1), but kernel upgrade via synaptics caused random hangs. Tried clean re-install with Feisty (7.04), but would also get random hangs.  Tried the various kernel acpi tweaks suggested on other threads here regarding the known double clock speed bug (noacpi, noapic, nolapic, noapictimer, etc) during live cd install, but no joy with the install process.  Also tried simpleMEPIS, openSUSE without luck - same random OS hangs despite multiple kernel boot tweaks.  NOT a component driver issue.  Even updated BIOS to latest version 58GW1P33 (7/2007) without Ubuntu success.

The only thing that allowed a proper install in the end was disabling ACPI **_AND_** APIC in the BIOS.  This allowed a LiveCD install without specific kernel flags.  Post installation, I re-enabled ACPI and APIC in BIOS (since I'm dual booting with Win XP which needs these options enabled) and then added the following kernel flags to GRUB:

noapic noacpi nolapic acpi=off irqpoll

This, believe it or not, is the only combination of installs and kernel flags that allow a stable Ubuntu gnome working environment on my hardware. All package updates now work, using the restricted glx nVidia drivers with great results, even with overclocking.

All in all, a very snappy budget linux box.  Hope this saves someone some time...

---

