---
title: "Fusion-Icon makes Compiz work but Compiz is broken?"
date: 2008-09-07
forum: General Help
---

### Post by nfox on 2008-09-07
Hey,

I don't know if this will help anyone and maybe this is the wrong venue to post this but it saved me several hours so if someone can benefit:

As many of you have had issues where Compiz will stop working one day, I too was in this situation. I learned that fusion-icon can actually get it all to work as normal. I had the "another window manager on :0" issue and still do. But when I run fusion-icon it still works and oddly the terminal output states the aforementioned error yet it still runs.

Then I found the compiz-check program 
[http://forlong.blogage.de/entries/pages/Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")
and while fusion-icon is running, everything checks out okay.



The point of my post is two-fold:

If your Compiz stopped working, does fusion-icon still work?
What is fusion-icon doing that "compiz --replace &" isn't?


I found this:
```
compiz --replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering
```
but simply typing this into the terminal does not work. As I said, fusion-icon's output states the same error yet still works perfectly.

Should this be reported as a bug or a fix? Why does this method work? Is anyone else experiencing this?

I would love to have Compiz more developed for end-users but the random "no worky"-ness of it is very irritating and my discovery can lead to a more stable version. Anyone with similar experience please let me know. Thanks

---

