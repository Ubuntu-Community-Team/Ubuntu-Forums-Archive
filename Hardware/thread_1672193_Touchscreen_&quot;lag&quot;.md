---
title: "Touchscreen &quot;lag&quot;"
date: 2011-01-20
forum: Hardware
---

### Post by oddish2211 on 2011-01-20
i've installed Ubuntu 10.10 on my HTC Shift, a very small UMPC with a touchscreen made by HTC.
the touchscreen works, but it kind of lags. if i move my cursor by moving my finger over the screen the cursor follows my movement but it lags. it's like the refreshrate is to slow.

a few years ago, someone wrote a driver for this touchscreen called htcpen. [here]("http://pof.eslack.org/2008/05/11/htcpen-htc-shift-touchscreen-driver-for-linux/") this driver was integrated into the kernel. i don't know much about linux drivers, i used to fiddle with xorg.conf, but since it's gone i don't know where to go.

so, my touchscreen lags, i believe the htcpen driver isn't used, but evdev instead. when i use the evtest tool to check for input, i can see it only gets input every +-0.5 second. that's why the cursor lags. anyone with a bit of driver knowledge who can help me out?

---

