---
title: "Waking from suspend and hibernate"
date: 2009-04-03
forum: Hardware
---

### Post by dignick on 2009-04-03
I've got problems with both suspend and hibernate.  These problems have been persistent through Ubuntu 6.06-9.04 beta.  The motherboard in the computer is a GIGABYTE GA-8PENXP.  There are no issues with sleep under Windows XP.

On suspend, no errors are given and the computer goes to suspend successfully.  On wake the computer starts to a blank screen with no errors, however in kern.log the following error is produced:
> Apr  3 14:53:05 study kernel: [   56.028033] ACPI: Waking up from system sleep state S3
Apr  3 14:53:05 study kernel: [   56.028358] ACPI: Unable to turn cooling device [f6c16db0] 'off'
Apr  3 14:53:05 study kernel: [   56.028418] pm_op(): pci_pm_resume+0x0/0x70 returns -16
Apr  3 14:53:05 study kernel: [   56.028422] PM: Device 0000:00:00.0 failed to resume: error -16
Apr  3 14:53:05 study kernel: [   56.028437] pci 0000:00:01.0: restoring config space at offset 0x7 (was 0x2a000f0, writing 0x22a000f0)

On hibernate, the following errors are produced in text mode:
> pm_op(): pci_pn_thaw+0x0/0x50 returns -16
PM: Device 0000:00:00.0 failed to thaw: error -16

On resume, the following errors are produced in text mode:
> pm_op(): pci_pn_restore+0x0/0x70 returns -16
PM: Device 0000:00:00.0 failed to restore: error -16


Anything I can try?

---

### Post by kestrel1 on 2009-04-03
What size is your swap partition? I think if this is too small it can impact on Hibernate.

---

### Post by dignick on 2009-04-04
Hmm possibly, 486mb with 1gb RAM.  However this doesn't explain suspend, which gives a similar error to hibernate.

---

### Post by kestrel1 on 2009-04-04
Could be related though.
Are you able to increase the size of the swap? However doing this can cause other problems.

---

### Post by brunogirin on 2009-04-04
I have the same problem when hibernating with Jaunty Beta on a ThinkPad T42 laptop with 1.3GB swap and 2GB RAM. How can I identify what device is reporting that error?

---

### Post by kestrel1 on 2009-04-04
With the Beta of Jaunty you may want to report a bug. I would think 1.3gb swap should be large enough, but you have to remember that when you hibernate you are trying to save running processes & you have 2gb RAM, so it may still not be enough.

---

### Post by brunogirin on 2009-04-05
Thanks kestrel1, I'll report it as a bug as the problem shows up even when I try to hibernate while I have no application running and memory usage is well below the 1.3GB available in swap.

---

