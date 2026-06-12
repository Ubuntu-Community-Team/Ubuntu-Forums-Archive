---
title: "64-bit flash - opera vs firefox"
date: 2008-10-16
forum: General Help
---

### Post by forger on 2008-10-16
I've always been wondering how come, in Ubuntu amd64, flash files work great in Opera browser, whereas they crash most of the time in Mozilla firefox and appear as a "gray" image block?

---

### Post by hyper_ch on 2008-10-16
it has to do with the nsplugin that doen't get (un)loaded properly... or so I heard.

---

### Post by forger on 2008-10-16
Thanks, let's hope they fix it :)

---

### Post by joebert on 2008-11-18
I actually have the oppisite problem on AMD64.

I normally use Opera, but I have to use Firefox 3 for flash.
Opera has a tendancy to lock up and the whole application fades to gray on complicated Flash movies, Youtube videos play sound but the picture remains blank.

I just recently moved from x86 to AMD64, I'd just gotten Flash working properly in Opera on that 32-bit system so this has been especially frustrating. :)

---

### Post by hyper_ch on 2008-11-18
there is now a beta version of adobe flash 64bit:

[http://www.kaourantin.net/2008/11/64-bits.html](http://www.kaourantin.net/2008/11/64-bits.html)
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

---

### Post by Arup on 2008-11-18
The Flash installed from repos works fine even though its x32 bit and needs nsplugin. With the new x64, it works even better but make sure to thoroughly remove every traces of the old plugin and nsplugin as well.

---

