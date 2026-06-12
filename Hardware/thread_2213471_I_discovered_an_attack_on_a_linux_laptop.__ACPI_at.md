---
title: "I discovered an attack on a linux laptop.  ACPI attack. 0% battery and not recharging"
date: 2014-03-26
forum: Hardware
---

### Post by codenine75a on 2014-03-26
A person would remote into the laptop somehow and mess with ACPI settings to mess with your battery functions.  It also messes with operating installations by affecting a memory source in CMOS.

In the kernel (I think v3 and above), ACPI actually using a space in CMOS and this can get disrupted.  My battery would not charge at all and it would be at 0%.  

I took a peek at acpi_cmos_rtc.c under the kernel source /drivers/acpi and on line 52 on v 3.13.7 

```

CMOS_WRITE(*value, address);

```

It writes to CMOS for ACPI which I thought was odd.  My windows OS does not have that problem.  I had to wipe CMOS and reload the linux OS to recover it.:confused:

---

### Post by whatthefunk on 2014-03-26
How would they "remote into a laptop"?

---

### Post by codenine75a on 2014-03-26
> **whatthefunk said:**
> How would they "remote into a laptop"?

I think I solved the problem. 
I did the old classic partition technique.  
I make different partitions for
/proc
/sys
/root
/sys
/var
etc

No concern it was a troll bout on the public wifi brother.

I think all live linux set ups have the same problem which is installing everything on one partition.  It is a big beginner security set up because a troll can walk all over your computer data.

---

### Post by tgalati4 on 2014-03-26
I have not looked at the source code for acpi_cmos_rtc.c but I would guess that the kernel needs to write to the CMOS to save the ntp-corrected time to the real time clock (rtc) so that you will have a reasonably current time when you reboot.  This is neither odd, nor a security risk.

It's quite possible that a cosmic ray blew through your CMOS and scrambled it, causing your symptoms.  Or, more likely, your battery has developed a fault.

---

### Post by codenine75a on 2014-03-27
A quick fix ubuntu does not tell the users to secure their root because root as a default password

sudo passwd

and I am smashing the space aliens with heavy rocks.

---

### Post by cariboo on 2014-03-27
Closed due to bad information.

---

