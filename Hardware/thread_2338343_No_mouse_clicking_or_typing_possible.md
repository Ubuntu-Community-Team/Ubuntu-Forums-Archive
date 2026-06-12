---
title: "No mouse clicking or typing possible"
date: 2016-09-27
forum: Hardware
---

### Post by Sparky34 on 2016-09-27
Hi forum members,

A week ago I upgraded my computer with a new motherboard with Skylake CPU and Samsung SSD. After the upgrade I installed Elementary OS 0.4 Loki (based on Ubuntu 16.04). 

The problems started with "flickering" of the screen, mostly by scrolling black squares came all over the screen and it was really annoying. Another issue was that after using the pc for around 20 minutes after startup, it would not allow me to click or type anymore. I googled this issue and found out that the Skylake CPUs are not properly supported jet, with a list of fixes provided. I installed a new kernel version (4.7.0), created the 20-intel.conf file and tested different kind of settings. The issue with the "flickering" seems to be solved now, only the issue with not being able to click or type stays. To be a bit more exact, typing or clicking is still -possible- but only if I click 30 times on a something it would eventually come up, or same with typing (in for example the terminal), I see the cursor flickering and after pressing a key on the keyboard at least 30 times it comes up on the screen.

Is this problem also related to the graphics not being supported? And if yes, would the problem be solved if I upgrade to a separate pci-e (nvidia) graphics card? 

I tried to google this issue but no result came up. Hope someone can help.

---

### Post by Sparky34 on 2016-10-03
- Bought a separate GPU (Nvidia GT 730) but after installation issue still came up.
- Created a new user account, and issue did not came up, so it was a configuration related issue.
- Disabled all startup applications in my own user account, and issue did not came up.
- Enabled them one by one, in the end **Caffeine** is the one that caused the issue. Hope it helps in case someone else has this issue in the future.

---

