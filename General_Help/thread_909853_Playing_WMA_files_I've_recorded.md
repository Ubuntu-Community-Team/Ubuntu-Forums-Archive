---
title: "Playing WMA files I've recorded?"
date: 2008-09-03
forum: General Help
---

### Post by igfud on 2008-09-03
I have an Olympus WS-100 voice recorder which records directly into WMA format on its internal memory.  It has a built in USB connector to pull the files off the internal memory.  In order to play the WMA format I installed all the GStreamer packages and the Ubuntu Restricted Extras package.  After doing this, I was able to play the files without any problems in Totem.

Today, I attempted to play one of the files.  When double clicking on it, Totem opens and the total length of the file is shown, but it doesn't play.  If I drag the time slider bar, the time will change, but the file refuses to play.  I can't think of anything that I would have done which might have caused this.

How can I go about listening to my recordings without <gasp>booting into Windows</gasp>.

Thanks,
igfud

---

### Post by aloshbennett on 2008-09-04
Is something else blocking yuor sound device?
eg, another music player or even worse, firefox on which you opened youtube a while ago?

---

### Post by mb_webguy on 2008-09-04
Try opening the files in VLC.  It doesn't use external codecs, so that would remove one potential problem area.

---

### Post by igfud on 2008-09-04
> **aloshbennett said:**
> Is something else blocking yuor sound device?
eg, another music player or even worse, firefox on which you opened youtube a while ago?

Bingo.  Closing Firefox did the trick.  Thank you!!! I'd have never guessed....I have Firefox open all the time.....

> Try opening the files in VLC.  It doesn't use external codecs, so that would remove one potential problem area.

I downloaded VLC.  While Firefox was open, it wouldn't play.  After closing Firefox, it worked great (as did Totem).  Thanks for the recommendation. I like the program.

igfud

---

### Post by aloshbennett on 2008-09-04
The flash plugin is the culprit. Poor firefox.

---

### Post by mb_webguy on 2008-09-04
Installing the Flash 10 plugin from the backports repository fixed that problem for me.

---

