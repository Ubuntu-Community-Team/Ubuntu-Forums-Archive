---
title: "Video Drivers for Thinkpad X61 Laptop missing in 11.04"
date: 2011-07-25
forum: Hardware
---

### Post by DuroSoft on 2011-07-25
I've been running Ubuntu for some time on my Thinkpad X61 laptop. Recently I decided to finally do the upgrade to 11.04. Previously Ubuntu was recognising the video card, and I even had the advanced window effects enabled with no problem. Now they are disabled and when I go to the additional drivers thing in system administration, nothing comes up. Is my video card, if not how can I install it, and how can I re-enable advanced window effects? :confused:

---

### Post by coffeecat on 2011-07-25
According to your other post, you are running Unity in 11.04 (and you don't like it - but that's another matter). Is this with the same machine? If you can get Unity, you can get desktop effects. You can get advanced desktop effects. Unity, being a compiz plugin, **is** a desktop effect. Perhaps you are being confused by the lack of the effects tab in the Appearance Preferences window. That's not because you can't get effects; that's because things are arranged differently in 11.04. If you want to try out different effects, install compizconfig-settings-manager, but be careful with some of them. Some compiz effects are incompatible with Unity. For example, if you want the desktop cube, do a search of the forum, **before** you break Unity. :wink:

A quick google search shows that your Thinkpad has Intel graphics. Is that so? If so, you won't find anything in Additional Drivers, because the only drivers for Intel cards are the default open-source ones, which are actually developed with contributions from Intel themselves.

---

### Post by DuroSoft on 2011-07-25
I'll just wait for it to be part of the main interface again. I thought that the fact that it was no longer in the appearance window was an indicator that my video card was no longer working with the OS. I fired up a few openGL apps and everything seems to be performing the same as before, so I think I'm actually fine in that regard.

---

### Post by coffeecat on 2011-07-25
> **DuroSoft said:**
> I'll just wait for it to be part of the main interface again.

You'll have a very long wait. :? The next release, Oneiric/11.10 will be based on gnome 3 and transition to gnome 3 is happening at the moment in the alpha stage of development. Many things will be different, not because of Unity or Ubuntu, but because of changes upstream in gnome.

Good luck! :)

---

### Post by .... on 2011-07-25
> when I go to the additional drivers thing in system administration, nothing comes up.
You have an Intel GPU, so there are no proprietary/binary drivers, and nothing should show up in additional drivers.

---

