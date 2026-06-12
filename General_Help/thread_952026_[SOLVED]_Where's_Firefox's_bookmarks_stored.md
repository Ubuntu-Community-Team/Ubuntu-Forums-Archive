---
title: "[SOLVED] Where's Firefox's bookmarks stored?"
date: 2008-10-18
forum: General Help
---

### Post by lsutiger on 2008-10-18
Today I was browsing through the file system and decided to open the bookmarks.html file under ~/.mozilla/firefox/<my profile>/. But I noticed that it does not reflect what bookmarks I actually have.

Does FF 3.X.X store the bookmarks somewhere else?
If not, what would be causing this?

---

### Post by scragar on 2008-10-18
Bookmarks are updated when firefox is closed, and not before, also, firefox keeps a number of different profiles as backups, you could try checking a different profile, see if that contains your bookmarks in a more up to date format.

---

### Post by kaibob on 2008-10-18
By default, Mozilla Suite/SeaMonkey and Firefox versions prior to 3.0 store bookmarks in the bookmarks.html file, located in the profile folder.... Starting in Firefox 3, bookmarks are stored in the places.sqlite file in the Firefox profile folder....

[http://kb.mozillazine.org/Browser.bookmarks.file](http://kb.mozillazine.org/Browser.bookmarks.file)

---

### Post by cyclobs on 2008-10-18
~/.mozilla/firefox/<some weird name thing>/bookmarks.html


yeah the bookmarks are saved in a html file in the .mozilla file which is located in your home directory

---

### Post by OrangeCrate on 2008-10-18
In the future, to make life a little more easy, you can go to:

Bookmarks > Organize Bookmarks > Import and Backup > Export HTML

Firefox will then store your bookmarks anywhere you want. I save the file to my Home folder, and then I drag and drop it along with the rest of my files on to a stick for backup.

And then, of course, you can use the import function to restore them to Firefox on a reinstall, or whatever.

Just try it, and you'll see what I mean.

---

### Post by fballem on 2008-10-18
> **OrangeCrate said:**
> In the future, to make life a little more easy, you can go to:

Bookmarks > Organize Bookmarks > Import and Backup > Export HTML

Firefox will then store your bookmarks anywhere you want. I save the file to my Home folder, and then I drag and drop it along with the rest of my files on to a stick for backup.

And then, of course, you can use the import function to restore them to Firefox on a reinstall, or whatever.

Just try it, and you'll see what I mean.

That's just too easy! Thanks so much.

---

### Post by lsutiger on 2008-10-19
Thanx for all of the input! I was a little worried about importing to a new system, but you have all answered my questions!
Thanx again!

---

