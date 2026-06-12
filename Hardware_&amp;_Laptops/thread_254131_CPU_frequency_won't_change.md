---
title: "CPU frequency won't change"
date: 2006-09-09
forum: Hardware &amp; Laptops
---

### Post by Henry Rayker on 2006-09-09
I'm running the amd64-k8 version of Ubuntu on my laptop (AMD Turion64 ML-30 1.6GHz) Okay, last night, my cpu frequency would change when I would run extra programs and all. I could also set the frequency with the GNOME applet. This morning, however, I boot up and I can no longer adjust the frequency. I'm stuck at 800MHz which is just plain silly.

Is there anything you guys can suggest? All I did to get it to work in the first place was  sudo dpkg-reconfigure gnome-applets. I have the control when I left click the applet, but it doesn't do anything. I have it set to allow me to change in the applet's option.

I remember reading somewhere that different tools work with varying degrees of efficiency, but I can't seem to find that page any longer.

Thanks.

PS this is my cpufreq-inf
cpufreq-info
cpufrequtils 0.4: cpufreq-info (C) Dominik Brodowski 2004
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.

I went into synaptic and searched for cpu and uninstalled completely anything that had anything to do with cpu frequency. I restarted and was told my cpu didn't support scaling and it would be clocked at 798MHz. I re-opened synaptic and installed powersaved which fixed my issue. Now I've got working CPU scaling via the gnome app.

I hope this helps someone.

---

### Post by Henry Rayker on 2006-09-14
Well, I'm using the 32b version of Dapper now, because of some driver issues in the 64b version. My frequency scaling works now, if my AC plug is in the laptop, but if it is not, I can't scale my frequency...any ideas?

---

