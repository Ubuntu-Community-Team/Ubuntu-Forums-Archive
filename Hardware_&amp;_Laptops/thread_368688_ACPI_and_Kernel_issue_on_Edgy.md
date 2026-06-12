---
title: "ACPI and Kernel issue on Edgy"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by geco on 2007-02-23
Hello, recently I upgraded from Dapper to Edgy without problems (actually I had hard work to configure ati drivers ;)) but ACPI stopped to work properly and I had just thermal monitoring.

I tried to reconfigure ACPI recompiling the DSDT file and debugging it... it was all ok but ACPI still didn't work :(

As last resort I downgraded my kernel from  2.6.17-11-386 (the last official Edgy kernel) to 2.6.15-28-386 (the last official Dapper kernel) and ACPI worked again.

So I think there's something wrong in Edgy linux-image or even in 2.6.17 kernel.

Anyway I will not use 2.6.17 kernel until ACPI will work because I need it on my laptotp.

If you just like to know I have an Acer Travelmate 3202XMi (Intel Pentium M 725, 1GB RAM, ATI Mobility Radeon 9700/64MB)

I will be pleased if you leave any comments.

Thank you.

---

### Post by geco on 2007-02-28
up.... still no comments :(

---

### Post by wersdaluv on 2007-03-01
I think I have the same problem.

Please see [this thread]("http://ubuntuforums.org/showthread.php?t=356269").

Do we have the same problem?

---

### Post by geco on 2007-03-02
> **wersdaluv said:**
> I think I have the same problem.

Please see [this thread]("http://ubuntuforums.org/showthread.php?t=356269").

Do we have the same problem?

Actually I have no problems with usb... it's just acpi that gave me problems.

Maybe I should try again with the Edgy kernel... but now I have no time.

Thank you,
geco

---

### Post by geco on 2007-03-04
I tried to run edgy eft from the live cd and... ACPI worked! So what's wrong with my installation?

Why the **same** kernel works with the live cd and _does not_ with the standard installation? What did I miss during the dist-upgrade???

---

### Post by geco on 2007-03-05
up #-o

---

