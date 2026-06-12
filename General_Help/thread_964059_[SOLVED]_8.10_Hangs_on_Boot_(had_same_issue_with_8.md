---
title: "[SOLVED] 8.10 Hangs on Boot (had same issue with 8.04)"
date: 2008-10-30
forum: General Help
---

### Post by chez17 on 2008-10-30
I'm using a Thinkpad T60. I just upgraded to 8.10 and I am having the same issue I had with 8.04. When I boot up my computer, the boot hangs about half the time. Sometimes it boots fine, sometimes it just hangs. It always stops on this:

"ACPI: Checking initramfs for custom DSDT"

Why does this stop it from booting? Is there any way around this? I know there must be other people with this issue, any ideas?

Thanks,
Dave

---

### Post by Titan8990 on 2008-10-30
From the grub menu highlight the Ubuntu that you boot and hit "e".

From the edit screen highlight the "kernel" line and hit "e" again.

At the end of that line add:

acpi=off

That should fix it for you.

---

### Post by chez17 on 2008-10-30
I guess I should have specified that I have tried that, but for some reason that makes my computer run painfully slow. Any other ideas?

---

### Post by Yellow Pasque on 2008-10-30
> **Titan8990 said:**
> From the grub menu highlight the Ubuntu that you boot and hit "e".

From the edit screen highlight the "kernel" line and hit "e" again.

At the end of that line add:

acpi=off

That should fix it for you.
Turning ACPI off on a laptop probably isn't a good idea. A better way to work around this issue is to add the *nolapic_timer* flag to the kernel line.

---

### Post by chez17 on 2008-10-30
> **Temüjin said:**
> Turning ACPI off on a laptop probably isn't a good idea. A better way to work around this issue is to add the *nolapic_timer* flag to the kernel line.

Just to double check, did you mean "nolapic" or "noacpi"?

---

### Post by Yellow Pasque on 2008-10-30
nolapic_timer
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt#1299](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt#1299)

---

### Post by chez17 on 2008-10-30
Thanks so much. Just out of curiosity, what does this option do. I have tried google but it just gives me results that show people with similar issues to me.

---

