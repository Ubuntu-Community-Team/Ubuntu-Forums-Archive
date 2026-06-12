---
title: "Nvidia, Power State, etc"
date: 2022-02-08
forum: Hardware
---

### Post by holysword on 2022-02-08
My Acer Nitro 5 laptop has a Nvidia RTX 2060 card and an i7-9750H.

Using "prime-select on-demand" results in 10~15sec freezes whenever I try to open a regular windows (e.g. kwrite, gedit) so it is basically unusable. Using "prime-select nvidia" causes it to overheat the whole time: I kid you not, I suspend the computer but the GPU fan rages on. Sometimes the computer stutter, since it is so hot the whole time.

The point is: there is no need. I figured out that if I unplug the power cable (even with "prime-select nvidia"), the computer automatically throttles something down, the temperature sinks and the fan becomes normal again. I plug the power again and boom, everything overheats in a few seconds again. 

I want to be able to trigger this "power saving" state, without having to unplug the power cable. But for my life, I can't figure out what is governing the frequency of my CPU/GPU. I do not have cpufrequtils installed and would prefer to not install anything extra either, unless very necessary.

Any ideas?

---

### Post by Autodave on 2022-02-08
Not sure what flavor of 'buntu you are running, but I would look in the Power Manager in Settings Manager.  You may be able to do that there.

---

### Post by holysword on 2022-02-08
Thanks for the reply. I'm using Ubuntu 20.04 but with Plasma-Workspace.

There isn't any option there relating to frequency, just screen locking/dimming and sleeping state for low battery.

---

