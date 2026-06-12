---
title: "Patriot 3070 trouble"
date: 2008-11-17
forum: Hardware
---

### Post by kwhyles on 2008-11-17
Hello, I'd just like to say I appreciate any help in advance.

Laptop Specs:

# Via C3 proseccor 1.20 GHz
# 133 MHz FSB
# 64 Kb Cache
# 256 Mb RAM
# 40 Gb Hard Drive
# 14.1" TFT Display
# 64Mb integrated graphics

OK I'm new to linux, I've installed it on my PC before fine but cant get it to work on my dads laptop.)
I've looked through the forums and tried to do numorous solutions:

> LiveCD = black screen after orange loading bar

Alternative CD = scrambled screen (as does safe graphics for both)

I even tried openSUSE = managed to install through VESA (got problems with desktop viewing, so used this to try and get ubuntu to work)

So I managed to load ubuntu taking following process:

```
# Boot LiveCD
# Install ubuntu (F6 - change "quiet splash" to "break=bottom") Enter
# chroot /root nano /ect/x11/xorg.conf
# Under "Section 'Monitor'" added:

HorizSync 36-52
VertRefresh 36-60
Option “MonitorLayout” “LVDS, AUTO”

# Then saved and booted with these options
```

I didn't expect this to work (I was trying anything) but it did, but then I got a problem once ubuntu started to install it stuck on 15%.
I've formatted the hard drive and tried installing on a clean partition.  

Just changed "LVDS" to "VESA" to see if I get any luck with that but seems to still be stuck on 15%
I will try to burn a new LiveCD in the morning.

Meh, I dont know!  Let me know if you need any more information...I will try my best.

---

### Post by kwhyles on 2008-11-18
bump

I'd really appreciate some help.  I've tried a new LiveCD and still the same, it wont load past 15% 

:confused:

---

### Post by kwhyles on 2008-11-27
For anyone getting the same trouble as me...

I managed to get 6.10 (Edgy Eft) installed onto this machine :)
Download it from here:

```
http://old-releases.ubuntu.com/releases/edgy/
```

---

