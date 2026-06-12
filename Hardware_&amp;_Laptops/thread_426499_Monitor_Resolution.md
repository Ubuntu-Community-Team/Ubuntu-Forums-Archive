---
title: "Monitor Resolution"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by GMWeezel on 2007-04-28
My monitor supports up to 1280 x 1024 at 60 Hz as its maximum resolution. In the xorg.conf, file, I changed the monitor horizontal sync and vertical refresh values to match my monitor as well but whenever I go to System --> Preferences --> Screen Resolution, it only lists 50, 53, 54, 55 and 56 Hz refresh rates as options. Any clue on how I can fix this and have more choices available. I think my monitor may be running at a > 50 Hz frequency but the numbers on the preferences are incorrect; I'm not sure about it though. Any clue on how I can fix this?

---

### Post by Cervantez on 2007-04-28
Im guessing you have an Nvidia card?

If so, in the terminal, write "sudo nvidia-settings"

In the control panel that comes up, click on "X server display configuration"

There you can choose your resolution and refresh rate, as well as many other graphics options.

---

