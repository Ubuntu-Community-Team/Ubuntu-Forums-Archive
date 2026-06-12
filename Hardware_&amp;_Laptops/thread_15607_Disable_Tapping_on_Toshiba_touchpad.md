---
title: "Disable Tapping on Toshiba touchpad"
date: 2005-02-15
forum: Hardware &amp; Laptops
---

### Post by Stormraven on 2005-02-15
Hello all,

I'm running Warty on my Toshiba M35X-S149 and would like to know if anyone knows how to disable touchpad tapping?  
It's not a deal-breaker or anything, but it would be nice.

The touchpad isn't Synaptics, but it does respond to those drivers.

Thanks!

Stormraven

---

### Post by mendicant on 2005-02-16
If you're using the synaptics driver for X, you can just change the synaptics InputDevice section to have:

Option "MaxTapTime" "0"

---

