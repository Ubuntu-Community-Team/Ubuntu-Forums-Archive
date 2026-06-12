---
title: "nautilus: disabling &quot;smart&quot; ordering on arrange by name"
date: 2008-11-18
forum: General Help
---

### Post by yacwroy on 2008-11-18
make 3 files:

aaa
aac
a-ab

list them in nautilus (or even console "ls") and you get

aaa
a-ab
aac

which is inconsistent with the old rule of "arrange by first letter - if it's the same move on to the next, etc"



another example is:

n1
n10
n2

nautilus (but not "ls" this time) lists these as

n1
n2
n10





It's obvious it's trying to be helpful, disregarding "-"s and sorting consecutive digits as single integers, but when browsing large source folders and random-letter-number filenames it's truly annoying.

Is there any way that I can get nautilus to go back to sorting files the basic consistent way, where it doesn't try to out-think me?

---

### Post by yacwroy on 2008-11-20
bumping this once -- is there somewhere better to put this?


I don't think submitting a bug report is the best way.


I could hack the source and recompile but it's damn annoying to have to lug my own version around when the source changes or I upgrade or switch PCs.

---

### Post by kaibob on 2008-11-20
> **yacwroy said:**
> ..Is there any way that I can get nautilus to go back to sorting files the basic consistent way, where it doesn't try to out-think me?

I can't be of direct help, but you may want to have a look at the following:

[http://bugzilla.gnome.org/show_bug.cgi?id=458707](http://bugzilla.gnome.org/show_bug.cgi?id=458707)

[http://ubuntuforums.org/showthread.php?t=68462](http://ubuntuforums.org/showthread.php?t=68462)

Apparently you need to change LC_COLLATE to a different locale if you want the sort to act differently. This seems like a simple issue, but the treatment of symbols, capitalization, customs in different countries make this much more complicated than you might expect.

---

