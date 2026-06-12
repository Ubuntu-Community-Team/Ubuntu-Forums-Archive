---
title: "Nvidia 8600gt resolution problem"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by icantdothatdave on 2008-02-03
Hello. I am unable to change the resolution of my Nvidia card to anything other than 640x480. It was working fine until I had to clear my BIOS because of an issue with the fan speed on my board. After clearing the BIOS Ubuntu booted into 640x480, and it can't be changed by anything that I've tried.

So far I've tried a dpkg-reconfigure, I've tried using Envy to set up the drivers, I've tried the Nvidia settings manager, and I've tried reinstalling Ubuntu. My motherboard is an Abit IP-35 Pro, and I'm using Gutsy 64-bit. Ack! :(

Please help!

---

### Post by overdrank on 2008-02-03
> **icantdothatdave said:**
> Hello. I am unable to change the resolution of my Nvidia card to anything other than 640x480. It was working fine until I had to clear my BIOS because of an issue with the fan speed on my board. After clearing the BIOS Ubuntu booted into 640x480, and it can't be changed by anything that I've tried.

So far I've tried a dpkg-reconfigure, I've tried using Envy to set up the drivers, I've tried the Nvidia settings manager, and I've tried reinstalling Ubuntu. My motherboard is an Abit IP-35 Pro, and I'm using Gutsy 64-bit. Ack! :(

Please help!

HI and if you reset you bios you may have changed your graphics settings. I would start there and check the voltage for the graphics.

---

### Post by icantdothatdave on 2008-02-03
Okay, I'll check that. One other thing that I noticed is that in Windows (this is a dual boot) the resolution used to max out at 1680x1050, the top resolution of my monitor. Now it slides all the way up to 2048x1536, which is way beyond the range of my monitor. What is that a symptom of?

---

### Post by overdrank on 2008-02-03
> **icantdothatdave said:**
> Okay, I'll check that. One other thing that I noticed is that in Windows (this is a dual boot) the resolution used to max out at 1680x1050, the top resolution of my monitor. Now it slides all the way up to 2048x1536, which is way beyond the range of my monitor. What is that a symptom of?

HI and I would say that your bios could have been set a fail safe and when you reset the changed to normal. There should also be a optimized settings also. Or it could have reset the opposite from normal to failsafe.

---

### Post by icantdothatdave on 2008-02-03
When I reset the BIOS I used the optimized settings. I'm pretty sure that's what it was set to by default. Now I am trying the fail safe, and that is definitely not what it was set to by default. Fail safe has the same results. Another important thing I should have noted earlier is that I am able to use 1680x1050 in Windows, even though there is the issue that I stated earlier.

---

