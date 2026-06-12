---
title: "GeForce 6150 - unstable color correction with Envy drivers"
date: 2008-11-16
forum: Hardware
---

### Post by couzin2000 on 2008-11-16
I put together this machine for a friend who does graphic design. She's been telling me about color problems - so I checked. She's using an ASUS M2NPV-VM mobo, with a built-in video card, the GeForce 6150 chipset. Out the box, Ubuntu had some trouble recognizing it, so I installed Envy, which worked perfectly.

Now, after a while, she decided to calibrate her screen's colors. We could see the colors were off a bit, so we decided to calibrate with the screen's OSD. This worked for a time.

Then, when I finally got there I checked her Ubuntu and I could fin the control panel to apply color corrections. I finally figure I needed to install [FONT="Courier New"]nvidia-settings[/FONT]. So once that was in, it worked like a charm - gamma correction, color warmth, digital vbrance, all hat was excellent.

Except that once the settings are applied, it takes about all of 10 minutes, and the settings get "cancelled-out". Everything goes back to the default settings, which is not right. To solve this, all that is needed is to click on the menu item in **System > Administration > nVidia Settings**. Even before the panel is displayed, the settings come back. Whenever the pc is shut down, bringing it back online we also lose the settings.

How do you make them stick? How do you make them permanent?

This is fairly important, as this is for a graphic designer, as mentioned before. Thanks in advance!

---

