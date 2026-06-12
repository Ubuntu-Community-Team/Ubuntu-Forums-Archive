---
title: "Gateway laptop overheating since 10.10"
date: 2010-11-28
forum: Hardware
---

### Post by daltore on 2010-11-28
I've been running Ubuntu on this laptop (Gateway NV5207u) since 9.10, and as soon as I updated to 10.10 I started having rather consistent overheating problems where the computer will freeze, and the screen will blank after a few seconds until I force a reboot.  I have already cleaned out the fan (Gateway's still got it, I had to disassemble the ENTIRE computer to get to it), and I've looked for some comprehensive fan control setting, but I've yet to find one that looks like it's supposed to be running.  I haven't changed the BIOS, and I've turned a lot of the ATI Radeon graphics settings down further than they were on previous installations.  Any ideas?

---

### Post by garvinrick4 on 2010-11-28
#Is something running like all get out and using your cpu up to 100%
#Use system monitor to check.
# What happens when you run off of live cd?
 Just throwing some stuff out there to check. Good luck with you machine.

---

### Post by daltore on 2011-05-08
I know this is way late, but I have since gained a lot of information on the Maverick instability issues.

It turns out that my laptop was not overheating, although the symptoms would be very similar.  There was some issue between Ubuntu 10.10 and the ATI Radeon graphics driver which caused HUGE instability problems, where the computer would crash randomly.  I never did figure out what exactly that issue was, and I never found a fix.  However, as promised, the issue was fixed in 11.04.  I haven't had a problem since I updated last week.

---

