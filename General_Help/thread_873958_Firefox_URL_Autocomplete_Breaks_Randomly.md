---
title: "Firefox URL Autocomplete Breaks Randomly"
date: 2008-07-29
forum: General Help
---

### Post by abbot on 2008-07-29
Hi All.

I was actually having this problem even before the firefox 3 release, but just now got around to posting something about it.  It seems to be a little glitch with firefox's autocomplete url history drop-down in the address bar.  It seems like it just randomly stops working at times until I restart firefox.  I use this feature a lot so it's kinda an annoyance.  

When it stops working it does this weird thing where I'll be typing a website and the autocomplete drop-down pops up for a split second a few times as I'm typing but doesn't stay up so I can select something.  It's super weird.  I haven't found any pattern that sets off this behavior.  It seems like it just randomly starts happening and doesn't fix it's self until I restart my browser.

Am I the only one who's had this problem?  Anything that I can do in about:config?  Any ideas?

Thanks.

---

### Post by y-lee on 2008-07-29
I've never had that problem nor am I sure what is causing it. but truthfully while I love Firefox it is a bit buggy and always has been. There are tho a couple of things you can try.

one is create start firefox in a terminal and see if it this behavior causes any post them here and maybe we can debug this problem.

Another is to create a new profile and see if this solves the problem. Sometimes Add ons or something else wrong in your default firefox profile causes firefox to act "strange". to create a new profile type the below in a terminal

```
firefox -P
```

And last there is an addon called [Autocomplete manager ]("http://www.ditii.com/2008/02/13/autocomplete-manager-firefox-addon/") which allows one to fine tune autocompletes features, it also claims to include "numerous fixes for location bar and Autocomplete-related bugs". it is maybe worth a try.

Note however I haven't used this add on because i can't stand either the autocomplete feature or the drop down box. The drop down box I have removed completely from my address bar and the autocomplete I have disabled. Just my preferences and the way i prefer firefox (well swiftweasel in my case) to act.

And oh btw ya might want to try swiftweasel as it is mostly the same as firefox just compiled for speed, it seems a little buggier than firefox to me but I like it and it is faster. Google it it is easy to find and even has a repo you can add. It stays a little behind firefox in version numbers but there is a swiftweasel based on FF3. Anyway it might not suffer from the same problem and it will import your bookmarks and addons and so on. 

Hmm also brings uo the fact you could try to reinstall firefox and see if that fixes the problem or uninstall it and download the firefox from mozilla and compile it from source code. either of those might also work.

---

