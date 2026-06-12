---
title: "Harddrive spinning down while on battery"
date: 2012-05-05
forum: Hardware
---

### Post by CaptnKnot on 2012-05-05
hello there!

I have quite an issue here, tried to find a solution to it but i cannot find anything.

When i unplug my laptop (Dell Vostro 3350) then the harddrive starts to spin down. This is very irritating becase it goes into some sort of "off" mode and when it starts to spin again it gives away some sort pc-speaker "beep". this happens about every 5 min or so. I would like to disable the spinndown completely becase i don't care for the batterylife.

I have tried install laptop-mode-tools and disable all sorts of things in the laptop-mode.conf but nothing seems to help.

this started when i upgraded to 12.04, i didn't have this issue in the 11.10 release.

anyone have a thought on this?

---

### Post by CaptnKnot on 2012-05-06
mind if i bump this up a bit? still need help.

---

### Post by CaptnKnot on 2012-05-10
ok, so i have found that previous versions of ubuntu have an option in the power preferences to "spin down harddrive when posslbe" (or something like that), any idea how to get that option back? I really need some help with this.

---

### Post by eleftg on 2012-05-23
See [https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/952556](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/952556)

This is a known bug. Edit /etc/hdparm.conf and:

1. uncomment  apm=255
2. add        apm_battery=255
3. reboot

If you have laptop-mode installed, remove it because it somehow conflicts with hdparm

Anyway, a fix has been released but the conflict with laptop-mode cannot be resolved by this fix.

---

