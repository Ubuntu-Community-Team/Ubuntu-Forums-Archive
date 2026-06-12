---
title: "On and off appearances of black and purple screens of death"
date: 2020-04-27
forum: Hardware
---

### Post by simplisagar on 2020-04-27
I've recently been able to do a successful install of 20.04 (\\:D/) after a previous failed attempt (dual boot with Windows 10). Now, there is this behaviour that occurs sometimes and not always. After going past the login screen, it sometimes stops at a black screen and nothing happens (the processor seems to run in full swing) and sometimes there is the purple screen that stays forever and other times, the desktop loads just fine. I understand that this is to do with the display server or the lack of installation of proprietary display driver. Ubuntu on Wayland does load the desktop but it cannot be used as it appears to be struck (processor in full swing again).


    At times when the desktop does load successfully (xOrg), the 'Additional drivers' application says that there are no proprietary drivers installed but also does not make any recommendations. How am I to approach this problem? Experts, please suggest. The laptop configuration is as follows:


Make: HP Pavilion
Processor: Core i5 6200U @2.30 Ghz
RAM: 8 GB


(These specs are taken from Windows's dxdiag)
GPU: Intel HD Graphics 520
Total mem: 4143 MB
Display memory (VRAM): 128 MB
Shared memory: 4015 MB

---

### Post by CelticWarrior on 2020-04-27
```
GPU: Intel HD Graphics 520
```

No proprietary drivers for this one, the default Intel open-source drivers *should* be installed and working.

There is a discrepancy here that could be indicative of some other problems.
You say
> RAM: 8 GB
but then
> Total mem: 4143 MB
which is half. 

Could it be that one of the RAM modules failed and that is the cause?

---

### Post by simplisagar on 2020-04-29
Unlikely that one of the RAM modules have failed. The total memory 4143 MB probably is the total graphics memory. Out of the total 8 GB RAM, 4015 MB is shared for graphics while 128 MB might be dedicated. But now that you mentioned that the default drivers for Intel graphics 520 should suffice and that there are no other proprietary drivers for it, maybe the xOrg needs to be reinstalled. The fact that the desktop does load when on Wayland is compelling me to think that xOrg might have gone corrupt for some reason. Is it possible to reinstall/fix the xOrg?

---

