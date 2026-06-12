---
title: "Lenovo G530-4446 Turning Off at beginning boot"
date: 2017-10-14
forum: Hardware
---

### Post by jeredhunter1 on 2017-10-14
Hello,

I am a non-techie who has started purchasing laptops at a local Goodwill and giving them away to my students loaded with GNU/Linux software.  I have refitted about a dozen computers this year but have had no serious problems.  I use graphical installers and go.  That should give you some idea of my experience.  

Yesterday I purchased an older Lenovo G530-4446 laptop that originally ran Vista.  It boots to BIOS and allows me to select a boot order.  It also begins booting from USB.  This is the good part, now for the confusing part.

I start loading 32 bit Lubuntu 16.04 just fine.  I select either install or test to install and things start loading.  Right after the mouse appears the computer turns off.  By that I mean that the computer completely powers off and the battery stops charging.  Does this have anything to do with the battery or is the problem related to something else?  I have tried booting with and without the battery inserted from 32 bit and 64 bit USB devices.  The same procedure occurs every time.

Thanks in advance.

---

### Post by mörgæs on 2017-10-15
Are you able to install using the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by efflandt on 2017-10-17
It might be an internal electrical problem. My Toshiba laptop from 2006 with dual core Intel 1.66 GHz had no problems running various Ubuntu versions over the years and even 64-bit 16.04. And its battery still appears to take a full charge. But more recently it started sometimes not turning on properly, regardless of battery, psu only, or both. When it fails some keyboard LEDs come on and that is all it does. A Dell laptop from 2007 with core 2 dual 1.66 GHz still works fine with 64-bit 16.04, other than its battery no longer holding a charge (15-20 minutes). Something odd when I brought the Dell up to 4 GB with identical RAM previously used in the Toshiba is that the Dell BIOS recognizes that it has 4 GB RAM installed (2x2GB), but says that only about 3.3 GB is usable and that is all that shows up in 64-bit Ubuntu. I don't remember being shorted RAM when using 2.5 GB in both laptops (2 GB + 512 MB).

I also have an MSI gaming laptop (GE60-2OE) from 2013 which no longer turns on properly. It starts and runs for 7 seconds with blank screen as fans (and measured power consumption) wind down, off 4 sec, on 7 sec, off 4 sec... until I hold power button to keep it off. Have not figured out what is causing that, but it apparently has some internal electrical issue (whether fully charged battery, psu only, or both).

If your laptop has 3 GB RAM (based on quick web search of your model), amount of RAM should not be an issue. I have a 1GHz 2-core tablet PC with AMD cpu and HD 6250 graphics and 2 GB RAM that boots Ubuntu from SD card (internal 32 GB SSD has Win7 Pro) and does not even have swap. Slow, but it works.

---

