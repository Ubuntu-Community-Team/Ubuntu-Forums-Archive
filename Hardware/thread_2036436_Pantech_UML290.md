---
title: "Pantech UML290"
date: 2012-08-01
forum: Hardware
---

### Post by sovet on 2012-08-01
I recently purchased a Pantech UML290. I'm assuming the firmware flashed to it is the latest version as I had to get it special order from a Verizon partner. I am having the issue where it is not mounting as the devices ACM0 / ttyUSB*** via ModemManager in xubuntu 12.04. I am able to get it to mount in Backtrack 5r2, and look at it via ~ls /dev~ as well as dial out using wvdial(4g is pretty awesome by the way). I am not even gaining visibility on it in xubuntu though. Is this maybe an issue with the ModemManager's plugins to handle non standard hardware, or maybe how the kernel is handling talking to the device? Any help would be greatly appreciated as I've exhausted my limited knowledge trying to find a fix or workaround, and don't particularly want Backtrack as a daily use OS.

---

### Post by sovet on 2012-08-07
Well it seems that this wasn't the place to find my fix. :( I am back to debian stable, and running fairly smoothly for the most part. I've got a few minor bugs I need to work out with it IE: random shutdown messages from root, but that's what I get for working on a relatively new piece of hardware. I hope it's just a temperature sensor issue, but we'll find out. :confused:

Any way ladies and gentlemen,
Good luck on your ubuntu and derivatives adventure. I may be back one day, but for now I'm just a debian dude.

---

### Post by userdelroot on 2013-05-22
Those of you that are still trying to get the pantech uml290 on wvdial and your are getting an error with Init3 = AT+CGDCONT=1.... Etc

The correct line if my memory is correct is.
Init3 = AT+CGDCONT?

+CGDCONT: 3,"IPV4V6","vzwinternet","0.0.0.0",0,0

I will post my entire wvconf later...

Hope that helps some of you. I know it is kind of an old post but those modems are still being used.
I will be also working on 3g/4g switch..
Basically windows has issues also without vzw manager 
But from what I can tell it tries 4g first and if the connection is poor or not at all it goes to 3g..
Then every now and then it will check if 4g is available.

More to come later..

---

