---
title: "heat issues?"
date: 2016-04-24
forum: Hardware
---

### Post by ckam032 on 2016-04-24
I'm a newb so bare with me but I'm running Ubuntu Mate 16.04 on an XPS 15 9550 and I seem to be having issues with heat.  Definitely runs a lot warmer than when I had windows.  Added the sensors applet at the top that shows the CPU temperatures of the cores.  Stays between 25-40 C and I'm runnning on the Intel graphics.  Installed TLP and the battery life seems great.  It running warmer seems to be the only issue. Is this normal?  Also the screen brightness is set to 50%  and the power seems to average between 10-16W.

---

### Post by virgosun on 2016-04-25
> **ckam032 said:**
> I'm a newb so bare with me but I'm running Ubuntu Mate 16.04 on an XPS 15 9550 and I seem to be having issues with heat.  Definitely runs a lot warmer than when I had windows.  Added the sensors applet at the top that shows the CPU temperatures of the cores.  Stays between 25-40 C and I'm runnning on the Intel graphics.  Installed TLP and the battery life seems great.  It running warmer seems to be the only issue. Is this normal?  Also the screen brightness is set to 50%  and the power seems to average between 10-16W.

I found 16.04 kernel 4.4 default intel_pstate drive place all my cores at max frequency even though default governor is powersave. So I disable intel_pstate = disable in kernel and set the default governor  to  conservative. I set PRIME profile to Intel and also disable Nvidia card in Bios. This way my laptop run cooler.

---

