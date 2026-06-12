---
title: "Sound Problems with Conexant CX20549 (Venice) on HP G6032EA Laptop"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by Psychobudgie on 2008-03-02
Hi,

I have managed to get Ubuntu installed on my HP G6032EA Laptop.
The only thing still not functioning is the Sound. The device is reported as a Conexant CX20549(Venice) and the output from aplay - l is

card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Everything reports back that it should be working and I've tried every suggested fix I have come across including downgrading and upgrading ALSA.

Does anyone out there have any suggestions I may have missed?

I have everything else working well, including the broadcom wireless and successfully solving the sound issue would finish the process off.

many thanks,

PB

---

### Post by Yellow Pasque on 2008-03-02
Did you use ALSA 1.0.16?
Try these scripts:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

You could also try OSS4 instead of ALSA
[http://paste.ubuntu-nl.org/56973/](http://paste.ubuntu-nl.org/56973/)
or see the HowTo in my sig if that does not work.

---

### Post by Psychobudgie on 2008-03-02
> **Temüjin said:**
> Did you use ALSA 1.0.16?
Try these scripts:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

You could also try OSS4 instead of ALSA
[http://paste.ubuntu-nl.org/56973/](http://paste.ubuntu-nl.org/56973/)
or see the HowTo in my sig if that does not work.

I could kiss you if I was that way inclined :)

I had already tried the alsa solution to no avail, but the oss4 solution was a new one and worked first time. I tip my hat to you.

cheers,

pb

---

### Post by Yellow Pasque on 2008-03-02
Good to hear. Enjoy.

---

### Post by Beernut on 2008-03-02
I have been chasing this problem for a couple of months.  I pretty much gave up and yesterday installed an update and all of a sudden my sound started working.  :)  This on an HP DV6000 laptop.

ALSA 1.0.14

---

### Post by vladk2k on 2008-04-12
> **Temüjin said:**
> Did you use ALSA 1.0.16?
Try these scripts:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

You could also try OSS4 instead of ALSA
[http://paste.ubuntu-nl.org/56973/](http://paste.ubuntu-nl.org/56973/)
or see the HowTo in my sig if that does not work.

I have a Fujitrsu Siemens Esprim Mobile V5545 with the same problem, alsa didn't work, even if the device was seen in all configs (aplay -l, alsamixer etc.)

Iinstalled OSS as per your instructions (the ones in your signature) and they work!
Even flash works (Even if I had to install it afterwards in firefox, twice... odd behavior but it works)
Volume control patch works also...

Just wondering... it says I have Conexant CX20548 and I'm pretty sure it's CX20549

---

