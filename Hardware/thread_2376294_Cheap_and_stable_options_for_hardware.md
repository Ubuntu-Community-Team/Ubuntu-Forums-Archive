---
title: "Cheap and stable options for hardware"
date: 2017-11-01
forum: Hardware
---

### Post by jimbobones on 2017-11-01
As it says on the tin ? I'm new to Ubuntu and looking to set up some boxes for advert display with remote access for me to change the ads

Thanks

I should have said - I need to roll out a lot of these  (100+) so cost is a serious concern

If someone would be so kind to recommend a supplier for hardware in UK that would be appreciated also - If import would be an option im keen to listen

Thanks again

---

### Post by TheFu on 2017-11-01
Welcome to the forums.

Depending on the harshness of the environment, you might need specialized gear.  On the low end, the exact interfaces required matters.  Do you need to deal with direct sunlight?  Outdoors?  Water proof/resistant?  wired ethernet?  wifi?  GSM-data modems?  Battery powered only?  What interface does the display have?  HDMI? RCA?  DVI? VGA?   Does the screen need to be included?  What size?  Is 4 inch sufficient? 8in? 10? 22? 65?  bigger?

A r-pi would be the most expensive you should get for the computer side - so about US$48 total for each.  That would be the pi, case, and power-wart.  A 2G micoSDHC for each would be extra.

There might be cheaper solutions - I've seen $10 devices with cheap displays, but they don't have networking.  Would a cheap tablet running Android with a 7-10in display work?

If I were doing it, I'd have each pull the new ad content from a central server using rsync+ssh periodically.  There is signage software for Linux-based Pis.  [https://www.screenly.io/](https://www.screenly.io/) is one option.

You have lots of details to determine.

---

### Post by coldraven on 2017-11-01
A couple of years ago I met someone who was into signage. I asked him if a Raspberry Pi was suitable and he replied that it did not have the grunt to do fancy transitions between images. This may well have changed with the new RPi3. 
I have used a RPi2 for an offline kiosk in an industrial building full of strip lights. (These will create a power spike when shutdown)  Each evening they just switch off the power to everything at the main breaker. The RPi has survived over a year of these hard shutdowns and reboots itself to the kiosk when the power comes back on.
Conclusion: The Raspberry Pi is cheap and reliable.
You can also get a Vesa mount to fix it to the back of a monitor.
Something to ponder, hope this helps.

---

