---
title: "Toshiba 1805-S204 Won't Finish Booting"
date: 2009-06-03
forum: Hardware
---

### Post by wmichaelb on 2009-06-03
Hi, I'm not new to Ubuntu, but I found a problem trying to install it on an older Toshiba Satellite 1805-S204.

I used Wubi to put Xubuntu 9.04 on it, but when I try to boot into that install, the machine grinds away for about three minutes, beeps loudly three times at me, and then shuts down. I tried verbose mode, and found an ACPI message that stated that it was repeatedly shutting down due to high temperatures (68-74 degrees). The fan in the unit is working, and I can hear it speed up as the processor works harder. I would say this is a hardware problem, but the unit runs XP just fine, never shuts down. I also have found a number of ACPI issues on the net with this laptop. Does anyone have any other suggestions?

Thanks in advance.

---

### Post by wmichaelb on 2009-07-02
I stumbled onto the noapic option on bootup; that allowed me to successfully install. Wireless didn't work for three days, and then all of a sudden kicked in. Now, all I have to do is fix the display resolution.

---

