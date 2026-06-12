---
title: "Hibernate not hibernating"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by trubblemaker on 2006-09-22
The issue: Hibernate is the same as turning off my computer.

I'm running a Gateway, 512 ram
 CPU: Intel(R) Celeron(R) M processor         1.40GHz stepping 08

the /etc/default/acpi-support I'm using is [from this post]("http://ubuntuforums.org/showpost.php?p=1178889&postcount=12")

<just before hibernate>
I think it flashes that something fails but then the screen is turned off. Don't know where to look for a log.
<after hibernate>
hibernate is still the same as turning off my computer.  (by turning off I mean that it is equivalent to turning it off.)  If I don't have my splash screen up I can see it clearing signature 2.  When I turn the computer back on, (after a hibenate) it really is like a normal turning-back-on and not the awesome back to where I was, like hibernate is supposed to. How can I make it hibernate for real?

I was able to hibernate before upgrading to dapper so it is possible. And I just need to find the right settings

---

### Post by frogotronic on 2006-12-10
> **trubblemaker said:**
> The issue: Hibernate is the same as turning off my computer.

I'm running a Gateway, 512 ram
 CPU: Intel(R) Celeron(R) M processor         1.40GHz stepping 08

the /etc/default/acpi-support I'm using is [from this post]("http://ubuntuforums.org/showpost.php?p=1178889&postcount=12")

<just before hibernate>
I think it flashes that something fails but then the screen is turned off. Don't know where to look for a log.
<after hibernate>
hibernate is still the same as turning off my computer.  (by turning off I mean that it is equivalent to turning it off.)  If I don't have my splash screen up I can see it clearing signature 2.  When I turn the computer back on, (after a hibenate) it really is like a normal turning-back-on and not the awesome back to where I was, like hibernate is supposed to. How can I make it hibernate for real?

I was able to hibernate before upgrading to dapper so it is possible. And I just need to find the right settings

log should be in /var/log/hibernate.log

---

