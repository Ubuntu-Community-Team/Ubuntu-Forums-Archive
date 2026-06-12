---
title: "If tempted to do a full format on a usb ssd - Don't"
date: 2014-04-27
forum: Hardware
---

### Post by mc4man on 2014-04-27
Maybe this is common knowledge that escaped me, in any event am posting in case it isn't.

A couple of weeks ago decided to do a new install of 14.04 to a usb3 ssd drive which is how I run Ubuntu.
For some lamebrain reason I did a full format of the drive first, not thinking about what a poor idea it would be.

The first indication came during the install itself, normally here it takes about 2 min. to do to that drive, took closer to 25 min.
In use I was having all sorts of issue doing more than one thing at a time, even bigger problems if actively writing to the drive.
Still didn't connect the dots, thought the install was bad, did several more with basically the same results. (may of even did another full format

When it finally dawned on me what the issue was I  formated the drive to exfat & did a sample write of a 1 gig iso, the results were staggeringly poor, around 3mB/sec average, dropping at times to kB/sec
(- this drive, an angelbird ssd2go,  on this laptop generally does  solid 220 - 240 mB/sec writes.

The bigger issue then on usb3 is that 2 possible ways to correct are either not available or highly discouraged 
trim - not available on usb
issue a secure delete command - while maybe possible could be even worse that the full format, apps like parted magic will rightly not allow.
The other possible solution is to force garbage collection (drive powered & idle), tried that for 8 hrs. with little improvement, maybe if I'd let it go for days..
(on a laptop with the external drive the best way to get  "drive powered & idle" was to boot to setup (bios) and just leave there.

The resolution was to create a huge single file, in this case a 100GB iso, write it to the drive, then delete. 
(afterwhich did also leave in powered & idle for 6 hrs. or so.
While I may not have regained all it's doing about 180 mB/sec now which is more than enough to run an Os.

---

