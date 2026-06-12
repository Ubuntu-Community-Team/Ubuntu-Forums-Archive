---
title: "Trouble getting a graphics card working. Help!"
date: 2011-06-03
forum: Hardware
---

### Post by JohneG on 2011-06-03
I got my hands on a Geforce graphics card which i have just put into the AGP slot on my main computer. When i go to boot up nothing happens on screen from either graphics card output. I have never installed a graphics card on a motherboard with an integrated graphics chip so i assume it doesn't know which one to use or there is some sort of conflict. I don't get any signal from either output, not even a boot up screen to select it in the bios. Anyone able to help?

---

### Post by Davaross on 2011-06-03
There is likely to be an option in the bios under advanced boot settings or something similar to select whether to use the integrated graphics or agp graphics. It is likely called something similar to "Init Display First: PCI/AGP". I have previously encountered a bug where the integrated graphics are disabled by the presence of an agp card but the bios does not automatically switch to the agp card. One thing to try is removing the card and changing the option I described in the bios to agp and then reinstalling the card.

Let me know how you get on.

Hope this helps,
Davaross

---

### Post by JohneG on 2011-06-03
> **Davaross said:**
> There is likely to be an option in the bios under advanced boot settings or something similar to select whether to use the integrated graphics or agp graphics. It is likely called something similar to "Init Display First: PCI/AGP". I have previously encountered a bug where the integrated graphics are disabled by the presence of an agp card but the bios does not automatically switch to the agp card. One thing to try is removing the card and changing the option I described in the bios to agp and then reinstalling the card.

Let me know how you get on.

Hope this helps,
Davaross

I have searched every option in the BIOS and have not found anything similar to what you mention. I actually can't see anything relating to AGP in the BIOS other than AGP aperture size which i have adjusted accordingly. The options in the advanced tab are -

Power-on options
BIOS Wake up
Onboard devices
PCI devices
Bus options
Device options

I don't see anything relating to displays or graphics in any of them

---

