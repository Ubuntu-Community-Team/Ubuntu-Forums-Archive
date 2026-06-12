---
title: "Assorted hardware queries"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by etherael on 2007-10-26
Hi guys,

Just finished installing ubuntu to my acer 5630, all works fine that is built into the laptop, what I was wondering was the following;

A2DP headset support, what's the current story with this? I've tinkered with a2dpd but was unable to get it to work at all, is there anything approaching a plan for incorporating this in a not mucking about in a terminal way?

Windows Mobile devices, when my windows mobile device is plugged into the laptop, it slows it down immensely (the phone, not the laptop) does anyone know why this might be the case?

The entire multiple audio output selection issue; Say I have an a2dp headset active, an onboard soundcard, and a USB headset, the sound preferences app offers the devices for you to choose which to use, but it treats "ALSA" as a single seperate entity, whereas I was under the impression that each device was actually handled *by* ALSA, does this imply that if you manually choose a different device in here it will use OSS, thus nixing software mixing? If so, how do you pick the default audio out for ALSA?

Thanks in advance

Regards
Eric

---

