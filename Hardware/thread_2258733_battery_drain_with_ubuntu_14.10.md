---
title: "battery drain with ubuntu 14.10"
date: 2014-12-30
forum: Hardware
---

### Post by Rinjo on 2014-12-30
Hi All,

I am using a HP Pavilion G6 laptop with dual graphics card.
My laptop already came with Windows 7 pre-installed and I installed Ubuntu 14.10 yesterday as a dual boot.
After installation I am observing that the laptop battery is draining quite fast while running Ubuntu, in comparison to when running Windows 7.
Normally I get a battery life of around 2.5 hrs on Windows, but with Ubuntu it is less than 1 hr.
Also the laptop fan seems to be working harder with normal browsing (no video/games playing) to cool down the laptop.

Is there any know issue with ubuntu when running on a dual graphics card environment? How to rectify this issue?

regards,
Rinjo

---

### Post by ajgreeny on 2014-12-30
Depending on the dual graphic cards you are talking about here you may need to either install the appropriate proprietary driver, or if it is an optimus graphics setup, you will probably need to try to get **bumblebee** working on the system.

More hardware info please.

---

### Post by Rinjo on 2014-12-31
Hi,

Thanks for your response.

My laptop hardware specs are as below:
Laptop: HP Pavilion G6
Processor: AMD A8-4500M APU with Raedon HD Graphics (Quad Core)
Graphics: AMD Raedon HD 7640G + 7670M Dual Graphics
RAM: 4 GB
HDD: 500 GB 

If you need any more information about the system, please let me know.

regards,
Rinjo

---

### Post by ajgreeny on 2014-12-31
Other than suggesting that you install the most appropriate AMD proprietary driver for the cards you have I can not help you; I have had no AMD cards that could use AMD drivers for a very long time.

The integrated graphics in the 4500 will work only using the open source radeon driver, I think, and I am not sure if that adds problems for you or not.

---

### Post by QIII on 2014-12-31
Hello!

I'm glad you used the term "dual graphics", which is what AMD calls your setup.  This is not the same as hybrid graphics, so don't follow any instructions for hybrid graphics.

To get this to work, please look at the ATI link in my signature.  Use the command line method of installing fglrx-updates and fglrx-amdcccle-updates.  

BE SURE to run

```
sudo amdconfig --adapter=all --initial
```

BEFORE you reboot to be sure both GPUs are properly initialized.

Then you *should *(every device is different, so there are no guarantees) be able to use the Catalyst Control Center to switch between the two.  Unfortunately, the switch is not dynamic like it is in AMD's Windows driver.  Their Linux driver requires you to switch using Catalyst, then reboot.

---

