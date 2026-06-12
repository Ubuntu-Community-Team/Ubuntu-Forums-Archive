---
title: "ClearWeather Screenlet not Working In Hardy"
date: 2008-07-18
forum: General Help
---

### Post by Maverick88 on 2008-07-18
I just installed Hardy and screenlets.  One of the screenlets I installed is ClearWeather.  Run it runs it complains it cannot find the Internet.

I do have internet and Firefox surfs the web just fine.

What is wrong?  

RobK

---

### Post by Chudilo on 2008-07-18
Make sure you are on screenlets version 0.1.2
I had the same problem with 0.1.1 (ClearWeather had some sort of a conflict)

---

### Post by Maverick88 on 2008-07-18
Yes, I am using Screenlets version 0.0.12. but I still have a problem with ClearWeather.  

Any ideas?  Or should I file a bug report?

---

### Post by Maverick88 on 2008-07-18
It is a bug in the code (Screenlets version 0.0.12).

Here is the fix..

open /usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py with you favorite editor. Remove the two occurrences of &prod=xoap, and save it. Then Re-start all screenlets.

Now I see the weather!

---

### Post by jkyahoo101 on 2008-07-18
It won't let me save it.

---

### Post by stldirty on 2008-07-19
> **jkyahoo101 said:**
> It won't let me save it.

```
gksudo gedit /usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py
```

type that into a terminal

---

### Post by jkyahoo101 on 2008-07-19
Wow thanks a lot.

---

### Post by SunnyRabbiera on 2008-07-19
Yeh I had issues with clearweather myself, I could give that fix up there a try.

---

### Post by irshadcharm on 2008-07-19
Do i have to restart after editing the ClearWeatherScreenlet.py file?

---

### Post by jkyahoo101 on 2008-07-19
No.

---

### Post by jsaulters on 2008-08-08
Thanks for posting the fix!

---

### Post by trash on 2008-08-19
can somebody with clearweather verify CAQC0213 for me, i did the fix but clearweather still won't work.

EDIT: nevermind, it's the xoap.weather.com and weathernetwork.com sites that are buggered up.
CAQC0213 shows up just fine at weathernetwork.com but xoap.weather.com can't find it. If i put CAXX0213 in clearweather i get Kapuskasing weather instead of Huntingdon,quebec... other may be having the same stupid problem so i hope this helps somehow... too bad they all couldn't use the same codes!

---

