---
title: "Asus 1215P TouchPad"
date: 2011-11-20
forum: Hardware
---

### Post by dirmansyah on 2011-11-20
2011-11-25

Oops, not really solved. :(

The "gpointing-device-settings" does not save the settings after logout or reboot. I searched on the net and found out some users also experienced the same issue. 

Also, I think the initial setting of chiral-scrollings could make users think that there is a problem with the touch pad. It would be better if the selected 'small-box' (at which the chiral-scrollings starts) is at the upper-right-corner only. Currently, all the small boxes are selected except the one at the centre.

The power manager of Lubuntu also has the same issue where the setttings of brightness are not saved. I never knew that anterograde-amnesia could attack applications too :) 


##########

Horraayyy, it is solved. :)
I remembered that I had downloaded "gpointing-device-settings" but since it did not appear on menu, I thought it was not the right one. Then I just found out that in its ".desktop" file there was "OnlyShowIn=GNOME". It is removed now.
Thanks for being patient with a newbiew.
##########



Halo,

- Lubuntu 11.10
- Asus 1215P

For Windows, Asus 1215P has Synaptics-Touchpad drivers.

For Lubuntu, currently, the touchpad can be used for tapping, tap-and-drag, and vertical-scrolling.

The horizontal-scrolling and chiral-scrollings are not available.

What should I do to have those two types of scrollings ?
(Three types, actually, since chiral-scrolling can be vertical and horizontal.)

Thanks.
.

---

### Post by dirmansyah on 2011-11-26
Does any user of Lubuntu experience the same issue concerning with PowerManager and gpointing which do not save the options?
Thanks.

---

