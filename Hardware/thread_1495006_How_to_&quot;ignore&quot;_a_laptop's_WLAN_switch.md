---
title: "How to &quot;ignore&quot; a laptop's WLAN switch?"
date: 2010-05-27
forum: Hardware
---

### Post by undaixo on 2010-05-27
Hi,

I have a VAIO notebook which has a switch for enabling/disabling wireless lan.

It seems that this button is a little broken because even in the ON position, It sometimes disables the Wireless and the indicating led does not light.

That's why I recently bought a PCMCIA wireless card.

My goal was to off the wireless switch (the intel wifi hardware) and use the new conceptronic card.

But It seems that if I disable the WLAN switch, the conceptronic connection is disabled too!

In windows, if I disable the switch, the Conceptronic card is still working.

How can I change this behaviour?

Thanks in advance,
regards.

---

### Post by pvdsar on 2010-12-12
I hope that someone with an answer to this question will share it with the world.
I have the same problem with my VIAO VGN-FE31H :-(

---

### Post by xavivars on 2011-08-22
I've got exactly the same problem. Have you managed to solve it?

---

### Post by lisergico25 on 2011-10-27
I have the same problem.
already give command 
rfkill list

with the hardware switch turned off and seems that my usb wifi is not hardswitched like the other one.
see

rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

but it still doesn't work!
i don't understand how to manage that

---

### Post by MatteoR on 2011-10-27
Hi.
I come from the Italian ubuntu-it forum (sorry for my bad English :-) )

Did you try to disable your wireless in-mount card in BIOS?

---

### Post by wirelessbug on 2012-09-03
I have this exact same problem on my old Vaio. It was in my laptop bag, which fell off a chair and hit the corner where the wireless switch is, and since then the wireless switch will seem to be set to "Off" even though it's in the "On" the position. I base this on the fact that wireless is disabled and the LED on the switch stops being lit.

I decided to get around this with a USB wifi dongle, which works in Windows, but not in Ubuntu, as Ubuntu thinks that disabling all wifi connections is the best thing to do when only one wifi device is physically disabled.

I've never used my BIOS manager before. Will I risk breaking it permanently if I screw around here? Right now my laptop is at the point where I can get the USB dongle to work if I boot up with the laptop wifi switch in the "On" position, but it stops working until I reboot again if I accidentally tap that corner. So it's usable, but frustrating enough for me to look for a solution. I don't want to make it worse, though.

---

### Post by arvati on 2012-12-09
I have the same problem too. Did anyone get ohw to solve it?

---

### Post by jwmatthys on 2012-12-13
I have a Vaio VGN-FE550G running Ubuntu 12.04. My wlan switch has been broken for a long time.

For me, it worked to type:

```
sudo rfkill unblock wifi
```

---

