---
title: "Drooling over widescreen monitors"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by Krydahl on 2008-01-10
So I'm thinking of buying a widecreen monitor - probably [a Samsung SM226BW 22"](http://www.dabs.com/productview.aspx?Quicklinx=4GQB&CategorySelectedId=11109&NavigationKey=11109,50429).

I'm running using the onboard graphics from my mobo (GeForce 6150). I've seen quite a few threads with people discussing problems getting widescreen resolutions working. Anyone any idea if this combination works OK?

---

### Post by chewearn on 2008-01-10
> **Krydahl said:**
> So I'm thinking of buying a widecreen monitor - probably [a Samsung SM226BW 22"]("http://www.dabs.com/productview.aspx?Quicklinx=4GQB&CategorySelectedId=11109&NavigationKey=11109,50429").

I'm running using the onboard graphics from my mobo (GeForce 6150). I've seen quite a few threads with people discussing problems getting widescreen resolutions working. Anyone any idea if this combination works OK?

I have a mobo with GeForce6150, and Samsung 205BW.  Quite similar combination, and it works.

---

### Post by Krydahl on 2008-01-10
Sounds reassuring, thanks.

---

### Post by cubeist on 2008-01-10
I have a 6150 with an asus 22" and it works great.  I finally managed to set it up so that when the big screen is plugged in the laptop screen is off.  You can also set it up as a dual screen or two separate screens.

---

### Post by Krydahl on 2008-01-10
Mine's a desktop and I'm only planning to run the one monitor, but it sounds like it should be ok. Now I just need to part with my hard earned cash...

---

### Post by articpenguin on 2008-01-10
i have a Geforce 6100 and i have a 19inch widescreen monitor at 1440x900 and no slowdowns:)

---

### Post by Krydahl on 2008-01-15
So I've bought the monitor now - it's big and shiny and very nice. No probs getting the resolution I wanted to work (had to edit the xorg.conf file, but that was easy).

Screen refresh rate is another matter. I've added lines for horizsync and vertrefresh, but when I look in system -> preferences -> screen resolution, it only reports 50 Hz. I should be at 75.

Interestingly, there an option in compiz CCSM for the refresh which I've set to 75. Anyone any idea if that overrides the basic gnome one? If not, how do I set it where it should be?

---

### Post by chewearn on 2008-01-15
> **Krydahl said:**
> So I've bought the monitor now - it's big and shiny and very nice. No probs getting the resolution I wanted to work (had to edit the xorg.conf file, but that was easy).

Screen refresh rate is another matter. I've added lines for horizsync and vertrefresh, but when I look in system -> preferences -> screen resolution, it only reports 50 Hz. I should be at 75.

Interestingly, there an option in compiz CCSM for the refresh which I've set to 75. Anyone any idea if that overrides the basic gnome one? If not, how do I set it where it should be?

Due to workaround at nvidia to support twinview and limitation of xrandr, the refresh rate reported by nvidia driver to xrandr is not correct.  Since you have a LCD, this refresh rate shouldn't matter (no eye strain like it was in CRT), so it's best to leave it alone.

Only reason to start messing with it is, if you got screen artifact, or video playback stuttering (some people have reported such problems).

---

### Post by Krydahl on 2008-01-16
No, no problems like that. It looks fine. I guess when you've just forked out for an expensive bit of kit, you like to think it's running its best is all.

---

### Post by scizzo on 2008-01-16
I am not using a onboard card however I am using a 226CW monitor with a 920T as dual monitor. IMO it all works just fine and I did the best buy ever when getting the 226CW.

---

### Post by Daelyn on 2008-01-16
> **cubeist said:**
> I have a 6150 with an asus 22" and it works great.  I finally managed to set it up so that when the big screen is plugged in the laptop screen is off.  You can also set it up as a dual screen or two separate screens.

Would you mind posting some information about how? 
Maybe a copy of your Xorg.conf ?

Thanks

---

