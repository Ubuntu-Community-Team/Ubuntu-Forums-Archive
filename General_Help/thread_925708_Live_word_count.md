---
title: "Live word count?"
date: 2008-09-20
forum: General Help
---

### Post by yavez on 2008-09-20
Coming from the windows world there's only one real funciton I miss in Ubuntu/Linux word processors and that's Live Word Count. As you type the word count is updated live at the bottom of the window (Office 2007 also does this).  My app of choice on windows that utilizes this function is called *Atlantis Ocean Mind* (very minimal install, very fast and typewriter sounds too).  I have this running flawlessly in Wine, but I'd love to go 'native' and not have to rely on Wine at all.

So does anybody know if there's similar functionality in any Ubuntu/Linux word processors?  If so I'd love to know.:)

---

### Post by mb_webguy on 2008-09-20
You might want to take a look at [this link]("http://yawar.blogspot.com/2006/05/live-word-count-script-for.html").

---

### Post by mc4100 on 2008-09-20
OpenOffice.org Witer will list the number of words in:
Tools -> Word Count
File -> Properties -> Statistics

... but they're not live.

---

### Post by mb_webguy on 2008-09-20
The link I posted describes a script that puts a live word count at the bottom of the OpenOffice window.  That's the great thing about open source software.  If a program doesn't have a feature you want, just add it yourself.

---

### Post by yavez on 2008-09-20
> **mb_webguy said:**
> The link I posted describes a script that puts a live word count at the bottom of the OpenOffice window.  That's the great thing about open source software.  If a program doesn't have a feature you want, just add it yourself.


Thanks, taking a look at the script right now :)

EDIT:  Unfortunately the script uses a floating window, not integrated into the actual 'bottom bar' and it did nothing but crash OpenOffice :(

---

### Post by mb_webguy on 2008-09-21
Minor correction:  I just tried out the script (you need to save it as something like "live-word-count.py" in "~/.openoffice.org2/user/Scripts/python/"), and rather than putting the word count at the bottom of the page as I originally thought (and posted), it puts it in a small separate window that stays on top of the OOo editor window.  It's still pretty nifty, though.

---

### Post by yavez on 2008-09-21
Working now.. and it is actually quite good.  It has a percentage completed aspect to the bar that's very hand if you're working toward a wordcount.  Now if only we could get this integrated into the actual bottom bar, or one of the menus.

I wonder if it can be added to a menu bar as a customization?  I'll have a go at that now.

---

