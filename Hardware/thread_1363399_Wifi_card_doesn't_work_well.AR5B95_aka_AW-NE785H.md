---
title: "Wifi card doesn't work well.AR5B95 aka AW-NE785H"
date: 2009-12-24
forum: Hardware
---

### Post by Scrubru on 2009-12-24
I have an ASUS laptop with Karmic. I notice that I only have a 50% reception even when the router is just 4 feet across. I have an AR5B95 aka *AW-NE785H* wifi card and after browsing the web I found similar problems with other users and they expected that Karmic would solve that problem. See [http://getsatisfaction.com/jolicloud/topics/weak_wifi_reception_on_asus_eee_pc_1005ha_p](http://getsatisfaction.com/jolicloud/topics/weak_wifi_reception_on_asus_eee_pc_1005ha_p)
I just want to see if there is some improvements. I can't wait for another 6 months for Lucid.

---

### Post by coffeecat on 2009-12-24
I believe that chipset uses the ath9k driver. Some people are getting improvements with chipsets using the ath9k driver by installing these two packages:

linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

That will install the backported ath9k driver (amongst many others). You'll need to reboot. It's worth a try. Please post back if you get an improvement. It will be useful information.

By the way, I always take the signal strength and connection speed as reported by Network Manager with a huge pinch of salt. I have a USB dongle with a Zydas wireless chipset. In Jaunty the signal was always reported as 100% - even if I put it in lead casing. Just kidding, but it never deviated from 100%. But now in Karmic, the signal strength is reported at about the 30% mark with only a 1 Mb/s connection speed. Except broadband speed tests tell me I'm getting dl speeds of about 4 Mb/s when NM says it's connected to the router at 1 Mb/s. :rolleyes:

---

### Post by Scrubru on 2009-12-24
> **coffeecat said:**
> 
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic


Thanks a lot. I think it works for me now. I used to drop out of the line frequently but the signal is very stable right now.

---

