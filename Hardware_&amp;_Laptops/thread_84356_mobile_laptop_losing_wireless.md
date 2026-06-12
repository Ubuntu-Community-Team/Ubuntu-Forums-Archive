---
title: "mobile laptop losing wireless"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by holiday on 2005-10-30
This is probably a noBrainer for most laptop users but for me - it's baffling.

My wireless laptop's been happily connected since install but I recently went on a trip. I could not connect from my hotel room, gave up and actually booted into windows for the first time in months.

Upon my return -- I can't connect. How can I get Ubuntu now to be as smart as it was when it installed. It found my wireless perfectly. Everyone was amazed. 

Do I have to reinstall to get my wireless back? 

BTW before I left  took the precaution of commenting out my wireless info in /etc/network/interfaces and then upon my return re-enabled it. But it didn't work. What's up?

---

### Post by holiday on 2005-10-31
Ok the problem was that the /etc/network/interfaces file had three entries for ath0. Once I cleaned up that file, and 

then 

#/etc/init.d/networking restart

I think Ubuntu should have notified me of the bad file. All I got was a 'fail' message from the commandline restart and absolutely nothing from the gui configuration utility. Not even anything in dmesg.

So a bit of sanity-checking and error-reporting on the parse of that interfaces file, I think is in order.

---

### Post by jjoyner on 2005-10-31
The thing about mine (ndiswrapper Broadcom), I have to boot up, go to Networking, click Wireless Connection, Deactivate, click Properties, drop down the box and click my ESSID, set the encryption to ASCII and then click OK>Activate>OK...It connects fine then....If I go to a new ESSID, I have to do this again...otherwise it works perfectly.

---

### Post by linuxa on 2005-11-01
**jjoyner**:

Why don't you put the info in your /etc/network/interface file (is this secure people?)

That gets loaded up at boot so the wireless info is always available by the time you get to X.

---

### Post by holiday on 2005-11-01
How does the interfaces file save us from the grief of moving about? 

Perhaps my problem is that on my home network I assign a static IP then when I'm away from home, the wireless tries to assert the static IP over whatever wireless it finds? Also the WEP settings. Perhaps the presence of a WEP key means it won't accept any other?

I tried using the Location setting but then things really started going crazy.

Do other people have this problem when they move their wireless about? Is everyone using DHCP?

---

