---
title: "MicroHDMI to VGA Adapter not recognized (Lenovo Yoga 2 Pro, Ubuntu 14.10)"
date: 2015-03-17
forum: Hardware
---

### Post by stefan_03 on 2015-03-17
Hey there,

I've got a Lenovo Yoga 2 Pro notebook with Ubuntu 14.10 installed on it. I just bought a MicroHDMI to VGA adapter, I've read reviews written by Ubuntu users who say that it works fine on their notebooks (12.04 and 14.04 and 14.10). 

My notebook won't recognize it, I've installed hardinfo and nothing shown there. Not even a message in the log files when I plug in the adapter. Even though my notebook's monitor is re-rendering when plugging in the cable and the external monitor also realizes that there is a cable plugged in, nothing works. Any hints for me? It's a KanaaN adapter, and it seems like it's the only working one for Ubuntu so far, but even this won't work for me :(


Thanks!

Stefan

---

### Post by wyliecoyoteuk on 2015-03-17
I have used a couple of HDMI to VGA adapters, and they usually just work, no setup or anything, even with a Raspberry PI and Android devices.
Often the sound is out of sync on video, but no other problems.
Are you able to see the second screen in display settings?

---

### Post by stefan_03 on 2015-03-17
Hello, thanks for your reply. No, I can't see it in the display settings (or anywhere else).
Video out of think won't be a problem as I use it for presenting only.

Maybe it's a Lenovo problem, I'll try it at my colleague's notebook with Windows 8 on it. In the meantime I've ordered a new adapter. 

Any terminal commands where I can see if the notebook realizes that there is any kind of new hardware plugged in?

---

### Post by stefan_03 on 2015-03-17
SOLVED. (Well, it seems like there never had been a problem)

Seems not to be a Linux problem. I've tried it on another monitor and joggled the cable on the notebook's HDMI port as discussed in the Lenovo forums (especially 4th post) [https://forums.lenovo.com/t5/Yoga-Flex-Laptops-and/Yoga-2-Pro-won-t-display-on-External-Screen-thru-micro-HDMI/td-p/1286541](https://forums.lenovo.com/t5/Yoga-Flex-Laptops-and/Yoga-2-Pro-won-t-display-on-External-Screen-thru-micro-HDMI/td-p/1286541)

Now it works. Plugged it in, joggled the cable and within few seconds it all worked fine!

Thanks for your encouragement wyliecoyoteuk :)

---

