---
title: "PCMCIA in Hardy Heron"
date: 2008-05-21
forum: Hardware
---

### Post by yury.jajitzky on 2008-05-21
Hi, recently i've installed Hardy in my Compaq Presario v2000 (AMD sempron/ 512 MB RAM), everything works fine but when i try to insert my sonyericsson gc89 (wireless modem) into my pcmcia slot, computer frezzes. i couldn't find much information on internet... please help me! thanks...

---

### Post by kjbuente on 2008-05-21
Have you tried rebooting with the card in? Does it start all the way when it does. When it freezes, can you press alt+ctrl+F2 and access a terminal?

Do you now what chip is driving your PCMCIA ports? Have you check to see if they are supported?

---

### Post by yury.jajitzky on 2008-05-21
> **kjbuente said:**
> Have you tried rebooting with the card in? Does it start all the way when it does. When it freezes, can you press alt+ctrl+F2 and access a terminal?

Do you now what chip is driving your PCMCIA ports? Have you check to see if they are supported?

hi again... when i reboot it, it stays completly freeze... nothing happens... the point is this bug didn't happen with Gutsy Gibbon, actually worked perfect... please help...

---

### Post by caudron on 2008-05-27
Just chiming in to "second" the issue.  I have been using this card for a while in 7.4 and 7.10.  After an update in 7.10, I could no longer boot when the GC89 card was in the system.  If I inserted it after boot up and then tried to run the connection script, the computer freezes.  Thinking I'd just been tinkering too much with the system, I did a full wipe and reinstall with 8.04.  The symptom remains, however.  I cannot use this card in Ubuntu currently, though I was able to previously.  Anyone have any ideas?

---

