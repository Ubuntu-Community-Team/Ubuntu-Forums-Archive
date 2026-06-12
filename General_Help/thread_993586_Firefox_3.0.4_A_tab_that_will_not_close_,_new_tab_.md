---
title: "Firefox 3.0.4 A tab that will not close , new tab button gone..."
date: 2008-11-25
forum: General Help
---

### Post by jason.b.c on 2008-11-25
Ubuntu 8.10 with firefox 3.0.4....  , i have a tab that simply WILL NOT CLOSE OUT  and has a rotating thingy in it showing that it is constantly loading , also - my "open new tab"  button keeps disappearing everytime i restart / open firefox...

<beep beep>:mad::mad::mad::x

---

### Post by jason.b.c on 2008-11-25
this tab has seriously been loading for an hour now....

---

### Post by kanikilu on 2008-11-26
Regarding the tab that doesn't stop loading, do the contents of the page ever show up? If so, I think I've seen that before, and it was a problem with the site, I think it was Digg or Slashdot or one of those during the Firefox 3 beta.

Anyways, there may not be anything you can do about it if it's a problem with the site. If you can post the URL, maybe someone can reproduce the problem.

As for the new tab button disappearing, I'm not really sure there...maybe a problem with your profile. Try creating a new profile with:

```
firefox -P
```

Note the capital "P". Kill any instances of FF before doing this. Then just create a new profile.

You could also move/rename (don't delete) your ~/.mozilla folder and let Firefox recreate it.

Beyond that, if that doesn't work, I don't really know. Maybe someone else will have some suggestions...

*EDIT* - This document may be relevant: [http://kb.mozillazine.org/Bookmarks_history_and_toolbar_buttons_not_working_-_Firefox](http://kb.mozillazine.org/Bookmarks_history_and_toolbar_buttons_not_working_-_Firefox)

---

### Post by jason.b.c on 2008-12-01
> **kanikilu said:**
> Regarding the tab that doesn't stop loading, do the contents of the page ever show up? 

oh yeah , it'll show up just fine - but if i want to close the tab for any reason it simply will not...and the constant loading is (i think) slowing firefox to a crawl....

---

### Post by jason.b.c on 2008-12-02
> **kanikilu said:**
> 


As for the new tab button disappearing, I'm not really sure there...maybe a problem with your profile. Try creating a new profile with:

```
firefox -P
```



You could **_also move/rename (don't delete) your ~/.mozilla folder and let Firefox recreate it._**



if i do that , does that mean that my FF will start from a fresh state ??? and that i will be losing all of my extentions and skins i have installed...?

---

### Post by jason.b.c on 2008-12-04
so no-one else has any ideas or answers to my last question....?

---

### Post by jason.b.c on 2008-12-04
BUMP

still having trouble...

---

### Post by dannytatom on 2008-12-04
I have no clue why your tabs are acting crazy, but have you tried reinstalling firefox?  If you don't want to lose all your extensions and themes, just open text editor and write 'em all down and you can reinstall when you get it working.

---

### Post by magmon on 2008-12-04
Hmm, Ive had trouble with FF remembering my settings for add ons and other shtuff if firefox doesnt close properly. Try putting the button out, closing firefox, then reopening.

---

### Post by vandorjw on 2008-12-04
Have you tried...

running firefox,

then opening up a terminal and typing, killall firefox

firefox will abrubtly close, and next time it starts, it will tell you

"firefox did not close properly, would you like to reload all your open tabs?" ~ or something like that.

Choose, open new session.

Problem should be solved.

Cheers - cc7

---

### Post by jason.b.c on 2008-12-05
> **cc7gir said:**
> Have you tried...

running firefox,

then opening up a terminal and typing, killall firefox

firefox will abrubtly close, and next time it starts, it will tell you

"firefox did not close properly, would you like to reload all your open tabs?" ~ or something like that.

Choose, open new session.

Problem should be solved.

Cheers - cc7


i'll try just that , thank you:p

---

### Post by Cresho on 2008-12-05
first close firefox

open up nautilus and hit view and "show all files".  right click on .mozilla and create archive.  delete folder ./mozilla

open firefox and see if this worked.

if it didnt, close firefox, then delete ./mozilla ad then extract the backup tar file into the here and should restore your settings.

I do this to my pc so there should be no problems.  As a matter of fact, i just did it and its restored.

---

### Post by Innuendo108 on 2011-03-13
I have the same problem (Ubuntu 10.10, Firefox 3.6.15), but not every time I open firefox window. I've noticed, that bug appears when I first time open firefox window.

I suspect my theme addon - eFirefox (firefox elementary theme)

---

