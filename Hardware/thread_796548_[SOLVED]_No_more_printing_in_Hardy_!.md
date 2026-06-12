---
title: "[SOLVED] No more printing in Hardy ?!"
date: 2008-05-16
forum: Hardware
---

### Post by MrEgg on 2008-05-16
Hello all,

Like a lot of people, I've upgraded from Gutsy to Hardy last month, and everything went nice and smooth. Ever since, I've been applying the various updates to my system.

My problem now is that as of today, my printer will no longer print. It's an Epson AC-CX11NF, connected via ethernet. I've add a similar issue in the past (with Gutsy), and applying sudo aa-complain cupsd would solve the issue. I've tried it here, but to no avail. I can still print from my laptop though, which is still under Gutsy.

I'm kinda lost as to how to solve my problem, here. I've tried stopping apparmor altogether, but that didn't help. And again, I've been on Hardy for almost 3 weeks now and everything was fine up until now.

Any suggestion would be more than welcome.
TIA,
Egg

---

### Post by redoscar3 on 2008-06-15
I seem to be having a similar experience.  I installed Hardy on my Acer laptop and configured it to print (using lpd) to my Samsung printer which is served by a Trendnet print server.  Initially, this failed until I found a thread which suggested putting AppArmor into complain mode for cupsd.  This I did, and I could again print from the Acer.

However, over the past couple of weeks, some package update has killed my ability to print.  No amount of sudo aa-complain cupsd has resurrected printing for me.

I would really like to learn how to diagnose the problem by reviewing log files and such.  Can anyone make suggestions about where to start looking for a solution to this issue?  Other computers on the network running Dapper, Edgy, Feisty, Gutsy, and Debian Sarge can still print normally.  It is only Hardy that is giving me this problem.

Thanks in advance for any help I receive.

---

### Post by briggella on 2008-06-15
Have you tried removing it and recreating it using the printing tools in Hardy. Cups is fiendishly complex to try playing with by hand.

---

### Post by MrEgg on 2008-06-15
> **briggella said:**
> Have you tried removing it and recreating it using the printing tools in Hardy. Cups is fiendishly complex to try playing with by hand.

Yes, I've tried that through [http://localhost:631/](http://localhost:631/), but it still doesn't send anything to the printer. I've tried printing through another computer (running Gutsy, having the printer shared), but I can only print the CUPS test page, nothing else. Each time, the print job is being sent and considered as finished by Cups, but the printer just doesn't receive any data (it doesn't even wake up).

---

### Post by redoscar3 on 2008-06-17
Surprisingly, the latest kernel update in Hardy has fixed my printing issues.

---

### Post by al-fred on 2008-06-17
[best free porn](http://absolutely.bedava250mb.com) 
[8mg avandia](http://abusing.bedava250mb.com) 
[accutane when will skin get dry](http://accutane.bedava250mb.com) 
[adalat non extended release](http://adalat.bedava250mb.com) 
[arizona lasix](http://arimidex.bedava250mb.com) 
[atrovent nebulizers](http://atrovent.bedava250mb.com) 
[aleve and blood pressure](http://alcoholics.bedava250mb.com) 
[allegra hotel in chicago](http://allegra.bedava250mb.com) 
[amitriptyline and cymbalta](http://amitriptyline.bedava250mb.com)

---

### Post by Cotopaxi on 2008-06-18
Just to inform you, that I am having exactly the same problems! I updated from Gutsy to Hardy and the printer worked fine (Brother MFC 5440CN). After I made a few package updates my printer is "dead". Any hints?

---

### Post by MrEgg on 2008-06-18
No, not yet, unfortunately: I'm still stuck with no printing from Hardy. So far, the only options I can see are: either revert back to Gutsy, or wait for an update that will finally fix this issue. It worked for redoscar3, so it will work for us as well.

---

### Post by MrEgg on 2008-06-24
I solved the problem with the following command :

```
sudo apt-get install libstdc++5
```


Cheers,
Egg

---

