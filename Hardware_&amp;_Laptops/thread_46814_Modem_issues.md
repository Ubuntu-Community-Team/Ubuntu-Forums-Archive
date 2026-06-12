---
title: "Modem issues"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by Hollowfrank on 2005-07-06
Is there any support under Hoary for Dynamode dial up modems, if not could someone point me in the direction of a cheap and cheerful compatible modem.

---

### Post by intangible on 2005-07-06
Perhaps, do you have a model number for the modem?

Your safest bet otherwise would be to grab an external modem that plugs in a serial port.  Those are almost guaranteed to be hardware based instead of software based.

---

### Post by Hollowfrank on 2005-07-06
M56PCI/S-FAST

i believe that to be the model number, after much interest over the last few months i'm just getting to using ubuntu, hence the hardware issue. Anyhoo, any help is much appreciated.

---

### Post by intangible on 2005-07-06
Looks like it will use the slmodem drivers, Try here: [https://wiki.ubuntu.com/forum/hardware/smartlink](https://wiki.ubuntu.com/forum/hardware/smartlink)

If you want it to run on something other than the default i386 kernel, you'll have to build the drivers yourself (do a search in synaptic for sl-modem).  But just using the default should be fine.

---

### Post by Hollowfrank on 2005-07-10
Right, I now have got hold of a modem with an Intel 82536/5628c, after having been told that these should work. The driver cd came with linux drivers for both sets, these drivers it seems are incompatible,  i don't have the expertise or knowledge to deal with this.

[http://www.safecom.cn/code/sub/category.asp?prdid=32&subcatid=8](http://www.safecom.cn/code/sub/category.asp?prdid=32&subcatid=8) - thats the intel chipset modem i have jut purchased.

so far with both modems there has been a complete lack of activation or detection.

---

