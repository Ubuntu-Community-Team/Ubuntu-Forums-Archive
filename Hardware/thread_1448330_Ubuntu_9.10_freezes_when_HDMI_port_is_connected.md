---
title: "Ubuntu 9.10 freezes when HDMI port is connected"
date: 2010-04-06
forum: Hardware
---

### Post by felipehummel on 2010-04-06
Hi, I have a Sony Vaio FW350 with a HDMI output. I'm trying to use it under Ubuntu 9.10 with a LG LCD monitor 21,5'. I've tried two approaches:
  
[LIST=1]
[*]Boot the laptop with the HDMI cable connected and monitor turned on. Result: LCD Monitor keeps turned on but the whole screen is black and Ubuntu do not seem to be initializing.
[*]Boot Ubuntu until the end. I then connect the HDMI cable into the Laptop. The mouse and the whole system freezes.
[/LIST]
  In both cases the only way to turn off the laptop is holding the power button.
  I've looked around the internet for similar problems, but only found workarounds for the same problem with VGA input, not HDMI.  I also tried to use metacity before connecting the cable, but still got the same result.
  Any hints?

---

### Post by alek01 on 2010-05-02
Hi Felipe.
I have the exact same issue but only after a fresh install of 10.04. I was initially running 9.04 and upgraded via synaptics to 10.04 and both my VAIO laptop and the external HDMI screens worked. Then I decided to make a complete fresh install using a 10.04 CD. And now pluging the HDMI cable freezes the system to death.
I'm searching further.

---

### Post by dag425 on 2010-10-11
I have the same issue with my FW351j VAIO. I have already updated both the kernel to 2.6.35-22-generic-pae and the drivers to my Intel 4500M HD onboard video card and my laptop continues to freeze as soon as I connect the HDMI cable to my TV and I am unable to find anymore workarounds, solutions, or fixes... Any and all help will be very much appreciated.

---

### Post by tuxonapogostick on 2012-02-19
Seems like this problem still persists regardless of the kernel and ubuntu updates. My computer is sony laptop vgn fw235d. According to lspci it has intel mobile 4 series chipset integrated graphics controller using the kernel driver i915. Ubuntu version: Oneric, kernel version 3.0.0.16.

---

