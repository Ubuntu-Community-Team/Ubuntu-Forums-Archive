---
title: "laptop cpu fan spinning non stop on 8.10"
date: 2008-11-03
forum: Hardware
---

### Post by eldragon on 2008-11-03
the notebook is an everex stepnote sa2053.

under hardy, this never happend.

non-deterministically, during certain sessions, the cpu fan does not shut down. no matter how cold the computer is.
when this happen, /proc/acpi/thermal_zone is empty. and the sensors applet cannot find any sensors.

ive scanned dmesg with and without fan control, and there is nothing dissimilar between them. (one of the boots take a bit longer than the other). which leads me to believe there could be a race triggering within the boot process but this is way beyond my skills.

searched launchpad for a similar issue, and cant seem to find it. i would report a bug, but wouldnt know where to start.

if anyone got a clue, please drop a hint!!! thanks!

im attaching lspci -vvnn, dmesg with and without the problem, and lsmod's output with and without the problem....

---

### Post by tagger_2 on 2008-11-16
I have noticed the same thing with Ubuntu Studio 8.10,which I installed yesterday. I moved to Ubuntu desktop 8.10 this morning and it's acting the same way, cpu fan doesn't seem to stop! This didn't happen in Hardy. 

Anyone knows if this is normal?

(laptop, Dell D630C)

Thanks

---

### Post by CAIIIO on 2008-11-20
I have exact the same problem after insalling 8.10 on DELL xps1330. The FAN does not stop even when the temperature goes down to 30C.

---

### Post by bcrom on 2009-01-09
Bump.  This is a really annoying issue.  I also have Ubuntu 8.10 on a dell xps m1330 and the fan will not stop running.  I had this problem last November.  It went away by itself, but I just did a reformat and it's a major problem again.  Sometimes it will turn the fan on and off every second which gets REALLY irritating.

---

### Post by bcrom on 2009-01-09
I fixed my issue by downgrading from the Nvidia 177 drivers to the Nvidia 173 drivers.

---

