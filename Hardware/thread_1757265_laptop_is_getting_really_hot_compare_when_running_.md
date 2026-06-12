---
title: "laptop is getting really hot compare when running winXP"
date: 2011-05-13
forum: Hardware
---

### Post by storm3d on 2011-05-13
Hello
 
I installed Xubuntu on my old Thinkpad T43 laptop. Compare to Windows XP, the laptop is getting really hot even its not doing anything. (There is no problem with dust or blocked vents) 

When I run windows XP the temperature is about 50C (during heavy usage) but Xubuntu makes 73C AND MORE for no reason. No application runs whatsoever. (latest Ubuntu - same problem)

Or maybe I am wrong and the latest Xubuntu is just not for laptop like this?

Any help appreciated

---

### Post by quixote on 2011-05-14
Not sure it applies to your specific model, but there's been a [bug reported]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/751689?comments=all") for some Thinkpads that makes them run hot. A workaround is to ask for a different power profile in the BIOS (by hitting the setup key for your laptop before it boots up).  You want the "balanced" setting rather than the default one which is optimized for top speed at all times.  It's described more fully in the comments in the bug report.

---

