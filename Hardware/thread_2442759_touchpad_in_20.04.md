---
title: "touchpad in 20.04"
date: 2020-05-07
forum: Hardware
---

### Post by rovdme on 2020-05-07
Dear Ubuntu Users, 

After updating to 20.04 my touch-pad is less responsive. Mainly 2 finger scrolling. It doesnt recognize 2 finger scrolling 100% accurate. It does in 19.10, flawlessly! 
With 20.04 it recognizes 6 out of 10  times two fingers on the touch-pad. The other 4 times as an one finger movement. i tried several other distro's to see if its related to Ubuntu, gnome or x11. All distro's with a newer kernel have the same problem; DE doesnt matter, x11, wayland either. 
Seems to be al driver problem in the newer kernels. Maybe a setting? 
Xinput says it's a Synp/2 synaptics touchpad. 

Is there a solution, conf. of some kind that can fix this?

Kind regards,

---

### Post by Claus7 on 2020-05-08
Hello,

and welcome to the forums!

Having problems with the touchpad myself, I tried to track it down from system logs. I got different errors, with some of them being related to kernel issues. 
Seems that your problems are kernel related issues as well, from your trials. One difference is that I started facing problems prior to 20.04 version.

As a result my proposal would be to start from there in order to have a better picture of the problem.

Regards!

---

### Post by rovdme on 2020-05-11
Thanx! haven't figure out whats going on. Only solution for now is installing synaptic drivers. Synaptic has priority over libinput at startup, so just installing it is all i had to do. this only works on X, wayland doenst work with he synaptics driver.

regards

---

