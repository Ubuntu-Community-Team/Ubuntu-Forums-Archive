---
title: "HDMI sound outage after upgrade to Kubuntu 14.04"
date: 2014-05-26
forum: Hardware
---

### Post by markMDW on 2014-05-26
The HDMI sound worked fine before the "upgrade" -- nothing else changed with the hardware.  I've gone into SYSTEM SETTINGS > MULTIMEDIA > AUDIO HARDWARE SETUP and fiddled around trying to get some sound, but NO LUCK.  There are two choices for sound card  "High Definition Audio Controller"  and "Built In Audio" (not sure why) plus a lot of other choices under the Profile dropdown menu.  Nothings wrong with the monitor or cable.  I've plugged it into another Kubuntu 14.04 computer and it the HDMI sound works fine.

I also switched the video card driver from an X.org to the "recommended" -- neither produce sound.  (Whatever driver WAS installed for Kubuntu 13.10 had worked fine.)  Could it be the driver?

PS -- I'll mark the thread solved just as soon as I get it working.  Does anyone have an idea?  
Thanks for helping me get the latest version of Kubuntu working flawlessly -- Kubuntu is THE most BEST 'buntu for me.  I finally feel like a power user again! :popcorn:

---

### Post by mastablasta on 2014-05-27
> **markMDW said:**
> I also switched the video card driver from an X.org to the "recommended" -- neither produce sound. (Whatever driver WAS installed for Kubuntu 13.10 had worked fine.) Could it be the driver?



most definitelly it's the driver (or it's settings). either video driver or more likely the sound driver. so if i understand correctly the propper sound ouput is not showing in the settings?

---

### Post by SeijiSensei on 2014-05-27
I have two Kubuntu 14.04 machines connected via HDMI with working audio.  One machine has an ATI card, the other an NVIDIA.  In both cases I needed to use the proprietary drivers to make this work.

---

### Post by Yellow Pasque on 2014-05-27
What GPU do you have?
```
lspci -k
```

---

### Post by markMDW on 2014-05-27
I'm don't have that pc plugged up at the moment so I can't type any BASH commands in, but I have the video card box it came in: 
It's a "PNY VERTO NVIDIA" GeForce 210 with 1024MB DDR3.  It includes DVI-I and HDMI and it supports DirectX 10.1"  Wow, I had know idea my video card had so many brand names and trademarks.  

It all worked fine before upgrading Kubuntu 13.10.

> "so if i understand correctly the propper sound ouput is not showing in the settings?"  <

The AUDIO HARDWARE SETUP has some listings for HDMI digital stereo, and I alternated between both of those.  To be honest, I really don't know exactly what I should be looking for.  There was a list with what appeared to me to be six or eight different options to choose from, with a preferred order of usage.  Two of them were highlighted as selectedable the others were shadowed out.  I could play around and promote or demote them, but it looks completely arbitrary and I'm mystified by the order.   Seems like it tries them all, one after the other.  HDMI is listed.  

Thanks everyone for taking a look into this.  I will be checking back tomorrow.

---

