---
title: "External monitor on laptop with display issues"
date: 2010-11-17
forum: Hardware
---

### Post by tsaid on 2010-11-17
Hi,

I'm having a specific problem on Ubuntu with an external monitor.

The inverter in my qosmio x505 q890 laptop monitor died (already ordered a new inverter, it should come 25/11). It's really dim, I can't see anything. So I plugged in an external monitor and installed Ubuntu using nomodeset (since it comes with nvidia).

On the first boot everything was working fine (using nomodeset). I installed the restricted drivers and restarted the laptop. The boot image and sound were played, but everything shows on the laptop monitor and I can't switch to the external monitor. It only switches when I'm in text mode.

Looking around I found out that I must change the nvidia-settings in order to use the external monitor. So I tried booting into recovery mode using safe graphics. It worked, everything showed on the external monitor. But, obviously, I can't change settings in the nvidia-settings.

So right now I'm a little stuck. What can I do next? Is there a way to change settings using nvidia-settings in text-mode?

Please help.

Thanks in advance,
Tarek.

---

### Post by tsaid on 2010-11-26
> **tsaid said:**
> Hi,

I'm having a specific problem on Ubuntu with an external monitor.

The inverter in my qosmio x505 q890 laptop monitor died (already ordered a new inverter, it should come 25/11). It's really dim, I can't see anything. So I plugged in an external monitor and installed Ubuntu using nomodeset (since it comes with nvidia).

On the first boot everything was working fine (using nomodeset). I installed the restricted drivers and restarted the laptop. The boot image and sound were played, but everything shows on the laptop monitor and I can't switch to the external monitor. It only switches when I'm in text mode.

Looking around I found out that I must change the nvidia-settings in order to use the external monitor. So I tried booting into recovery mode using safe graphics. It worked, everything showed on the external monitor. But, obviously, I can't change settings in the nvidia-settings.

So right now I'm a little stuck. What can I do next? Is there a way to change settings using nvidia-settings in text-mode?

Please help.

Thanks in advance,
Tarek.
bump

---

### Post by Fafler on 2010-11-26
I don't know if this is going to work, but install the SSH server and enable X forwarding. Log in from another machine and run the nvidia control panel over SSH.

Or just write a /etc/X11/xorg.conf

---

### Post by tsaid on 2010-11-26
good idea! I'm going to try that later today and I'll post the results!

---

