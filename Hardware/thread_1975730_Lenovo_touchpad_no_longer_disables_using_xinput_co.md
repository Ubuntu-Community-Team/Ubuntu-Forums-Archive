---
title: "Lenovo touchpad no longer disables using xinput command"
date: 2012-05-07
forum: Hardware
---

### Post by brian71 on 2012-05-07
I have a Lenovo V570. I am running Ubuntu 11.10.

Until today, I could disable my touchpad with the following command:

xinput set-prop 12 "Device Enabled" 0

But now when I try that command, my system acts like something is holding down the Return key, and I have to restart the system to make it stop.

Here's what I get when I do a "xinput list":


&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=9	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                       	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Ideapad extra buttons                   	id=13	[slave  keyboard (3)]



Also, I don't know if this problem is related, but Ubuntu no longer remembers my wifi password, so now I'm having to type it in each time I log on.


I'm guessing that this has something to do with one of the updates I installed in the last day or two.

Any ideas would be appreciated!

---

### Post by brian71 on 2012-05-08
If anyone could at least give me an idea of some logs I could look at to start troubleshooting this, I'd really appreciate the help. It's very difficult to type on this laptop without hitting the touchpad, which causes the cursor to jump around.

Thanks.

---

