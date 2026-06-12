---
title: "Thinkpad R50 and battery"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by anandi on 2006-11-03
I have recently removed xp completely on my R50 and replaced with Dapper. Earlier it was a dual boot between Dapper and XP.

Now i noticed that my R50 battery doesn't last for more than 30 mins, whereas while running under xp it used to give me 1.5hrs of battery time. I checked on the battery charge as well, even Dapper says the battery is 100% charged, however it just doesn't last that long anymore.

I am sure this is to do with the power management, i tried to disable acpi by specifying the kernel parameter and enabling apm, however the condition renamed the same. Switching to APM, also introduced a problem, when the lid of the laptop is closed, it goes in sleep mode even when i have configured the sleep button option from the power management to do nothing when the lid is closed. This forced me to switch back to acpi.

Now can someone please direct me on how to get back the battery time on the thinkpad.

---

### Post by pentium0 on 2006-11-29
It is likely that you need to get CPU scaling working.  This might involve loading the kernal mod speedstep-centrino with the command

sudo modprobe speedstep-centrino

But there are many threads dedicated to getting CPU scaling working for various CPUs.

---

