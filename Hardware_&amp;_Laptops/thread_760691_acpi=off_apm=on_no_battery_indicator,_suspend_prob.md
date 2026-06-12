---
title: "acpi=off apm=on no battery indicator, suspend problems"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by aptalca on 2008-04-20
I am using a Fujitsu Lifebook N3010 laptop that was manufactured in 2003.

I installed Gutsy for the first time and it took 7+ minutes to boot to login page.

I got rid of quiet and splash and realized it was getting stuck on 3 acpi related things for 1-2 min each.

then I added acpi=off and apm=on and it booted in 1 minute

but there is no battery indicator when I unplug the ac, and there is no battery tab in power management. Suspend does not work, It tries to do it and then takes me back to the login window. Hibernate happens, but I cannot resume. Shutdown and restart work with no problems

Then I saw in one thread that I should add apm in etc/modules
But that resulted in a total system crash during boot due to fsck. I had to start with live cd and edit modules and take out apm.

Now when I type in apm, apmd or xapm in terminal, I keep getting a segmentation fault.

I am in need of help

Thanks

---

