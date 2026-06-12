---
title: "Asus PL80J and Ubuntu experiences?"
date: 2010-11-21
forum: Hardware
---

### Post by laubblatt on 2010-11-21
Hi all,

I just bought a new notebook, the Asus PL80J and installed Ubuntu 10.10 on it.
Most things do work!
Some details:
CPU: Intel i5-430UM dual core with hyper-threading (seems to work)
GPU: NVIDIA Optimus (GeForce 310M)

**TODOs:**
Noise and energy saving:
 I would like that the notebook is quiet, when there is little workload, even when on AC. Further the battery should have 5h and more.
Therefore I installed laptop-mode-utils and powertop.
With Battery and only surfing I have just 13W usage, which is ok. I just realized that the 320GB hard drive is relatively noisy. With laptop-mode-utils the HD goes to sleep every now and then.

**Temperature and fan control:**
I installed lm-sensors, but sudo sensors-detect did not find any modules to work with. Are there any experiences to have temperature measurements and may be some more control on the fan?

Example this guy here got his ASUS UL30 down to 7 Watts and no fan sound at all:
[http://www.meisterkuehler.de/forum/notebooks-handys-mobile-hardware/28038-vorstellung-asus-ul30a-core2duo-idle-deutlich-10-watt-luefter-steht-fast-immer.html](http://www.meisterkuehler.de/forum/notebooks-handys-mobile-hardware/28038-vorstellung-asus-ul30a-core2duo-idle-deutlich-10-watt-luefter-steht-fast-immer.html)

[B]
Hybrid graphics:[/B]
There is a NVIDIA Optimus (GeForce 310M) on board. After install, the proprietary driver menu asks for installing the NVIDIA drivers, this resulted in a nightmare, with black screen after reboot with Lucid. (I still do not know how to get back to the previous settings, so I installed Meerkat, and work without the NVIDIA drivers).
Is there a way to switch off the NVIDIA card and to check if it is consuming energy or not?
[B]
High-pitched buzzing sound:[/B]
This is really annoying and happens at boot time, but also under windoof7 and under ubuntu. As far as I know it has something to do with the C4 sleep states of the CPUs. One guy recommended to start the audio recorder, it works for me, but at the same time the energy consumption goes up! ([http://forum.chip.de/notebooks/rm-clock-gegen-hochfrequentes-fiepen-988794.html#post6187940](http://forum.chip.de/notebooks/rm-clock-gegen-hochfrequentes-fiepen-988794.html#post6187940))

Well this is maybe to much, but I am interested in other solutions and experiences with this notebook!

Cheers,
maik
--

---

