---
title: "Rotation key on Tablet PC HP touchsmart tm2"
date: 2011-04-04
forum: Hardware
---

### Post by vedovatti on 2011-04-04
Hi there,

I am opening this thread because I didn't find a solution the other threads.

Basically the HP touchsmart tm2 has a rotation key on the side of the screen that normally it rotates the screen (pretty obvious). But in Ubuntu 10.10 doesn't work. The problem is that I think that it doesn't even get detected.

When I use the command to check the keys on my PC:
```
xev
```
When press the rotation key I get no answer.
Anyway if somebody has an idea of how to activate it would be great. My xinput --list is this:
> &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Finger touch             	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen eraser               	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen stylus               	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=16	[slave  keyboard (3)]
Thanks

---

### Post by eplifeus on 2011-04-30
It´s a kernel bug, tried rotate button + fn +f3. You receive event rotate button!

Sorry my bad english!

---

### Post by vedovatti on 2011-05-01
Hi, ):P

Yes, you are right! It is a bug and is already reported to the kernel.org as Linux bug from the HP WMI driver and in launchpad too. Let's hope it would be soon fix.

Cheers

---

### Post by eplifeus on 2011-05-01
Thank you!!!!

---

### Post by android272 on 2011-05-04
dose any one know the bug report number.  I tried looking for it but could not find it.

---

### Post by vedovatti on 2011-05-05
Yes, here it is:

[https://bugzilla.kernel.org/show_bug.cgi?id=32792](https://bugzilla.kernel.org/show_bug.cgi?id=32792)

and
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579534](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579534)

---

