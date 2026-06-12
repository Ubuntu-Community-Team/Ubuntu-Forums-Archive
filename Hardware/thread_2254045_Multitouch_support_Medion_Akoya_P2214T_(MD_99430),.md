---
title: "Multitouch support Medion Akoya P2214T (MD 99430), Ubuntu 14.10"
date: 2014-11-24
forum: Hardware
---

### Post by Mizuti on 2014-11-24
Hello,
I am trying to get multitouch to work in Ubuntu 14.10 for my Medion Akoya P2214T (MD 99430) laptop/tablet hybrid. Ideally I would like to get it to work on both the touch screen and the touchpad, but the latter is the important one right now. I'm having some trouble identifying the touchpad as well. The drivers that came installed in Windows are for an ELAN Smart-pad. However, xinput does not show anything like that:
```
mizuti@mizuti-Akoya-P2214T:~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. eGalaxTouch EXC3000-0166-29.00.00	id=10	[slave  pointer  (2)]
&#9116;   &#8627; ITE Tech. Inc. ITE Device(8910)         	id=11	[slave  pointer  (2)]
&#9116;   &#8627; ITE Tech. Inc. ITE Device(8910)         	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                    	id=13	[slave  keyboard (3)]
    &#8627; AT Raw Set 2 keyboard                   	id=14	[slave  keyboard (3)]

```
I suspect the eGalax Inc. entry represents the touchscreen, so I would then guess the ITE Tech. entries are for the touchpad, but I have so far been unable to find a confirmation of this online. Also, I can find a lot lot of solutions for so-called "Elantech" touchpads, but is that the same brand as ELAN? In any case, that solution ([http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/](http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/)) did not work for me. Can anyone point me in the right direction?

---

### Post by Mizuti on 2014-12-08
Nobody?:shock:

---

### Post by niccer on 2015-03-28
Hi,
can you post details about the devices (lspci, lsusb) and relevant parts of the Kernel log?
Cheers!

---

### Post by Vladlenin5000 on 2015-03-28
eGlax is a well known brand of touchscreen technology, indeed.
ITE Tech and ELAN, on the other hand, are probably unrelated to Elantech. There's are open bugs reported for many of them.

---

