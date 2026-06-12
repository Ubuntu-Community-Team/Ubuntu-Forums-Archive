---
title: "erratic multitouch touchpad"
date: 2011-01-16
forum: Hardware
---

### Post by spigolo on 2011-01-16
hi,

i've recently bought a samsung n150 plus netbook, installed ubuntu and found it perfect except for the multitouch on the trackpad.

the bad behavior is as follows:

put one finger on it then very little later put a second finger on it and the cursor of the mouse jumps all over the place. same goes when taking fingers off: if you have two fingers and release one only slightly before the other the cursor is really jumpy. this happened on 10.10 desktop and 10.10 netbook edition (as well as jolicloud...) 

i tried many different xinput configurations,(including setting the JumpyCursorThreshold property to a various level) with no results. i followed about half a dozen threads in the forums but none seemed to have a solution. i think [there is a bug on launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/503944") for it that has a very low importance level.

things that seem to me of importance:
- when the two fingers are very very very precisely put together on the touchpad, the behavior is correct, but we're talking about a non usable precision. 

- testing the device through xinput shows that on an erratic double press the button 5 (that is, scrolling) looks like it's being pressed a gazillion times.

- the xinput device uses a elantech touchpad 

-trying the unit with an opensuse 10.3 live usb the touchpad behaves correctly, xinput reports the device as a "Im/PS Logitech Wheel Mouse" not as a symantec or elantech touchpad.


any help would be appreciated as this minor failure is very annoying on an otherwise perfect experience.

thanks!

---

### Post by spigolo on 2011-01-26
bumping this one.

really nobody with a faulty elantech driver out there?

btw, an usable workaround - ie reverting to an older generic driver that works - would be:

```
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps
```

or to set it permanently:

```
echo "options psmouse proto=imps" | sudo tee -a /etc/modprobe.d/options.conf
```

this one loads the driver i found on opensuse wich works to a level: smooth 2 fingers vertical scroll, 1-2-3 fingers tap, no horizontal scroll, no pinch and rotate and mostly no touchpad suspend while writing.

i also havent found the exact same bug on launchpad, although many similar.

any comment welcome :)

---

### Post by dilodicus on 2011-02-22
Thank you!

I've just bought a N150 plus for a friend, and was beginning to despair about the erratic multitouch and lack of vertical scrolling, not too bothered about any of the other missing features, this fix has fixed all I needed! Thank you!!!

:)

---

