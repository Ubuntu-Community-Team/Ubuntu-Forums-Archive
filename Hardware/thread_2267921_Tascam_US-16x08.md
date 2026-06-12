---
title: "Tascam US-16x08"
date: 2015-03-04
forum: Hardware
---

### Post by jdieter on 2015-03-04
Had a hell of a time getting this thing to work with ubuntu studio 14.04.2
The problem was that in QjackCtl - the "interface" selection drop down was greyed out.
After much of a muchness I figured out how to make it work:

1: power on the us16x08 BEFORE powering on the pc
2: after the pc powers up - start QjackCtl - go into settings
3: use the "server" drop down to select something other than alsa - then back to alsa until the "interface" drop down becomes enabled
4: select the us-16x08 as the interface, set input channels to 16 and output channels to 8
5: save and start jack
You will now have all channels available for patching in ardour DAW.

note: pulse audio sees the board as a 7.1 with no inputs (mics) - thats fine I guess - you can select the US-16x08 and your system sounds will play through outputs 1 and 2

---

