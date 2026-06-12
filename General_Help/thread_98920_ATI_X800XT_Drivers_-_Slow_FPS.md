---
title: "ATI X800XT Drivers - Slow FPS"
date: 2005-12-04
forum: General Help
---

### Post by Alex[RM-UK] on 2005-12-04
Hey, 

I have been trying to install my ATI Drivers for my X800XT in Ubuntu 5.10. I have followed this guide: 

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver](http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver)

And it worked, and I thought exelent it all works! So I downloaded penguin-racer and I couldn't even navigate on the menu's. The FPS were SO SO slow it was un-usable. So I tried some test I saw on tinternet and typed some commands in Terminal. Here are the commands and outputs of them all:

[http://pastebin.com/448585](http://pastebin.com/448585)

As you can see there are many errors. Why is it? When I run gears the gears run so so slow. Here is a link to my xorg.conf file:

[http://pastebin.com/448603](http://pastebin.com/448603)

Please can someone help me sort this out! Everything else works fine (desktop wise) just games/gears are so slow.

Thanks,

---

### Post by Alex[RM-UK] on 2005-12-05
Bump. Anyone know how? Please

---

### Post by Zeroedout on 2005-12-05
try running ```
 sudo fglrxconfig 
```

---

### Post by mcrosmar on 2005-12-05
[quote='Alex[RM-UK]']Hey, 

I have been trying to install my ATI Drivers for my X800XT in Ubuntu 5.10. I have followed this guide: 

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver")

And it worked, and I thought exelent it all works! So I downloaded penguin-racer and I couldn't even navigate on the menu's. The FPS were SO SO slow it was un-usable. So I tried some test I saw on tinternet and typed some commands in Terminal. Here are the commands and outputs of them all:

[http://pastebin.com/448585]("http://pastebin.com/448585")

As you can see there are many errors. Why is it? When I run gears the gears run so so slow. Here is a link to my xorg.conf file:

[http://pastebin.com/448603]("http://pastebin.com/448603")

Please can someone help me sort this out! Everything else works fine (desktop wise) just games/gears are so slow.

Thanks,[/quote] 
Have a look here
[http://www.ubuntuforums.org/showthread.php?t=75378&highlight=xorg-driver-fglrx]("http://www.ubuntuforums.org/showthread.php?t=75378&highlight=xorg-driver-fglrx")

---

### Post by Alex[RM-UK] on 2005-12-05
Thanks it works now, But when ever I exit Penguin-Racer it restarts X, any reasons why?

---

