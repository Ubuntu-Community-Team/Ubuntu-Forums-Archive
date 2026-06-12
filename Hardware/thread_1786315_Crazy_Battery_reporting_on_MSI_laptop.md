---
title: "Crazy Battery reporting on MSI laptop"
date: 2011-06-19
forum: Hardware
---

### Post by mylo9000 on 2011-06-19
My wife has a MSI A6000 series laptop and has it dual booted with Ubuntu 10.04 LTS and Windows7 that it came with. She spends most of her time in Ubuntu on an ac adapter, but on the off time she unplugs to take the laptop somewhere the battery monitor reports the charge level is at 96% and there are 4 minutes of life. after 2 minutes on batter the laptop shuts down. If you start up and go into windows7 there are is a good 3.5 hours of life on the battery.

I've been scouring google and these forums for the better part of 2 hours and i can't seem to find a way to correct the battery reporting issues.

Anyone out there have any experience with this kind of issue?

Thanks in advance.

Laptop Specs [here]("http://www.msimobile.com/level3_productpage.aspx?id=184")

---

### Post by mylo9000 on 2012-03-28
should have posted this sooner. tho, it doesn't really matter because noone has replied to this.

i fixed the issue by using this command in terminal:

```
gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false
```

it forces the battery to only go by percentage and not try to caclulate an estimated life span in minutes (which it doesn't do very well). So now we get aproximately the same battery life in linux as we do in windows.

---

