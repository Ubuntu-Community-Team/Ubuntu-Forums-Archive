---
title: "Recognising external display in 12.04"
date: 2015-06-09
forum: Hardware
---

### Post by iamroddo on 2015-06-09
I have a Lenovo L440 with Ubuntu 12.04 LTS work laptop. The laptop is single boot (ie no Windows and no possibility to install it). I have root/sudo access. I can install packages but upgrading the system would lose me what limited IT support I get from my company.

I want to connect it to an external screen which has a higher resolution than that of the laptop screen. When I boot up the laptop with the external screen connected the Ubuntu bootup sequence is displayed in full screen on the external display. However once Ubuntu completes to start up only a part of the external display is used, matching the number of pixels used on the laptop screen. The display is simply cloned. When I open the display settings only the laptop screen is displayed, even if I click detect displays.

---

### Post by TheFu on 2015-06-10
Try **lxrandr**.
if that doesn't work, please post the exact GPU vendor, model, and drivers used.

You don't need Windows, BTW.

---

