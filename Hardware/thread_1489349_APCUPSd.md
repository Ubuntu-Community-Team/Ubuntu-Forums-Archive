---
title: "APCUPSd"
date: 2010-05-21
forum: Hardware
---

### Post by RasterBurn on 2010-05-21
hello, does anyone here have any experience with apcupsd and the "APC Smart-UPS 1400" backup system that uses cable model "940-0024C" (its a non-USB serial cable) I am having some troubles making the system work... UPSCABLE is simple enough to deal with, its either "smart" or "940-0024C" both work.

The next part seems to be problematic which is the UPSTYPE the only way i could get it to work was with the following settings:
UPSTYPE dumb
DEVICE /dev/ttyS0

technically i should be able to use:
UPSTYPE apcsmart
DEVICE /dev/ttyS0

Unfortunately with the second setting apcupsd fails to work and with the first setting apcupsd doesnt gather enough crucial information in regards to the status of the UPS

as the other bit, i am using gapcmon as the frontend gui to see the information that apcupsd is gathering

---

### Post by mattster98 on 2011-01-05
I'm experiencing the same issue.  Can't figure out what is going on, other than maybe the UPS's serial port is finally dead.  It's old, but otherwise working.

Mine is an APC Smart-UPS 2200XL rackmount unit.

Have you had any luck figuring this out?

I have had smart signaling working with this UPS in the past, but at some point disconnected it, so I'm not sure if a kernel change, serial port default settings, or other changes may be the cause.

Any suggestions are appreciated.

--Matt

---

### Post by RasterBurn on 2011-01-06
I had some luck getting it to work, no major luck though, was only able to get minimal information through the serial port, unfortunately sometime mid 2010 one of the batteries in my APC died and well, didnt bother forking out the cash for a replacement battery so i havent bothered with it since

---

### Post by bluelamp999 on 2011-05-26
I'd like to *bump* this...

I've a Belkin UPS (F6C800ukUNV) attached to my 10.10 server with a serial cable (apparently the UPS will only work with the USB cable supplied by Belkin which, of course, I can't find.)

Thus far, I can only get apcupsd to work with the following settings...
```
UPSCABLE smart
UPSTYPE dumb
DEVICE /dev/ttyS0
```

This only returns a subset of the info of which apcupsd is capable.

I've managed to get the Webmin module for apcupsd working.

Has anybody any idea of what settings to try in the apcupsd conf file so I can access the full info from the UPS?

Is it even possible with the Belkin? It's fairly new (~ 3 years)

Thanks!

---

### Post by bluelamp999 on 2011-05-27
Please disregard the above!

Tried it with a USB cable and... 

```
UPSCABLE smart
UPSTYPE usb
DEVICE 
```

did the trick...

I just remember reading in the FreeNAS forums (when the box was running as a NAS) that the Belkin cable was specific to the UPS. Twaddle obviously!

Now just to source replacement batteries...

---

