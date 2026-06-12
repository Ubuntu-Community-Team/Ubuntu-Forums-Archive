---
title: "Hello, I need help with power managemet."
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by EnlistedSquire on 2008-01-31
Hi,

First post so hello.

Having installed and used a couple of different distros for all of five minutes in the past, this week I've decided to look at migrating my main PC usage from XP to Linux.

After a few false starts I've got an Ubuntu desktop with Compiz set up and it's ticking along quite nicely except for one problem I've been unable to solve.

Basically, Linux won't boot with any kind of acpi support except for acpi=ht (I have a HT Pentium 4). I've tried a hundred different combinations of switches with the same outcome - it just hangs during loading of the kernel.

This wouldn't be a problem apart from the fact I've also been totally unable to get APM to work. If I try suspending the PC it just drops to a "screen locked" dialogue and when I unlock it I get a pop up message saying there was an error.

I've tried adding apm=on to the kernel options, adding apm as a module to load and every possible combination of BIOS settings.

I did come across tuxonice and had a go at recompiling a kernel with it but being a noob I'm not sure if I did it right and it didn't work.

Does anyone have some suggestions that might be a bit "out of left field" to get some kind of suspend/hibernation working because I feel like I've tried everything.

I should mention, all ACPI type stuff works fine under Windaz.

Thanks.

Darren.

Specs:

Ubuntu Gutsy / Windows XP dual boot.
Pentium P4 HTT 3.6GHz
2 GB DDR2
GeForce 7800 GTX
ASUS P5GD1-FM motherboard (a Fujitsu custom job, BIOS is the latest release).

---

### Post by EnlistedSquire on 2008-02-01
Just a bump.

Thanks.

---

### Post by oldsoundguy on 2008-02-01
isn't your hyperthreading determined by the bios and the onboard chipset?  Mine is on my MSI board. I have a HT 3.06, but am running XP on it right now because of hardware/software that I need to be able to use that is, at present, unsupported in Linux.

---

### Post by EnlistedSquire on 2008-02-02
Hi oldsoundguy,

I do have a BIOS setting to enable/disable hyperthreading but even with it enabled, Ubuntu only sees one CPU thread in System Monitor without me using ACPI=HT.

---

