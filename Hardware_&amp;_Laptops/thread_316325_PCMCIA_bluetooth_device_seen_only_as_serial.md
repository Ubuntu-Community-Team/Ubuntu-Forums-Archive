---
title: "PCMCIA bluetooth device seen only as serial"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by lcohen999 on 2006-12-10
I'm hoping someone can help me

when I do a lspcmcia I get this result:

lcohen@lcohen-laptop:/usr/lib/pcmciautils$ lspcmcia
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:02:04.0)
Socket 0 Device 0:      [serial_cs]             (bus ID: 0.0)
lcohen@lcohen-laptop:/usr/lib/pcmciautils$ 


however Device 0 is a PCMCIA bluetooth device.

How can I change/force this to load proper bluetooth drivers?

Thanks!

---

### Post by flowKub on 2006-12-18
I'm facing the exact same problem. have you made it work manually?

Under SuSE 10.0 on the same machine, the same bluetooth-pcmcia-card runs perfectly out-of-the-box. can I get any useful information out of the running SuSE?

---

### Post by flowKub on 2006-12-22
I just installed most packages that seemed relevant, searching in synaptic for:

bluez
bluetooth
pcmcia
setserial

one of them is officially deprecated, but try that one as well if it doesn't work otherwise.

I'm not sure which one did the trick.

---

