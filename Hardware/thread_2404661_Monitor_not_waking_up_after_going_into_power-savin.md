---
title: "Monitor not waking up after going into power-saving mode"
date: 2018-10-26
forum: Hardware
---

### Post by accessd on 2018-10-26
As of a few days ago, once my monitor turns itself off after a specified amount of time, it no longer wakes up by moving the mouse or pressing buttons on the keyboard. The only way to wake it back up is by physically turning it off and back on again. Given that it was working fine until this week, I assume that it was an update that introduced the problem. 

I'm running Ubuntu 18.04 using an X.org session. I have a Radeon RX 560 Series graphics card and am using the amdgpu-pro drivers. I tried upgrading the drivers to the latest version, but that did not solve the problem. I experienced the same issue when I was using the iGPU on my Intel® Core™ i7-4790K CPU, but have not seen it since I installed a discrete graphics card. Does anyone have any idea what's going on or how I can troubleshoot this issue?

---

### Post by Autodave on 2018-10-27
Have you determined that it is not the monitor's fault?  Could be.  If it is connected by a VGA cable, try another cable: they are known to fail, especially the cheaper ones.

---

### Post by accessd on 2018-10-27
It's connected via HDMI. Everything else works fine, but I'll try another cable and see what happens ...

---

### Post by him610 on 2018-10-27
> my monitor turns itself off after a specified amount of time
Have you tried to set your monitor to _never_ turn off in the Power Settings?

---

### Post by Autodave on 2018-10-28
There are several different versions of HDMI cables.  Earlier ones didn't have the audio capability, for instance. Try another cable and report back.

---

### Post by accessd on 2018-10-28
> **Autodave said:**
> There are several different versions of HDMI cables.  Earlier ones didn't have the audio capability, for instance. Try another cable and report back.

I tried a brand new HDMI cable and I'm still experiencing the same issue. I also tried using xscreensaver instead of gnome-screensaver, but it produced the same result.

---

### Post by accessd on 2018-10-28
> **him610 said:**
> Have you tried to set your monitor to _never_ turn off in the Power Settings?

Yes, I can set the monitor to never turn off and do it manually. However, I would prefer if the monitor would turn itself off when the computer is inactive and back on when I press a key, as it's supposed to.

---

### Post by accessd on 2018-10-29
Anyone have any other ideas?

---

### Post by him610 on 2018-10-30
> running Ubuntu 18.04 
Have you considered using another ?buntu release? My spouse uses Ubuntu while I use Xubuntu. I am constantly frustrated using Ubuntu because the lack of granularity to control settings whereas in Xubuntu it seems you can change settings that are not available in stock Ubuntu. There is a caveat though with Ubuntu,  you can probably change those settings in a configuration file if you have the knowhow as to which one to modify.

On another thought, I had a small problem with my monitor displaying on one of my systems using a HDMI cable. I replaced it with a DVI-D cable - problem solved.

> using the amdgpu-pro drivers
Have you considered dropping back to the amdgpu driver? I have a lesser AMD GPU that uses the radeon driver. I just finished testing the timed power-off then power-on by an up-arrow keypress - works as expected.

Keep at it; you will solve it eventually. Tenacity + Perseverance + Improvement = Success.

---

### Post by accessd on 2018-11-12
Thank you all for your help. It turns out to be an issue with the update to the 4.15.0-38 kernel. Once I booted using the Linux 4.15.0-36-generic kernel, the monitor started behaving as expected.

---

