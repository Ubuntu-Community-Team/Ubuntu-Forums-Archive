---
title: "ACPI not working Edgy EFT"
date: 2006-11-19
forum: Hardware &amp; Laptops
---

### Post by LDRoamer on 2006-11-19
I will start by saying I am really new to linux stuff and so have a lot to learn.

I have on old Compaq Armada 1750 that I am running Edgy Eft on. My problem is that the ACPI stuff does not function. I have checked the bios and ACPI is enabled (my only options there are enabled and disabled).  It works in windows XP and it also seemed to work when I had the testing version of Debian installed (ETCH). If enter the command "acpi -V" I get:

No ACPI support in kernel, or incorrect acpi_path ("/proc/acpi")

I checked and the folder /proc/acpi does not exist.  

I presume that simply adding the folder won't help as there must have to be configuration files in there as well. I also presume that the kernel does support ACPI.

Is there anyway to get the ACPI stuff working on my old laptop? I could go back to Etch when it becomes stable but I found configuring the Debian distribution much more difficult than with Ubuntu. Any help would be appreciated.

---

### Post by s2s2 on 2006-11-24
](*,) ACPI does not work on this laptop. I assume if Compaq, now HP, would have bothered to complete the ACPI code in the Bios, the laptop would (any developers want to have a crack at this?). I have the latest released bios for this laptop, it's 11/1999 (Fn+Esc, and Up and Down arrow key will give more info).

I have seen other posts (google 'ACPI Compaq Armada 1750') regarding your problem, and no one can make it work. I have Edgy Eft on a CD, and booting the Live version or choosing Install, does not make the fan work. It's best to use a bootable Setup CD, and turn off 'ACPI Enable'. Fn+F11 several times when turning the laptop on, resets/clears the CMOS.

I have upgraded mine, and am having some problems with data corruption (at least under W2K & XP), but I think it's related to continuing use of the original IBM 6.4 Gig HD/timing issues.

Good luck. APM mode will work the best though.

-s2

---

### Post by aeb1 on 2007-04-07
MSFT has its tracks all over the BIOS code. IMHO, they deliberately crippled the code so it only works with the M$ O/S. The only easy fix requires a soldering iron.  :mad:

---

