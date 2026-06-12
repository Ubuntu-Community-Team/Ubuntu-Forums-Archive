---
title: "CPU frequency scaling not working..."
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by examancer on 2006-07-04
I'm running Ubuntu 6.06 on an Acer Aspire 3623WXMi. It has a Celeron-M 1.5GHz cpu. I know that the CPU supports scaling cause I dual boot to windows and can scale it down manually and see obvious battery life differences. However, the CPU frequency scaling applet in Dapper says my system may not be configured correctly or that its not supported. Well, I know the second one isn't true, so I'll assume its misconfigured. Any ideas how I might go about fixing this? Would be a real battery saver...

---

### Post by zgoda on 2006-07-04
You have to manually select scaling governor and add it to /etc/modules for this type of processor (it uses p4_clockmod). I have laptop with C-M 360J and frequency scaling works from 175MHz to 1.4GHz, but I don't observe substantial changes in power constumption.

---

