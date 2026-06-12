---
title: "[SOLVED] Dell D630 NV135 Docking station freeze"
date: 2008-08-13
forum: Hardware
---

### Post by sagyvolkov on 2008-08-13
Hi,

Using hard 8.04.1 on Dell D630 with Nvidia NV135.
Compiz is enabled.
I've recently started using a docking station, which works fine, including disconnecting/connecting.
I then connected an external LCD to the docking station, the LCD was disabled by default (look at nvidia-settings). still undocking/docking worked fine.
Once I enabled the external LCD (nvidia-settings), using the "Separate X Screen" and restart X all was working, but undocking and docking, makes my laptop freeze (once I dock back in). 
I could not find anything regarding the freeze and power cycle bring the machine backup normal.

Basically, all I want is an option to dock/undock and use only one screen at the time (moving the content from one external LCD to laptop LCD once i dock/undock). I could do this on my T60 with aticonfig, but can't find the write option on nvidia.

Also, could someone explain the difference between the nvidia-glx and the nvidia-glx-new drivers? both have the same description in synaptec.

Thanks.

---

### Post by sagyvolkov on 2008-08-13
Update:
The same phenomena happens with nvidia-settings configuration set as TwinView.
Also, the problem persist with compiz disabled (System->Preferences->Appearance->Visual Effects->None).

I can not find any error messages in /var/log/messages, syslog, kren.log, debug or Xorg.x.log. Its like the system freeze in such a way it crashes without writing anything to logs.
I have two laptops like these, both the same configuration (Different External LCDs) and both have the same issues, so I'm ruling out any hardware issues.

Any help would be appreciated.

---

### Post by sagyvolkov on 2008-08-13
Update:
Installed Envy, and let it install the latest nvidia drivers, nvidia-settings now show 173.14.12.
Crash still occur.

---

### Post by sagyvolkov on 2008-08-13
Uninstalled any nvidia package.
rebuild xorg.
problem still persist.
Further more, problem happens when i undock/dock even with the external monitor **not** connected to the docking station.

Again, any thoughts would be appreciated.

---

### Post by sagyvolkov on 2008-08-15
Well, this looks like a bug in the kernel fixed only in 25
I found a workaround, you suspend the laptop prior to docking it, then open the lid/press the power (whatever brings it back on from suspend) and it works fine.

---

