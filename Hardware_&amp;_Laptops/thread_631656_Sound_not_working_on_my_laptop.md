---
title: "Sound not working on my laptop"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by Orivel on 2007-12-04
I currently own an advent 8212 laptop (link to specification [http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@1348264557.1196808174@@@@&BV_EngineID=ccdgaddmjgdfemhcflgceggdhhmdfnn.0&page=Product&fm=null&sm=null&tm=null&sku=953386&category_oid=-27757#productInformationSection]("http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@1348264557.1196808174@@@@&BV_EngineID=ccdgaddmjgdfemhcflgceggdhhmdfnn.0&page=Product&fm=null&sm=null&tm=null&sku=953386&category_oid=-27757#productInformationSection") ) I installed Ubuntu 7.10 and it worked great.  The sound worked fine, apart from when i plugged in some headphones, the internal speakers did not cut off.  I searched the internet for a solution and came across this [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto").  I followed the instructions and they were all completed, but when i rebooted i had no sound.  My laptop can no longer find a sound card.

```
aplay -l
``` returns
```
aplay: device_list:205: no soundcards found...

```

So i now have no sound at all. Can anyone help me?  I am also completely new to linux so have very little knowledge of the operating system so far.

---

### Post by Yellow Pasque on 2007-12-04
Before you do a reinstall, try OSSv4 (see link in my sig) and see if that gets your sound working.

---

### Post by Orivel on 2007-12-04
Thanks, that has worked great.  Only problem was Rhythmbox music playe made songs sound distorted, but i used Banshee instead and songs play fine. Does exactly what i wanted it to do, i can now mute my internal speakers.

---

