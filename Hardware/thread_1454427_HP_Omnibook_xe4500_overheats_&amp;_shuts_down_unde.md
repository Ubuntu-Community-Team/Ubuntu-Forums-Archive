---
title: "HP Omnibook xe4500 overheats &amp; shuts down under Ubuntu 9.10"
date: 2010-04-14
forum: Hardware
---

### Post by Grakul on 2010-04-14
Hi, All

I've been having a problem with an old notebook I got from work. The CPU temperature (queried using acpi -t) starts out low (around 30 degrees), but very quickly heats up as I use it. At around 70 degrees, the machine just powers off. If the machine is cool when I boot it up, and I let it boot all the way (into Mythtv in my case, as I have Mythbuntu 9.10 installed), then leave it alone, it runs for days/weeks without problems... until I try to do anything remotely taxing on the machine, which often causes an immediate power down.

I thought this was just a problem with the notebook, but then I found this bug on launchpad: [Aspire 5315-2713 overheats shuts down using Ubuntu 9.10]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/525756")

The people there seem to believe this is a bug in either 9.10, or the kernal used in 9.10. Doing some additional research, I found some old tutorials for controlling the fan speed, involving lsm-sensors and pwmconfig--I've also discovered that these tutorials no longer work in 9.10.

I don't really have the luxury of installing Windows or a previous version of Linux (We have limited bandwidth to download stuff, and besides the machine has a tiny hard drive, so dual booting wouldn't really be an option). I know it's a completely different notebook make and model, but could it actually be a "bug" in the way Ubuntu 9.10 controls the fan speed?

Cheers
Grakul

---

### Post by Grakul on 2010-04-15
Can nobody offer some suggestions about this issue?

The above bug report also intimated that installing updated BIOS firmware helps. I'd love to try this, but on the HP website ([http://search.hp.com/query.html?lang=en&search=++&qt=xe4500&la=en&cc=us&charset=utf-8]("http://search.hp.com/query.html?lang=en&search=++&qt=xe4500&la=en&cc=us&charset=utf-8")), I can only find a Windows installer for the latest BIOS firmware. Anyone know how I can get hold of a Linux one?

Cheers
Graham

---

### Post by Grakul on 2010-04-18
Update: I picked up my shiny new [laptop cooling pad]("http://www.bidorbuy.co.za/jsp/item/Item.jsp?Trade_TradeId=20479508") yesterday, and it works beautifully! I hammered the notebook with everything I could, and after several hours, the hottest it got was 47 degrees, and no shutdown! :)

---

