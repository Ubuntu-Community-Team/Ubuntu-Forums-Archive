---
title: "What happened to my computer!? (ACPI)"
date: 2006-03-14
forum: Hardware &amp; Laptops
---

### Post by el3ktro on 2006-03-14
Ok I have a really strange issue. I have a NForce 4 mobo, and I'm running on Dapper (but it doesn't have to do with Dapper, thats for sure). I didn't do any updates on Dapper for 3 days now. My computer was running perfectly in Dapper, and in Breezy for months, and with Gentoo before - NO problems at all. As I said, I didn't do ANY updates the last three days, nor did I change ANYTHING in my configuration. My computer was working fine until yesterday evening. Today, I powered on my PC, and it suddenly won't boot. It said "Uncompressing Linux", and that was it. Hmm, I booted the rescue kernel, it booted until it said something about ACPI, and then it stopped. I ran a full memtest, everything went fine. I tried to boot from some other Linuxes, like Knoppix, an Kubuntu LiveCD, a Gentoo install CD - all with the same result, they all wouldn't boot suddenly. Well until I booted the Gentoo CD with noapic noacpi apic=off acpi=off (I wasn't sure about the extact kernel options, so I entered all four) - and Gentoo suddenly booted. I mounted sda1, changed the GRUB booting line for Ubuntu, and now Ubuntu also boots again with APIC/ACPI turned off.

What the hell happened? How can ACPI suddenly, from one day to the other, over night when the PC is turned of, stop working? I did NOTHING on my PC, no updates, no config changes, no hardware changes - it's all the same. Yesterday I was learning for university and all I did was displaying a few PDFs for my classes - nothing fancy. My PC has good cooling, it's all high quality components - any ideas somebody? I'm afraid my mobo is somehow broken, but how the hell. The only thing that I COULD image is that on my Northbridge, I replaced the loud cooling fan with a (quite big) passive cooling device, but didn't have problems with that ever since. The mobo has no internal graphics, so the northbridge shouldn't get that hot...


Tom

---

### Post by el3ktro on 2006-03-14
What the ... I just reloaded the default BIOS settings, rebooted, then configured the BIOS as it was before and now it works again with ACPI enabled. Damn computers can be strange don't know how that happened ...

Tom

---

