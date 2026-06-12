---
title: "Can I setup a TX1200 to run Ubu off an SD Card?"
date: 2008-09-24
forum: Hardware
---

### Post by ewangr on 2008-09-24
Am getting ready to start doing the bus commute again, and I'd really like to take advantage of my TX1200 (HP laptop, 2 gigs RAM, Touchscreen, etc). I gather from the old support forum that I should be able to get it up and running on Ubuntu, but I'd like to add a twist. I'm worried about the HD from all the bumping around on a bus, and so am wondering if I can configure it to boot and run from a 16 gig SDHC card in the internal card reader? If not, is there someway to setup a small USB drive to boot from one of the USB ports, and then have it run Ubu off the SD card?

If I do all that, will the touchscreen and the rotate button still work? Will I be able to tether my laptop to my AT&T Samsung Sync (A707) using bluetooth or my T-Mobile Dash (HTC) using a USB cable?

Thanks in advance for your help. Your assistance may help get a couple programs written, and will help me to save a few emissions compared to driving the car :-)

---

### Post by ewangr on 2008-09-24
OK, DL'd the 8.04.1 CD (which I gather is necessary to address a bug in the USB code) and installed it to my SDHC card (8 gigs - will try with the 16 gig when I get it).

Install seemed to go just fine. Reboot, and saw Grub come up, and then it went to the menu to give me my boot choices. It then gives me an error that it can't load the listed partition.

Looking at the boot script, it's starting with:
root (hd1,0)

I tried replacing that with:
root (hd0,0)

but then it would just give me a blinking cursor in the upper left.

Any ideas?

---

### Post by ewangr on 2008-09-24
OK, the trick was to change the first line to:
root (hd0,0)

and then wait about 60 seconds. It then brings up the Ubuntu system quite nicely. Now I have the rather more "mundane" issue of getting Ubuntu to recognize my Broadcom 802.11 a/b/g wireless card. Would I be able to avoid doing the whole ndiswrapper thing if I went to Ibex instead of doing this with Heron? It's going to be a pain to have to find/buy a cable so I can plug into my router just for this...

---

