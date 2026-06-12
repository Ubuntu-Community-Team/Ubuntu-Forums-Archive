---
title: "Errors with mounting particular windows applications through Wine 1.1.24"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by 9thwonder on 2009-06-30
Hey guys I was wondering if anyone could help me with this problem. I was trying to install a game called Guild Wars on Jaunty with Wine version 1.1.24. However I receive a particular error in my terminal. Here is a copy of it:

dupy@dupy-desktop:~$ wine "C:\Program Files\Guild Wars\Gw.exe"

fixme:win:EnumDisplayDevicesW ((null),0,0x32eb54,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e228,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dc28,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dcb8,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.


If anyone has any advice on how I could troubleshoot this problem it would be of much help.

---

### Post by Mark Phelps on 2009-06-30
If you're going to use Wine, you need to become familiar with the CodeWeavers application compatibility site, where they list how well individual MS Windows apps work with Wine.  The link below is to the page for Guild Wars, and the rating of Garbage indicates that is most probably will NOT work:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2243]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2243")

---

