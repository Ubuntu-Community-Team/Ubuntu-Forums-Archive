---
title: "Touchpad won't work on my Acer"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by obi-nine on 2006-06-01
Hi folks,

I have an Acer 4652 LMi. About a month after I got it (and under Breezy) the touchpad went all erratic and then stopped working for about a week before mysteriously starting to work again.

About a month ago the same thing happened but this time it hasn't come back.

Today I finished upgrading to Dapper (YAY!) which has fixed my other main pain - refusing to come out of suspend properly but my trackpad still doesn't work, although it no longer seems to be giving the syslog error that it used to when I booted (something about "losing sync at byte 1").

I installed ksynaptics (I'm using Kubuntu) which gives me a control panel app to switch it on and off. When I toggle it gives me the following in my Xorg.log:

[I]Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found[/I]

But I'm still not getting any action from the pad itself.

Any ideas?

thanks,

obi-nine

---

