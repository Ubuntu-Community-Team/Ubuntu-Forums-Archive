---
title: "I need help badly. CPU upgrade makes ubuntu boot to terminal"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by jamesey on 2008-01-15
I upgraded my cpu today. when I booted for the first time, my monitor light stayed orange as if no video was connected. when I plugged my video into my onboard card, everything looked normal. however, I can't boot into the GUI. I see the colorful ubuntu loading logo and then the terminal starts. When I type "startx" I get an error stating "no screens found" fatal IO error 104. help please!!.

---

### Post by rfruth on 2008-01-15
Upgraded CPU from what 2 what - same system board / video controller ?

---

### Post by jamesey on 2008-01-15
I also see an error stating 
(WW) fglrx: No matching device section
and 
I'm typing this all from my cell phone. I'm desperate

---

### Post by rfruth on 2008-01-15
dpkg -reconfigure xserver-xorg might get you going

---

### Post by jamesey on 2008-01-15
I only change my processor from AMD 3000 XP to AMD 3800 X2. everything else in my shuttle st20G5 (sff pc) remained the same.

---

### Post by kostkon on 2008-01-15
I assume that now you have reconfigured X, and you are OK using your on-board graphics card.

I believe there is a problem with your Nvidia card. This becomes more obvious from the fact that you connected this card to the monitor and no signal was sent to it.

The error message
```
(WW) fglrx: No matching device section
```
means that the Nvidia driver tried but it could not find the card.

Thus, two things may happened.

Maybe you on-board card is selected as the default in your BIOS. I suppose that some settings in the BIOS got reseted when you changed your CPU.

Or maybe this card just died for some reason.

EDIT: you can give this command in a terminal to see if Ubuntu can see the card
```
lspci -v
```

---

### Post by jamesey on 2008-01-16
> **rfruth said:**
> dpkg -reconfigure xserver-xorg might get you going

you're my hero. my ATI card is doing it's thing again, and my new dual core is zipping along the way everything should be.

---

### Post by kostkon on 2008-01-16
> **jamesey said:**
> you're my hero. my ATI card is doing it's thing again, and my new dual core is zipping along the way everything should be.

Oh sorry! You have an ATI card, not Nvidia! Wrong guess but I should have know better, since the *fglrx* driver is for ATI cards. I got confused somehow...

---

