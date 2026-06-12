---
title: "Slow wireless speeds when transferring data to NAS"
date: 2015-07-16
forum: Hardware
---

### Post by Hamish_Claxton on 2015-07-16
Hey Guys,

I've noticed that when I've been copying data to my NAS the speeds vary to a maximum of 3.5 MB/s. On Windows I am able to achieve a maximum of 13 MB/S when transferring data. 
Wireless Card is Intel® Centrino® Ultimate-N 6300. Not sure how to configure the device to achieve optimal speeds. Any help is appreciated.

Thanks in Advance,
Hamish

---

### Post by Hamish_Claxton on 2015-07-18
Turns out Wireless-N is broken in the Linux driver. Are there any cards that are fully supported by Linux?

---

### Post by weatherman2 on 2015-07-18
It is not broken in the newest versions of the iwlwifi Linux driver.  I use my Intel 6235-N Centrino card daily and get excellent 802.11n transfer speeds in Ubuntu 12.04, on numerous different routers.

Some people claim that disabling 802.11n with certain Intel wireless cards fixes connectivity problems, but I have used the 6235 and other Intel cards in several laptops without needing to disable 802.11n.  I would consider that unacceptable.

But we don't know what version of Ubuntu you are using - ?

With newer versions of the iwlwifi driver, FYI, you can the "11n_disable" parameter to different values (try 8) that don't actually disable 802.11n speeds.

---

### Post by Hamish_Claxton on 2015-07-18
Hmm, I'm running Ubuntu MATE 15.04. I've tried a few things like disabling power management and didn't get anywhere. Yeah, I agree disabling 802.11n is unacceptable. Would the "11n_disable" parameter, disable the ability to connect to N networks?

---

### Post by Hamish_Claxton on 2015-07-18
Okay, so I tried the fix stated in this guide -[http://http://bernaerts.dyndns.org/linux/74-ubuntu/322-ubuntu-trusty-intel-centrino-6235-slow-freeze](http://http://bernaerts.dyndns.org/linux/74-ubuntu/322-ubuntu-trusty-intel-centrino-6235-slow-freeze).
My speed on Ubuntu MATE has increased from ~1.5 MB/s to about ~4.5 MB/s. However still no where near the speed I was getting on Windows.
Also the speed slowly drops, was on 4.5 MB/s then went down to 3.7 MB/s and still dropping.

EDIT: I removed all the options except 11n_disable=8 and the speed seems to be staying around 4.5 MB/s. Copying an 8GB file to test.

EDIT 2: Tried the 2.4 GHz band and the speed is a lot slower ~2.0MB/s.

---

### Post by weatherman2 on 2015-07-19
How are you comparing the speeds you get in Ubuntu with the speeds you get in Windows?

4.5 MB/s is a tad slow but depending on how your router is setup and how much interference there is in your area, that may not be terrible.  Are you using 40MHZ double channels?  Using WPA2 + AES encryption (or no encryption)?

---

### Post by Hamish_Claxton on 2015-07-19
I'm comparing them by copying a file over the network to my NAS. On Windows I get about 13 MB/s. Hardly any interference in my area. Network is currently setup to use WPA2.

---

### Post by weatherman2 on 2015-07-19
Are you seeing 13 MB/s as the final average transfer time or is that an indicator of the copy speed from Windows while the file is copying?  Are you transferring a large file?

Does your router give you connection information about various clients, to know how how fast the client is really connected to the router?  (Mine does - so if I'm close to my router and using a 40MHZ dual channel, I might expect to see connection rates closer to 300Mbps but over 150Mbps at least.  But if never goes above 150Mbps, maybe it's only using a 20MHZ channel for example.)

---

