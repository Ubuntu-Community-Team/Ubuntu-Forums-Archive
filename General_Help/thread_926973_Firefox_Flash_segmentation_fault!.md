---
title: "Firefox Flash segmentation fault!"
date: 2008-09-22
forum: General Help
---

### Post by Zzzach on 2008-09-22
I've been trying to figure this out FOREVER!!! Firefox still randomly crashes on youtube and certain websites. All terminal says is "segmentation fault" and a bunch of getvalue variables. I've tried both flash 9 and 10 and neither have fixed the crashes. It's driving me crazy! Is it something to do with Alsa and Pulse maybe? Plz help!

---

### Post by russlar on 2008-09-22
Are you on 32 or 64 bit?

---

### Post by Zzzach on 2008-09-22
I'm on 32 bit 8.04

---

### Post by dodle on 2008-09-22
Have you recently installed any fonts?

---

### Post by Zzzach on 2008-09-22
> **dodle said:**
> Have you recently installed any fonts?

No, this problem has been going on ever since I installed 8.04 like months ago. :mad:

---

### Post by dodle on 2008-09-22
Darn, fonts were what caused firefox to crash on me.  

> **dodle said:**
> If it has to do with the extensions, you can try deleting the files named extensions.cache, extensions.ini, extensions.rdf, and there might be another called extensions.  They are located en ~/.mozilla/firefox/dl1afknk.default

You could also try uninstalling firefox, then deleting ~/.mozilla, and reinstalling firefox.... if you haven't tried already.

Does running it from the console post any kind of error?

---

### Post by linux5uper on 2008-09-22
I followed part B in the following tutorial

[http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse+audio+fix](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse+audio+fix)

to fix a problem like yours. Check out the other sections too, if you haven't.

*edit:* Better try the updated version

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

I did it now and it works fine.

---

### Post by Zzzach on 2008-09-22
Thanks, I'll try your suggestions and let you know how it turns out.

---

### Post by Zzzach on 2008-09-22
I tried all that stuff but the website was still crashing. Then I deleted flash 10 again and tried flash 9 and the website is working now, so maybe it was a problem with flash 10. I don't know... I was having problems before with flash 9 too though, that's why I upgraded to flash 10 but that didn't fix my problems either. Maybe now things will work, we'll see.

---

