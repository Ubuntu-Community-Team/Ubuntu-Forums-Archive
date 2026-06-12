---
title: "Firefox &amp; FLASH"
date: 2008-10-21
forum: General Help
---

### Post by Rob2008 on 2008-10-21
Having trouble with flash installed version 10 via a .deb file but some websites wont display .swf at all YouTube displays them but i have to double click on them then they crash

Rob

---

### Post by sethvath on 2008-10-21
Do not install anything from untrusted sites. Which version of ubuntu are you running 32bit or 64? 

[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

After installing type ```
about:plugins
``` in firefox and make sure under shockwave flash its listed as Shockwave Flash 10.0 r12

---

### Post by AlanR8 on 2008-10-21
Didn't have many problems with Flash 9.* and 10.* just works for me. 

Kubuntu 8.4.* on this machine and Intrepid Beta on the EeePC

---

### Post by Vantrax on 2008-10-21
Make sure that FF isnt trying to use another method of rendering flash like VLC. Sometimes even with flash installed FF doesnt want to use it.

That being said flash has been a problem for linux in general for a little while. The 32bit binarys are working well now but the x64 are very poor.

---

### Post by ajgreeny on 2008-10-21
If you have the 32 bit system, get the .deb from the adobe site and you shouldn't have any problems with it.
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by sethvath on 2008-10-21
> **Vantrax said:**
> 

That being said flash has been a problem for linux in general for a little while. The 32bit binarys are working well now but the x64 are very poor.

The x86_64 method described in ubuntugeek works. I would say flash 10 is more stable in 64bit compared to flash 9. Sites that didn't use to work well at all under flash 9 could be rendered without stuttering or causing FF to crash.

---

