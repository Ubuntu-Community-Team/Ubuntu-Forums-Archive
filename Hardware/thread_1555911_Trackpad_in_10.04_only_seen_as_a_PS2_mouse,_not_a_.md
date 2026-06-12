---
title: "Trackpad in 10.04 only seen as a PS2 mouse, not a trackpad (Dell Latitude XT)"
date: 2010-08-18
forum: Hardware
---

### Post by gohanssjn on 2010-08-18
So I can't do any scrolling.  Laptop is a Dell latitude XT.

Any ideas?  Any other info I can give that would help?

---

### Post by gohanssjn on 2010-08-19
Well, I tried to pull up my xorg to list it, but I must be looking in an old place.  is there a new way to access it in 10.04?

---

### Post by gohanssjn on 2010-08-28
Still cannot find a way to make it re-detect the mouse :(

Very useless without scrolling on a touchpad...

---

### Post by anubhavrocks on 2010-08-28
Try this out:
[http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings)

---

### Post by gohanssjn on 2010-10-22
Yeah, no go.  Still sees my touchpad as a mouse, not a touchpad.

Here is my Xorg list (but in 10.10 now):

```

xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                       	id=11	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                       	id=12	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig MultiTouch                       	id=13	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                      	id=14	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=17	[slave  keyboard (3)]

```

---

### Post by Ayuthia on 2010-10-22
You might try installing linux-tools.  There were some updates for the Dell Latitude Alps touchpads and I think they are bundled in this package, but I could be wrong.

---

### Post by gohanssjn on 2010-10-23
> **Ayuthia said:**
> You might try installing linux-tools.  There were some updates for the Dell Latitude Alps touchpads and I think they are bundled in this package, but I could be wrong.

Didn't seem to make any difference.

---

### Post by gohanssjn on 2010-11-04
Still no luck.

I did find out that while my Trackpad uses a Synaptics driver, it is an ALPS trackpad.

---

