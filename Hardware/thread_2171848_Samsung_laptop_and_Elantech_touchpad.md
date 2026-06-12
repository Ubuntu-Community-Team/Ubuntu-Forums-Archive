---
title: "Samsung laptop and Elantech touchpad"
date: 2013-09-01
forum: Hardware
---

### Post by joaov-ferreira on 2013-09-01
Seems like it's a known issue and i saw some people that make it work in diferent distros, but I'm having a lot of trouble trying to put it to work.

It started when I fisrt installed ubuntu 13.04 x64 on my samsung RV411-AD1BR notebook (this model is made in brazil, so I don't know the similar model in other places, the specs can be found [here]("http://www.samsung.com/br/support/model/NP-RV411-AD1BR-techspecs") in portuguese) and using the kernel 3.8.0-29-generic.

The mousepad didn't worked at all, so I did a "fix" creating a conf file on **/etc/modprob.d/** with option** psmouse proto=imps**, and now it is recognised as a generic PS/2 mouse, so it won't have the multitouch gestures as I have on windows.

I've already tried [this]("http://ubuntuforums.org/showthread.php?t=2111236") solution and also didn't work, but this made the touchpad be recongnised as Elantech touchpad, but when I do anything on the touchpad, it goes crazy and makes random or random gestures. I also tried to install the 13.11rc7 release from the kernel, but haven't solved for me 

I don't know if it's a configuration issue, but I'm looking for a real fix for days and I haven't found any yet :(

---

