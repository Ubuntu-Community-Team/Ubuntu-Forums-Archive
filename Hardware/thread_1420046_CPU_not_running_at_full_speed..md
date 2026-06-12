---
title: "CPU not running at full speed."
date: 2010-03-02
forum: Hardware
---

### Post by perrti-y02 on 2010-03-02
Hello,
I am running Ubuntu 9.10 64bit on a Shuttle SG31G2 with an Intel Core2Duo which is supposed to be running at 2.66ghz. As it stands it is running at 1.600 Ghz according to both Linux and Windows 7. I have checked the BIOS which is claiming that the clock speed is 333MHz and the multiplier is 8 (which by my calculations is 2.664GHz) but when I run sudo lshw on the linux installation it claims a clock speed of 200.

Does anyone have any idea what is going on or how to solve this?

I am fairly sure that it is actually running at 1.6GHz because the entire system seems quite sluggish compared to what it used to be like, even though I have just done a fresh install.

Many Thanks

Tim.

---

### Post by wojox on 2010-03-02
Have you tried right clicking the top panel and adding CPU Frequency Scaling Monitior and adjusting it? Sounds like it's set to Power Saving or something.

---

### Post by wojox on 2010-03-02
Another thing, if it's a fresh install did you activate any video drivers. That will make feel sluggish, if you didn't.

---

