---
title: "Laptop runs very hot"
date: 2013-10-03
forum: Hardware
---

### Post by manoriax on 2013-10-03
Hello everybody,

I am wondering why my laptop does run so hot. It's now at about 77 °C even though I only watch a video on Netflix and have a browsser window open. When the laptop is idle, it's at about 65 °C, which is, ion my opinion, still rather hot. Here are some specs:

I am using a HP Pavilion g6-1336eg, AMD A6-3420M APU with Radeon HD 6520G + 7450M Dual Graphics.

While using the open source driver, my idle temperature was at about 80 °C, so I installed the fglrx driver from the Ubuntu repos. Temperature was about the same as it is now, but the driver didn't recognize both graphics adaptors, which was a problem, as I need them both. So I went along and installed the flgrx stable driver from the AMD website, which recognized both adapters but then the laptop was very hot again. Now I am using the latest fglrx beta driver, which recognizes both adapters and lets the laptop run cooler than before. But still, I find that >60 °C on idle is a bit much, isn't it?

So, does anybody know whether there is a way to improve anything so that the temperatures go down? I am already using Jupiter and the hardware itself is clean (physically).

Thanks!

-Phil

---

### Post by subhendu2 on 2013-10-03
> **manoriax said:**
> Hello everybody,

I am wondering why my laptop does run so hot. It's now at about 77 °C even though I only watch a video on Netflix and have a browsser window open. When the laptop is idle, it's at about 65 °C, which is, ion my opinion, still rather hot. Here are some specs:

I am using a HP Pavilion g6-1336eg, AMD A6-3420M APU with Radeon HD 6520G + 7450M Dual Graphics.



This has nothing to do with Ubuntu. 
AMD processors are known to get more hot than their Intel counterparts. In fact the Radeon graphics card also emits large amount of heat and when you are watching videos the graphics card works.

If you feel it is too hot u can use cool pads. but i feel nothing to worry about

---

### Post by manoriax on 2013-10-03
Sounds reassuring, thank you.

---

