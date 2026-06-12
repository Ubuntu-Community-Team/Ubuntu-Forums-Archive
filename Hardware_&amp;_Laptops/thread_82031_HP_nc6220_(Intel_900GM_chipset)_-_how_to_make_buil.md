---
title: "HP nc6220 (Intel 900GM chipset) - how to make built-in &amp; external monitors Just Work?"
date: 2005-10-25
forum: Hardware &amp; Laptops
---

### Post by meldroc on 2005-10-25
](*,)

I'm having a lot of problems trying to configure my system so I can switch between the internal 1400x1050 display and the external HP 2035 LCD monitor plugged into the DVI port of its docking station (running at 1600x1200).

Currently, I can switch between an xorg.conf that runs the external monitor at 1600x1200 beautifully, and another one that runs the built-in monitor at 1280x1024 (really ugly since the monitor's native resolution is 1400x1050).  What's funny is that I used to be able to get 1400x1050 resolution when the laptop was running Hoary, but that stopped working when I moved to Breezy.

Ideally, I'd be running dual-head, but I'd be happy with an arrangement where I can have a mirrored display or one where I can hotkey between the internal and external displays.  Anybody have any ideas how to make this work?  The i810 drivers just utterly suck at enabling displays to Just Work. ](*,)

---

### Post by tekmerc on 2005-11-06
I have the same laptop which I use with a lcd monitor connected to a docking station at work. The lcd resolution is 1280x1024 and the laptop has a native resolution of 1400x1050. I just use xrandr (Gnome System->Pref->Screen Resolution) to pick the right resolution once I boot up and it just works.

Make sure that you have a 1600x1200 resolution in your xorg.conf file.

---

### Post by tekmerc on 2005-11-06
For fixing the native resolution on the laptop screen you need the 915resolution hack. It is pretty easy.

I documented my experiences here:

[ubuntu-breezy-on-hp-nc6220]("http://astibharath.org/blog/ubuntu-breezy-on-hp-nc6220/")

---

### Post by tytus on 2006-10-14
> **meldroc said:**
> ](*,)

I'm having a lot of problems trying to configure my system so I can switch between the internal 1400x1050 display and the external HP 2035 LCD monitor plugged into the DVI port of its docking station (running at 1600x1200).

Currently, I can switch between an xorg.conf that runs the external monitor at 1600x1200 beautifully, and another one that runs the built-in monitor at 1280x1024 (really ugly since the monitor's native resolution is 1400x1050).  

I did not get even to this point :( Could you be so nice an post the two xorg.conf files that your are using. I can't get my external monitor to go beyond 1024x768. I have the same laptop except that the max resolution of the build in LCD is 1024x768.

Thanks

---

### Post by tytus on 2006-10-25
I got my external monitor to work with 1600x1200 (sort of) I had to boot with the external monitor connected and and use fn+F4 to switch to the external monitor bofore X started.

---

