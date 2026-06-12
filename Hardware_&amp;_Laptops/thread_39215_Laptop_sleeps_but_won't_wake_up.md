---
title: "Laptop sleeps but won't wake up"
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by hyperboloid on 2005-06-03
I recently installed Hoary on an IBM Thinkpad T41. Install was flawless and everything just works, EXCEPT for suspend/resume. Yes, I followed all the HOWTOs I could find, and tried all the recommendations. In particular, I uncommented the line "ACPI_SLEEP=true" in /etc/default/acpi-support and added various options to the "# kopt" line in /boot/grub/menu.lst. Yes, I remembered to do "update-grub" each time, and rebooted, but to no avail. 

This is driving me crazy, and if I can't get suspend to work I'm going back to Gentoo, although I really like the ease and user-friendlinessof Ubuntu. 

Suspend works just fine, but resume does not. I get a blank screen and a locked keyboard, and have to power cycle and reboot. If anyone has figured out a solution to this, please reply.


[Note: I tried APM instead of ACPI, and it led to a disaster: I had to repair the hard drive with fsck in order to boot the system after everything crashed very hard after a suspend/resume.]

---

