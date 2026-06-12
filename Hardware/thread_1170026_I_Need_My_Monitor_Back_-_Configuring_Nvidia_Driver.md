---
title: "I Need My Monitor Back - Configuring Nvidia Drivers"
date: 2009-05-25
forum: Hardware
---

### Post by mulluysavage on 2009-05-25
I Currently have a scrambled mess on my display. Trying to get full resolution on my Acer x183h. I was living with 800X600 but wanted better. Tried manually editing xorg.conf as per Nvidia's instructions- replaced the driver name with "nvidia" to no effect on reboot. Launched Nvidia Driver Configuration Utility from System menu, said "you are apparently not using an Nvidia driver," and found that I could enable the proprietary driver. Did so and rebooted, to the scrambled screen. What can I do now to get a useable display? What steps should I take to get my driver working properly?

---

### Post by mulluysavage on 2009-05-25
okay... so I entered GRUB interface on restart and entered recovery mode. From there I rebuilt my config file and started up and... voila, I had the screen resolution I was trying to get from the start. Fine.. but I'm still not running the proprietary Nvidia driver... should I care? I'm going to be running mythbuntu and watching video and such - so I imagine I will want hardware acceleration.

---

