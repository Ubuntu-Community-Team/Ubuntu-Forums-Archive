---
title: "Brightness adjustment is not working properly,"
date: 2012-08-12
forum: Hardware
---

### Post by r3n3b4rb0s4 on 2012-08-12
Hello there, 

I am using Ubuntu 12.04 on a Samsung Laptop (300e4a-ad1 model). To get brightness adjustment through multimedia keys working properly i've ever used these lines on /etc/default/grub file:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux acpi_backlight=vendor enable_mtrr_cleanup splash"
GRUB_CMDLINE_LINUX=""

```

Until the kernel 3.2.0-26-generic it was ok but after any kernel update i can't adjust brightness using the newer kernel through multimedia keys. With acpi_osi=Linux acpi_backlight=vendor it doesn't change nothing and without it or with acpi_osi=Linux acpi_backlight=legacy, the environment is crashing when i try to change the brightness.

I think that it's not related to kernel as i compared the both config files, dmesg and modules. Anybody seen or is experiencing the same problem?

Thank you.

---

### Post by r3n3b4rb0s4 on 2012-08-13
Hello,

I was able to fix the issue by adding "blacklist samsung_laptop" to the file /etc/modprobe.d/blacklist.conf, everything is working fine now. I am really unsure about the reason of this module cause those issues, as it was already loaded on older kernels.

Moderation, feel free to close this ticket as a resolved issue.

Thank you.

---

