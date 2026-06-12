---
title: "Ubuntu 8.04 beta hangs when boot on AC power"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by Olnex on 2008-04-19
When I boot while the laptop is on AC power, after the GRUB, I see:
ACPI: EC: acpi_ec_wait timeout, status = 0, expected_event = 1
      EC: read timeout, command = 128
If I use battery, booting is normal, even after booting I plugged in the AC.
Removing -quiet does not help.
My laptop is Sony VAIO VGN-C25G
Thanks

---

### Post by Olnex on 2008-04-19
I also have this problem with Release Candidate, can it be resolved in the final release?

---

### Post by Meakeiok on 2008-04-23
Just want to say that I have the same problem on my Sony Vaio VGN-C2Z.
I can still boot into Ubuntu (also 8.04) using an older kernel 2.4 for example. So I think it&#8217;s a problem with the new kernel.
I hope there will be a kernel fix soon for this problem.

---

### Post by Olnex on 2008-04-23
i just read some messages from launchpad that this bug may not be fixed soon as it is nearly 24th April

---

### Post by Olnex on 2008-04-23
And I also wonder doesn't the kernel devs even test it before releasing, or is it just a problem that only certain Vaio models have?

---

### Post by Meakeiok on 2008-04-23
It seems like the problem is already known [http://bugzilla.kernel.org/show_bug.cgi?id=10222](http://bugzilla.kernel.org/show_bug.cgi?id=10222)

Maybe it is already fixed in the last kernel 2.6.25 (ubuntu uses 2.6.24 atm)

---

### Post by Cyynic on 2008-04-26
I found this Launchpad bug report that refers to this problem [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137")

it details testing a kernel patch (way over my head) but then it points out that removing 'quiet splash' from the kernel line in /boot/grub/menu.lst will solve the problem for now.

(amusingly the kernel developers couldn't reproduce the crash because they always remove those tags so they can troubleshoot)

This corrected the problem on my Sony Vaio VGN-N250E, hope it helps others until they come out with a kernel patch.

---

### Post by Olnex on 2008-04-27
Yes, that works for me, but I only removed "quiet" and I can still see a beautiful splash with text information below the "Ubuntu" logo and progress bar.

However, by doing this way, when I boot my laptop(or restart), at the very beginning, sometimes, not always, I can see something like "ACPI: bus type pnp registered..." and then it just hangs there, only pressing start button works, it happens sometimes.

---

