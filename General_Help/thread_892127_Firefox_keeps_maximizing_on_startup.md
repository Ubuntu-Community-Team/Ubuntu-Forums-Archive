---
title: "Firefox keeps maximizing on startup"
date: 2008-08-16
forum: General Help
---

### Post by AgentZ86 on 2008-08-16
Hi all
I'm using 8.04 32 bit version

All was working perfect for a long time, then all the sudden when I open firefox it just opens maximized and I can't see the minimize/maximize/close buttons or title bar

It's sort of maximized all the time, and I can hit the F11 to give me a minimize/maximize/close button, however if I don't hit a button quickly it maximizes and hides behind the panel bar.

Why would this happen all the sudden. ??

If I turn off compiz-fusion then it appears to work normally, but if I turn on compiz-fusion it does this again for some reason.

Not really a big deal, but it is getting a little annoying.

---

### Post by carlolovearianne on 2008-08-16
Check "show hidden files" in Nautilus and try deleting the .mozilla hidden folder in Home. 

When you re-open Firefox it should be back in pristine condition.

---

### Post by fdesign on 2008-08-16
Keep in mind that doing that will also delete your preferences and bookmarks.

You will probably want to at least backup your bookmarks before you proceed.

---

### Post by chavita on 2008-09-19
Thank's a lot! thats do the job!, remember backup bookmarks!

---

### Post by crazy_fox on 2008-10-16
Its only the "appreg" file that needs deleting in the ".mozilla" folder. Then restart.

---

### Post by abbaseo on 2009-04-03
where to find this appreg in .mozilla folder ?

---

### Post by logic++ on 2009-04-03
All you have to do is to uncheck the ```
Legacy FullScreen Support
``` from System> Preferences> CompizConfig Settings Manager> WorkArounds.

---

### Post by wsscott on 2009-04-05
Had the same problem after the cat hit my keyboard.  Try pressing the F11 key.  It toggles back and forth from full screen

---

### Post by abbaseo on 2009-04-08
thanks Logic, its working fine now,so far

---

### Post by VastOne on 2009-04-08
> **AgentZ86 said:**
> Hi all
I'm using 8.04 32 bit version

All was working perfect for a long time, then all the sudden when I open firefox it just opens maximized and I can't see the minimize/maximize/close buttons or title bar

It's sort of maximized all the time, and I can hit the F11 to give me a minimize/maximize/close button, however if I don't hit a button quickly it maximizes and hides behind the panel bar.

Why would this happen all the sudden. ??

If I turn off compiz-fusion then it appears to work normally, but if I turn on compiz-fusion it does this again for some reason.

Not really a big deal, but it is getting a little annoying.


Are you a compiz user?  If so, every time there is a kernel upgrade, I have this same issue.  For whatever reason, under Preferences/Appearance/Visual Effects none of the choices are ticked.  I always have to change back to the extra tick (my preference) and then everything goes back to normal...There was a kernel upgrade today and I had to fo this all over again

VastOne

---

### Post by Pearson1 on 2010-01-11
You need to delete** .mozilla/firefox/********.default/localstore.rdf**

---

### Post by nZain on 2010-05-07
> **Pearson1 said:**
> You need to delete** .mozilla/firefox/********.default/localstore.rdf**

Thanks a lot, that did it for me. A quick search in the file revealed, that the main window hat a size property, which was set to maximize. Deleting this file did the trick and now devilspie is able to modify the geometry of firefox ;-)

Edit1: Unfortunately, this works only once. After I close firefox, it restores its desire for starting maximized.
Edit2: Creating a new profile resolves the problem for some (!) sessions... but at some point it starts maximized, again. The only thing I put in, are the bookmarks - so I don't see, how this can affect the maximize-behavior. Btw. this is not the compiz problem - I have deactivated the compiz effects.

---

