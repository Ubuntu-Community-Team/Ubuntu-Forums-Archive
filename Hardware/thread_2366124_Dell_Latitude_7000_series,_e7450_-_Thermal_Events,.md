---
title: "Dell Latitude 7000 series, e7450 - Thermal Events, Booting Issues, Runs Slow, The Fix"
date: 2017-07-14
forum: Hardware
---

### Post by AnotherBrian on 2017-07-14
Putting this out here for the next person who runs into the issue.  
Replacing the battery and it runs like a champ. 

Symptoms were:
[LIST]
[*]Numerous thermal event errors.  These were observable in the bios log.
[*]Sudden shut off - presumably from thermal events.
[*]Laptop ran slow.  Using "apt-get install hardinfo" and running cpu blowfish resulted in slow performance numbers such as 35 versus a fast 4 under normal operation. Speculation here, but I think the intel thermal management system was throttling the cpu due to prior thermal event.  In that case, the management system was not releasing the cpu to run fast after a reboot. .
[*]System would not boot if both memory  slots had memory sticks.
[*]Booting was difficult.  It would fail to boot, got flashing lights, always posted (i think) with dell logo, then shutdown. .  Booting with no battery would require 2 steps. First boot fails.  Put in battery and of course boot fails but obviously some sort of handshake occurred between laptop and battery.  Remove battery and then it booted into bios diagnostics, then reboots into operating system.
[/LIST]

Things I did but don't think they are a factor: 
[LIST]
[*]Updated bios to latest.  Rather bizarre, I ran dell's diagnostic (from web)  while booted on windows and the system started working well - long enough to update bios. Did driver and bios updates.  Bios update requires a functioning battery.  Noticed that one of the driver updates was to the Intel Thermal Management System chipset.  I don't know if that update on windows persists when booted on linux.  Maybe the chipset gets pumped once.  I don't know.  This did not fix the system.
[*]My usage included  on my lap and possibly the ventilation ports were not fully breathing.
[/LIST]

Hope this helps the next person.

---

### Post by Autodave on 2017-07-14
Bad batteries will cause weird problems at times.  Laptops also get weird at times for no apparent reasons. Whenever I get someone's laptop that all of a sudden is doing something strange or not doing something that used to work, I clear it by removing the battery and power cord and then leaving it sit for 10 minutes at least. Reinstall battery and power cord and turn it on.  Believe it or not, that fixes quite a few of them. :-)

---

### Post by AnotherBrian on 2017-07-14
in my rublings, I am sure i did that.  i have had other systems where one has to hold down certain buttons for a period of time (e,g., 30 seconds) to cause some sort of reset.  But never tried it here. 

Some of my readings indicated dell authenticates (at least for some laptops)  the battery.  a justification I read said this was to assure people know they are getting a quality battery. (Of course its not to force you to my the dell battery).   One reading claimed that the battery will only allow a finite number of recharges.  And so on.

---

### Post by goostech on 2017-07-14
most likely a defective motherboard, to me dell is KINDA known for the mobos to be No.2 the I figured it was the mobo because its not reading the battery, the thermal temps are going iffy, having ram in both slots will cause it to not boot so the ram/ ram slots is all ****y, and the BIOS is logging ALOT of events, if your up for the DIY you can replace the MOBO or if you have the wallet thickness just buy a new computer my suggestion try a Lenovo or somthing Quad core Dell from 2007-2010 like a Dell Latitude E6510 or if you choose lenovo try a T4XX or T61p

---

