---
title: "two monitors?"
date: 2019-05-14
forum: Hardware
---

### Post by naomibrown on 2019-05-14
Hi,

I've got a bit stuck trying to work out whether I can use two monitors or not with my Dell XPS 8300. I've got two ports at the back of my desktop. It's a DVI -D one (I learnt there were different types today....). The ports will both allow me to plug in the same cable and display the single monitor correctly. I've tried using lshw ([following these instructions]("https://askubuntu.com/questions/31618/how-can-i-find-my-hardware-details")) to see if I can see whether it supports two monitors or not, then got lost in the detail. What exactly am I looking for to see if it will work? 

Any presumably I can use any monitor that is a DVI -D one as long as I also get the right cable?

Thanks,
Naomi

---

### Post by Autodave on 2019-05-14
It should work just fine.  You need to get the correct cable and hook it up and let us know what happens.

---

### Post by naomibrown on 2019-05-14
Thanks. I'll give it a go ....

---

### Post by TheFu on 2019-05-14
It would depend on the GPU.  Usually, but not always, if the GPU has the port, than it can be used concurrently. The driver must support it and there are multi-monitor setup tools.  The easiest is lxrandr. If you don't have it, just install it. Tiny.

---

### Post by mastablasta on 2019-05-16
VGA monitor can also be connected to DVI-D using an adaptor. usually such adaptors come free with graphics cards, but not always. in any case they are not too expensive.

other two common types of output are HDMI and newer DP (display port). these can also be used for 2nd monitor and usually work out of the box. 

there are various adaptors for various ports out there.

VGA is very old but i can see it is still used a lot on projectors, so usually cards would have it on as well or offer an adaptor when you purchase it. it is often still fund on business hardware.

---

### Post by TheFu on 2019-05-16
DVI-I adaptors come with the cards, IME. These just convert the existing analog into VGA.

DVI-D adaptors need to be "active" and cost a little more. Adaptors, if included, are for HDMI, not VGA. Also, most VGA adaptors are limited to 1080p or if they claim higher resolutions for VGA, they don't output the correct EDID information, so we get to do all sorts of debugging, tweaking and manual customization for the EDID data, xorg files and client-side GPU overrides.  I have a little experience doing this to get an nVidia 1030 GPU working with a VGA KVM switch.  It was not a fun 3 days to get 1920x1200p working.  If you only want 1080p, I suppose any active DVI-D to VGA adaptor will work. If you want higher resolution, be prepared to fight more than should be necessary.

None of the 10xx or 20xx nVidia cards support VGA output. I've only seen fakes with VGA ports.

---

### Post by mastablasta on 2019-05-17
some low profile ones do have VGA, though it is likely secondary display and then needs to be set as primary.

---

### Post by naomibrown on 2019-05-25
It works! :) I just plugged it in using an adapter and then changed the settings so that it picks up the second monitor.

---

