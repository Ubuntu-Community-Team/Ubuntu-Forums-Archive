---
title: "NVIDIA Driver 460.80 freezes Linux system when plug monitor though DisplayPort"
date: 2021-07-16
forum: Hardware
---

### Post by potatolige on 2021-07-16
Hi,

I am not sure if this is the correct place to post my problem. 

I have got a problem for my dual monitor setup using Displayport with NVIDIA GPU, after I updated my nvidia driver or maybe some Linux stuff few weeks ago.
I cannot enter the system when I plug my second monitor using the Displayport cable. And when the pc is on, then pluing Displayport cable will lead a dead to the system.

Setup:


Driver version: 460.80
GPU: 2060 Super
OS: Ubuntu 20.04
Linux core: 5.4.0-77-generic
monitors resolution: two iiyama 2560 * 1440 monitor (HDMI + Display port)



I posted another issue in NVIDIA's forum but unfortunately got no answer yet. 
[https://forums.developer.nvidia.com/t/driver-460-80-freezes-linux-system-when-plug-monitor-though-displayport/182871](https://forums.developer.nvidia.com/t/driver-460-80-freezes-linux-system-when-plug-monitor-though-displayport/182871)

I appreciate any help from the community.

Best,
Ge Li

---

### Post by linuux on 2021-07-16
I read on here and I think on that forum that there is a Nvidia driver bug - with hdmi to displayport connections....especially with using driver version 460.

So, try a newer driver - 465 or 470 beta and see if the experience is any different.

Other things to try if possible:
* hdmi to hdmi connection
* Ubuntu 21.04 live iso - with driver 460, 465 or 470 (easy way to try a newer kernel to see if there's any difference)

Advanced commands and steps to try - search the forum for the recent 'issues' with nvidia  - some may apply to your case, some might not
- search the nvidia developer forum - there were some recent posts about this - but, I think many involved laptops - nvidia hybrid graphics - may not apply to desktop cards, I dunno. 

Good luck.

---

### Post by Autodave on 2021-07-16
Where did you get the driver from?

---

