---
title: "Loss of network access"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by lagger on 2006-04-04
I've been running Ubuntu on a Dell Inspiron 5000e for about 4 months with no notable problems. Last night, however, I shut down my machine since I share its wireless card with a second laptop that runs Windows XP. I ran the XP machine for a bit and then put the wireless card back in my Linux box. This is something I've done many times with no problems.

For some reason, however, I no longer have network access. During boot-up, everything proceeds normally except that "Waiting for network interface to come up" fails.

My first thought was that my wireless card had a problem. However, when I put it back in the Windows box, it found my network with no issue. 

I've tried booting up my Ubuntu machine with a cabled ethernet connection rather than the wireless card. Again, the network connection fails to come up. 

I consulted a friend much more knowledgeable that me. He had me look at /var/log/messages and then to run $ dmesg to see if there were any errors. The only things that he thought looked a little strange were these:

ACPI: Looking for DSDT in initrd...not found! not found!

ACPI-0295: *** Error: Looking us [STAT] in namespace, AE_ALREADY_EXISTS
ACPI-0508: *** Error: Method execution failed [\_SB_.BAT0._BST] (Node d7b21160), AE_ALREADY_EXTSTS

My friend thought these messages indicated that ACPI might be causing the problem, but then he realized that my laptop (~6 years old) predates ACPI. Nevertheless, he walked me through the process of turning off ACPI in the kernel, but the result was the same.

A couple other points I should mention: I've tried booting under 2 different kernel versions and I've tried putting my wireless and ethernet cards in different PCMCIA slots.

If anyone has any solutions or suggestions, I would be grateful.

Thanks!

---

### Post by waster on 2006-04-04
6 years old? maybe you're laptop is screwed. try a live CD, e.g. Dapper  Flight 6 Live, or Knoppix.

---

### Post by lagger on 2006-04-04
Thanks for your suggestion. I happened to have a Puppy Linux CD on hand, so I tried it. Same problem. It seems you may be right that it's the sign of a dying laptop.

---

### Post by waster on 2006-04-05
never heard of Puppy. Use the most recent distro you can to ensure best hardware detection.

---

