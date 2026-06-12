---
title: "Disable &quot;Some&quot; USB Ports in Ubuntu"
date: 2013-12-29
forum: Hardware
---

### Post by Rushyang on 2013-12-29
Hello Guys,

I need to disable USB ports in "just front panel" in Ubuntu. Not ALL! because 2 ports in back of CPU will be occupied by Keyboard and Mouse. By disabling all USB ports will stop their functioning.. 

This is requirement in my company and I am a bit confused how to do it.

Let me know if this is possible and please help me out asap.

---

### Post by plucky on 2013-12-29
> **Rushyang said:**
> Hello Guys,

I need to disable USB ports in "just front panel" in Ubuntu. Not ALL! because 2 ports in back of CPU will be occupied by Keyboard and Mouse. By disabling all USB ports will stop their functioning.. 

This is requirement in my company and I am a bit confused how to do it.

Let me know if this is possible and please help me out asap.

Pull out the cable that goes to the front ports.

---

### Post by Rushyang on 2014-01-05
Well, That's not the solution that I'm looking for!
NO H/W interaction guys!

Anyone else?

---

### Post by ian-weisser on 2014-01-05
You can make a udev rule.

That may be tricky, because you have (if I recall correctly) no assurance that the USB ports will have the same label after each reboot. So you will need to test for the keyboard and mouse, and disable the rest.

For example udev rules, see etc/udev.rules.d/ and /lib/udev/rules.d/ . Don't erase anything in /lib, a similarly-named rule in /etc will override the /lib rule.

---

