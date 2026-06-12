---
title: "Suspend breaks display, any pointers?"
date: 2007-03-07
forum: Hardware &amp; Laptops
---

### Post by ZeroXR on 2007-03-07
On my project Toshiba laptop, I have run into an odd bug where when I suspend the laptop with the Suspend command... The laptop goes into the suspend mode with the clear ring around the power button doing a fade/glow in orange and same for the battery LED on the front of the laptop. But on waking it up from the suspend with either a power button or key press, The machine powers up everything except the display.

The odd thing is... when I close the lid and re-open it, everything functions properly after I type my password.

I have read a lot of Googled posts about the problem and many say that typically the newest firmware resolves the problem... I have the newest firmware and it's still a problem. Can anyone help me out here?

---

### Post by vespo on 2007-03-23
Hi

istall vbetools and add the following line to your xorg.conf, section "device"

```
Option "VBERestore" "true"
```

---

