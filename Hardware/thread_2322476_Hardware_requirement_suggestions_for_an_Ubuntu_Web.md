---
title: "Hardware requirement suggestions for an Ubuntu Web Server"
date: 2016-04-28
forum: Hardware
---

### Post by james221 on 2016-04-28
Hi guys, 

I run a small business offering SugarCRM to our customers. We have dedicated webserver (ubuntu) from Germany where our customer systems are located.

I'm in need of an on-site webserver to use as a backup machine, that i can store backups and replicate the databases in case of the servers going down in Germany.

I've built PC's many years ago, and my plan is to build a fairly powerful PC to store in-house that could serve as a web-server if things went pear-shaped.

[B]Im thinking of:
[/B]
Intel Core i7-6700K 4GHz Socket 1151 8MB L3 Cache
Gigabyte GA-Z170XP-SLI Socket LGA 1151 HDMI 7.1 Channel Audio ATX Motherboard
Corsair Vengeance LPX 32GB DDR4 (2x16GB) 2400MHz C14 Memory Kit
Samsung 850 EVO 1TB 2.5inch SSD

Does this sound fair? Do you see any issues running a web-server on these specs?

Or should I get a proper server like: 
[http://www.ebuyer.com/566940-hpe-proliant-dl385p-gen8-third-generation-opteron-6320-2-8-ghz-8gb-ram-2u-f0b19a](http://www.ebuyer.com/566940-hpe-proliant-dl385p-gen8-third-generation-opteron-6320-2-8-ghz-8gb-ram-2u-f0b19a)

or

[http://www.ebuyer.com/568138-hpe-proliant-ml350p-gen8-base-8gb-xeon-e5-2620v2-tower-server-736958-421](http://www.ebuyer.com/568138-hpe-proliant-ml350p-gen8-base-8gb-xeon-e5-2620v2-tower-server-736958-421)

I'm not really sure what the difference would be, although the spec : price ratio seems poor with an actual 'server'. :confused:


Many thanks!!

---

### Post by mörgæs on 2016-04-30
Hi, welcome to the fora.
The CPU you mention belongs to the Skylake family, which needs some special settings in order to disable one of the power save modes. It's probably not a problem for you as a web server is not likely to need the highest possible powersave.

---

### Post by gordintoronto on 2016-04-30
How active are your clients? Your configuration seems like overkill unless you're getting more than a dozen website hits per second. Then again, I have no experience with SugarCRM, so maybe dozens of hits per minute would be the yardstick.

Less CPU and memory might free up money to RAID the drive. SSDs don't give you any warning before they stop working.

---

