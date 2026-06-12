---
title: "Acer Aspire One Touchpad No Longer Working"
date: 2011-01-23
forum: Hardware
---

### Post by ebcovert3 on 2011-01-23
Greetings all. 

Here is my problem: My touchpad on my Acer AspireOne/Ubuntu 10.04 no longer functions. I have an external USB mouse that I use on occasion. One day I had it plugged in and I think I suspended my computer incorrectly. Now my touchpad won't work at all. I think that is the source of my issue but I have no idea how to address it.

Here is my xinput file:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Acer Crystal Eye webcam                 	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

```
And the output from Xorg.0.log (grep touchpad) is:
```
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) Synaptics touchpad driver version 1.2.2
(--) SynPS/2 Synaptics TouchPad: touchpad found
(--) SynPS/2 Synaptics TouchPad: touchpad found
```

I am open to all ideas. Thanks.

---

### Post by anglican on 2011-01-24
> **ebcovert3 said:**
> Greetings all. 

Here is my problem: My touchpad on my Acer AspireOne/Ubuntu 10.04 no longer functions. 

...

I am open to all ideas. Thanks.Have you tried [Fn]-[F7] to toggle it back on?

H

---

### Post by ebcovert3 on 2011-01-24
Yes. The Notify bubble shows the touchpad being engage/disengaged as it should. However, the functionality never materializes.

---

### Post by ebcovert3 on 2011-02-02
Ok I am not claiming to understand what happend, but dropping the machine into Hibernate twice over two days appears to have fixed the issue. 

Marking this solved I guess.

---

