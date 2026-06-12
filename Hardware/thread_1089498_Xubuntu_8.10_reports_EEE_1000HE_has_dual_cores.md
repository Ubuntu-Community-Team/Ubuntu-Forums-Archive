---
title: "Xubuntu 8.10 reports EEE 1000HE has dual cores?"
date: 2009-03-07
forum: Hardware
---

### Post by Grendelmon on 2009-03-07
Got my Blue Asus EEE 1000HE from Amazon this week :D...  I reformatted and installed Xubuntu 8.10 on it.  Works great, and I love that the wireless doesn't need restricted drivers.  Anyway, has anyone noticed that Xubuntu 8.10 is reporting the 1000HE as having (2) Atom N280 cores???  I first noticed this while checking the performance in "System Monitor."  I also checked /proc/cpuinfo and it says I have process #0 and processor #1.  Obviously this is wrong, but weird..?  Are the 280s too new for Ubuntu to recognize?

---

### Post by Chibone on 2009-03-07
Atom 280? From my quick google, it sounds like an atom 270 with boosted fsb (533 > 667) and slightly faster clockspeed.  

That being said, it might show up as 2 cores because of hyperthreading, like in windows.

---

### Post by Grendelmon on 2009-03-07
Yeah, actully on another forum someone explained it.  The  Atom uses hyperthreading, and Ubuntu sees it as 2 cores.

The 1000HE uses the Atom N280, but it doesn't use the new video chipset, still the old GMA950 :-(

[http://en.wikipedia.org/wiki/ASUS_Eee_PC#Eee_1000_Series]("http://en.wikipedia.org/wiki/ASUS_Eee_PC#Eee_1000_Series")

---

