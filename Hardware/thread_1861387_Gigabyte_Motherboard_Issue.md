---
title: "Gigabyte Motherboard Issue"
date: 2011-10-15
forum: Hardware
---

### Post by d4m1r on 2011-10-15
This isn't directly related to Ubuntu as it happens because the OS boots (and before the grub menu for that matter) but to get my PC to boot in Ubuntu, I have to boot it up, and then restart  it...Why? Because I have an eSata external HDD that doesn't startup  until AFTER the BIOS passes. I enabled ACHI and SMART monitoring in the  BIOS, so after the BIOS passes, ACHI runs a quick SMART scan and the  eSata HDD fails because it doesn't power on fast enough ("SMART check  failed" message). I restart the system, BIOS clears as usual, ACHI/SMART check  passes fine because drive is booted and off to Ubuntu or Windows 7 I  go.....

Is there anything I can do about it? Its a Gigabyte motherboard and it  does have a "Delay for HDD" option, but then the BIOS only waits up to  15 seconds and it doesn't boot the eSata HDD at that point either...

Note - I don't want to disable SMART monitoring and specific Gigabyte model # is GA-MA78GM-S2H.[SIZE=1][COLOR=#666666]

[/COLOR][/SIZE]

---

### Post by d4m1r on 2011-10-16
70 views and no ideas?:confused:

---

### Post by oldfred on 2011-10-16
I have a Gigabyte but a version for Intel. I turned off a fastboot option (but not for your reason). Does that make any difference for you?

---

### Post by d4m1r on 2011-10-16
> **oldfred said:**
> I have a Gigabyte but a version for Intel. I turned off a fastboot option (but not for your reason). Does that make any difference for you?

Haven't tried that...I know I have it enabled, but what does it do exactly?

My guess is it won't make any difference because that still happens at the BIOS level  and the SMART check gets done after that but I'll try it anyway.

---

### Post by bobbennett on 2011-10-16
I have a recent Gigabyte motherboard and ran into trouble booting from USB.  Turns out it has to be one of the FAT* filesystems.  Not sure if that would be the issue with your eSATA boot or not but it may be worth checking.


bob

---

### Post by d4m1r on 2011-10-16
Sorry but the filesystem of the external HDD is of no relevance in this case.

---

