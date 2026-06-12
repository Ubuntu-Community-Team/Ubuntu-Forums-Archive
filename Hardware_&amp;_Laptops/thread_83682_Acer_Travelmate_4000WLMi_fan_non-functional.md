---
title: "Acer Travelmate 4000WLMi fan non-functional"
date: 2005-10-29
forum: Hardware &amp; Laptops
---

### Post by dangerjunkie2002 on 2005-10-29
Hi,

I did an upgrade from Hoary to Breezy recently on my Acer Travelmate 4100WLMi (1.5GHz Pentium-M, Intel 915GM graphics, Centrino 2200BG WLAN). Yesterday I had to boot into Windows to run a specific application at work and I noticed the Travelmate's (very quiet) fan running when I put my hand near the air outlet. It's just dawned on me that the fan hasn't been running at least since I upgraded to Breezy and may not have run with Hoary either (or Linux's CPU speed management is so good the machine doesn't get hot enough for the fan to kick in but I doubt that as it got really hot outside the other day)

I am booting with the kernel line:

/vmlinuz-2.6.12-9-686 root=/dev/hda5 ro noapic quiet splash

The noapic is needed to get the machine to boot at all and if it isn't there the boot process hangs at the "Uncompressing Linux... OK, booting the kernel" stage. When the machine is at the GRUB menu the fan is running.

I would be very grateful for any advice you could offer as to what I should do before I melt my laptop down.

Thank you,
Paul.

---

### Post by dangerjunkie2002 on 2005-10-29
Update:

I was advised to check the contents of /etc/default/laptop-mode and ENABLE_LAPTOP_MODE is true. I also changed the corresponding entry in /etc/default/acpi-support to true as well but no luck.

I've been playing with kernel options and:

* noapic - Machine boots but fan doesn't work.

* nolapic - hangs at boot

* noapic nolapic - boots but no fan again and ethernet (Broadcom 4400) doesn't work

* acpi=on apm=off - hangs at boot

* acpi=off apm=on - boots, fan works but now ethernet (Broadcom 4400) doesn't work and /var/log/messages complains that apm is not present in the BIOS

This problem seems to be very similar to res_overloard's problem here [http://ubuntuforums.org/showthread.php?t=83770](http://ubuntuforums.org/showthread.php?t=83770)

I don't know if it's relevant but I do get loads of lines in /var/log/messages like these which I believe are due to the machine having a smart-battery rather than a regular laptop one. 

Kernel: ACPI-0362: *** Error: Looking up [Z00B] in namespace, AE_NOT_FOUND

Kernel: search_node dffe2e80 start_node dffe2e80 return_node 00000000

Kernel: ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node dffe2e80), AE_NOT_FOUND

Thanks,
Paul.

---

### Post by res_overlord on 2005-10-31
Does this happen when you are on AC power, battery, or both?

I posted a solution to my problem on the thread you referenced, but I don't feel confident it will work for you.

Regards, 

Joe

---

