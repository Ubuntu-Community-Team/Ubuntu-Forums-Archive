---
title: "Speakers vs. Headphones - how to get them to work correctly?"
date: 2019-10-02
forum: Hardware
---

### Post by dagmann on 2019-10-02
After kubuntu 19.10 was installed my speakers worked fine, but not the  headphones. When I unplug my headphones the speakers stop working. :confused:

Does kununtu handle both speakers and headphones? If so how, and where would the speakers and headphones selection be?

My Sennheiser headphones are plugged into my Creative Labs Z sound card. Does kubuntu handle sound cards?


I take it that everyone has their speakers and headphones working properly.

---

### Post by dagmann on 2019-10-10
as I posted in the Kubuntu forums:

The secret weapons are:

in daemon.conf -------------------------------
avoid-resampling = false
enable-remixing = yes
remixing-use-all-sink-channels = yes
enable-lfe-remixing = yes
default-sample-rate = 48000
alternate-sample-rate = 48000
default-sample-channels = 6
default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe

And using AlsaMixer correctly!

---

