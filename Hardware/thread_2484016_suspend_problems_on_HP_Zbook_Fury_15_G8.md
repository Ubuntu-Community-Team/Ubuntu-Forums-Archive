---
title: "suspend problems on HP Zbook Fury 15 G8"
date: 2023-02-15
forum: Hardware
---

### Post by mlancelle on 2023-02-15
Hello,

I have an HP Zbook Fury 15 G8 with Ubuntu 20.04.5 LTS (I don’t want to upgrade to 22.04 if possible).

symptoms:
[LIST]
[*]with s2idle, when trying to supend, the screen turns black, but the fan keeps spinning and the laptop stays hot, using a lot of battery. 
[*]with deep (/sys/power/mem_sleep now contains s2idle [deep]), which I guess is what I want, suspending works properly but waking up does not. The keyboard LEDs and fan react when I try to wake up, but the screen doesn't show anything. I need to long press the power button to shut down and restart. 
[*]journalctl shows 'systemd-sleep[7107]: Suspending system...' when  suspending, does not show anything at the time trying to wake up 
[/LIST]

things I tried without success:
[LIST]
[*]I switched to the certified kernel (5.14.0-1024-oem as specified in [https://ubuntu.com/certified/202105-29010](https://ubuntu.com/certified/202105-29010), I was on a generic kernel before) 
[*]I switched to the NVidia driver (NVIDIA driver metapackage from nvidia-driver-525 (proprietary), I was on Nouveau before, I also tried the NVidia 510 version) 
[*]I updated the firmware with fwupdmgr update 
[*]I tried without display manager (sudo service gdm stop) 
[/LIST]

What could I try next?

Disclaimer: I haven't used Linux for a decade and I don't really know what I'm doing.

---

### Post by mlancelle on 2023-02-16
if this is the wrong forum, please kindly refer me to a better place, thank you!

---

### Post by max-waw on 2023-03-19
I have very similar issues, namely fans spinning after trying to put laptop to sleep.
It also happens on Zbook Fury.

The only difference is that I'm using Ubuntu 22.04.

Did you find any solutions to the problem?

regards

---

### Post by mabdelaal86 on 2023-05-17
I have the same problem with ZBook Fury and Ubuntu 22.04.
Hope someone find a solution for it.

---

