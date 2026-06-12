---
title: "Scrolling with DualPoint Stick on Dell Latitude E6500"
date: 2010-05-30
forum: Hardware
---

### Post by theburningor on 2010-05-30
Ok, so now that Canonical has gotten rid of the HAL in 10.04, how do I set up my dual point stick to allow me to scroll when I hold down the middle button?

I was using the directions [here]("http://wiki.archlinux.org/index.php/Dell_Latitude_E6x00#AlpsPS.2F2_ALPS_DualPoint_TouchPad") (yeah, it's Arch, but it worked fine the last few distros).

Any thoughts?

---

### Post by theburningor on 2010-06-17
(bump)

My research so far has suggested that Lucid uses DeviceKit to replace HAL, but I'm still totally unsure how to actually use DeviceKit the way I was using HAL and Xorg before that to configure these sorts of hardware parameters.

---

### Post by Xlar on 2010-08-23
I also struggling with this issue and was wondering if anyone has come up with a solution. 
I have tried googling to see if I can come up with anything but everything that I have seen is the same as what theburningor has linked to.  
Any help would be appreciated. 

Thanks if advance, 
Xlar

---

### Post by chonduhvan on 2010-12-07
Have the same problem.

I have install [gpointing-device-settings]("http://live.gnome.org/GPointingDeviceSettings"). This is GUI configuration tool for pointing devices. 
Select "DualPoint Stick" tab.
Check "use wheel emulation" and select button 2.
It`s work for me.

---

### Post by Xlar on 2011-01-04
Thanks chonduhvan,  I am going to give that a try :)

I'll let you know how it turns out.

---

