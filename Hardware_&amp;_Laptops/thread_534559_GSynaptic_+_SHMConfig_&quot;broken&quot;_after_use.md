---
title: "GSynaptic + SHMConfig &quot;broken&quot; after user switch"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by nickpeirson on 2007-08-25
I'm running Feisty Faun and have a synaptic touchpad installed and configured with GSynaptic. I noticed that after switching users the configuration of the touchpad seems a little broken.

Symptoms are:
Scrolling with the right edge of the pad scrolls and moves the cursor. Normally it just scrolls without moving the cursor.
Using two fingers to click, which is usually assigned to middle click, triggers a middle and left click.

It seems that the events are being captured and actioned by two different drivers, or the same driver with two configurations. I've tried opening GSynaptic to check the configuration, however it reports that SHMConfig is disabled, despite it being set to true in xorg.conf and having worked before switching users.

Does anyone have any idea where I could start looking? Let me know if any logs would be useful.

Cheers
Nick

---

