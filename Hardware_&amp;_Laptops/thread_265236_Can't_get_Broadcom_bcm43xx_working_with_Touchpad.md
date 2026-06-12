---
title: "Can't get Broadcom bcm43xx working with Touchpad"
date: 2006-09-25
forum: Hardware &amp; Laptops
---

### Post by pvangarde on 2006-09-25
Linux is notorious for not ever working out of the box. You kinda have to fight it to get it to do what you want. Spend hours reading posts and trying out different things, while praying and sacrifacing animals to the gods who wrote the kernel.

Anyway. I just got a Compaq Presario V5000Z and I can't get Ubuntu to function on it. No sir. The issues I had when I installed it fresh:

1) No wireless. lspci | grep Broadcom returns
```
0000:06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```. I found an article on this forum which led me through installing bcm43xx-fwcutter. Wireless works... but (see below)

2) Strangely, my touchpad went erratic. I dug into forums and bug reports all of last night, and saw pretty much anything from kernel upgrades to turning off powernowd. Nothing helped. 

It seems like my synaptics touchpad only can't work together with wireless. I removed all of bcm43xx-fwcutter and restarted the laptop. Now I have no problems, whereas before, dmesg would produce a gazillion lines a second of

```
psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
psmouse.c: TouchPad at isa0060/serio2/input0 - driver resynched.
```

So, anyone know how to resolve the conflict between my mouse spontaneously doing things on my screen and the wireless driver issue? I tried ndiswrapper and I can't even get it to start my broadcom wireless card.


Any help would be greatly appreciated as this is my last resort for such.

---

### Post by trubblemaker on 2006-10-17
there is an updated package for synaptics touchpad that might help your issue, i don't have that issue but it did solve some other problems for me just look up 'synaptics' in synaptic.

let me know if this works for you

---

