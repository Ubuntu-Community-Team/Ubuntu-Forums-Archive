---
title: "PCMCIA Usb and usb modem issue."
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by christhemonkey on 2006-10-13
This thread is for my brother and his laptop,

his issue is this:

He has a compaq armada, but the built in usb 1 port is broken.

So he now has a 4 port usb2.0 pcmcia expansion card.

Unfortunately, to get this to work at all, the OHCI-HCD module had to be blacklisted.


Now his usb ports are working, and he can use them all fine and howdydoody.
but one of the things he needs his usb ports for mainly, is for his usb modem.
Which is, understandably, vital for his university revision.
The usb modem, when plugged in, produces no output at all on dmesg.
The power light on it also does not even switch on.

The usb modem is a SpeedTouch USB ADSL Modem. (of unknown revision, but using PPPoE) and as i understand it, uses the ohci-hcd module?
So without it he cant seem to get online?
But with it his usb ports wont work so he wont be able to get online anway?

He is currently offline, but with very limited access to the internet.
He is also living in hull (about an hour away from me) so i cant help in person.

Any help at all in this rather interesting situation would be much appreciated.

---

### Post by christhemonkey on 2006-10-22
An update for any one who reads this,

My brother is coming home for his birthday and bringing his modem and laptop with him.
I shall fiddle around with it when he comes back.


Someone else with my brothers vague sort of usb/pcmcia/external-hd problems:
[http://lists.xensource.com/archives/html/xen-users/2005-08/msg00452.html](http://lists.xensource.com/archives/html/xen-users/2005-08/msg00452.html)

But they never reached a solution.

---

### Post by christhemonkey on 2006-11-24
Just to say a solution was reached,

the problem was, the pcmcia usb 2 expansion port was being underpowered.

It came with a cable that gives it the neccesary voltage (plugs into a ps/2 port or another usb), and this enabled it to get the power required to be able to use the pcmcia card with his modem.

---

