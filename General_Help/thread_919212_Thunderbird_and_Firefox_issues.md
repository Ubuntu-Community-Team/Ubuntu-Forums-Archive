---
title: "Thunderbird and Firefox issues"
date: 2008-09-13
forum: General Help
---

### Post by awiggin on 2008-09-13
Hey all,

Total novice here.  I am having problems with Thunderbird and Firefox.

With Tbird, it closes immediately after opening, unless I open it from a root terminal.  If I do it from the start menu, no go.  

Earlier, I couldn't get it to start, even from a terminal and the output in the terminal said something about 

"Pango-WARNING: failed to create scaled cairo font, expect ugly output. the offending font is 'Tahoma 9.099609375' 

Segmentation fault"

_________

With FF, the fonts don't come up at all on some sites.  It think the problems might be related.

Any help?

Thanks,
awiggin

---

### Post by y-lee on 2008-09-13
I am not sure but you can try deleting the hidden folder .fonts in your home directory if you have one...I found a similar post and that worked for them :) Also looking around I found some post about this problem being related to ms fonts and perhaps a permission problem in /usr/share/fonts/truetype/ so you could try to completely purge the msttcorefonts package and if that works reinstall it if you need or like it and see if still works. Hopefully one of these will help and either way post back and let us know.

Good luck and peace :)

---

### Post by awiggin on 2008-09-13
I tried uninstalling msttcorefonts.  When I did that, I couldn't see hardly any text on any websites.  And it didn't solve the Thunderbird issue.

So I reinstalled msttcorefonts.  Now I can see text on some pages (not facebook).  

Still, the only way I can open Thunderbird is when I am in the root terminal.  If I try just to open it from the terminal window, I get the same response as above (Pango: WARNING...").

Please help.  I really like Thunderbird and I use it on my other machines.  And I need to fix the browser issue, too.

How do I delete that hidden file (.fonts)?  I couldn't find it.

Peace,
awiggin

---

### Post by awiggin on 2008-09-14
I have updated my fonts and things are better.

But I still can't see certain things.  I updated with tahoma, but the computer isn't recognizing anything that is in tahoma bold.

I put up another thread on this font topic.

Thanks,
awiggin

---

