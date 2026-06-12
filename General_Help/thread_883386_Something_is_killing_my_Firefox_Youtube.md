---
title: "Something is killing my Firefox Youtube"
date: 2008-08-07
forum: General Help
---

### Post by S3loth on 2008-08-07
[[IMG]http://img413.imageshack.us/img413/6642/youtubeto6.th.jpg[/IMG]](http://img413.imageshack.us/my.php?image=youtubeto6.jpg)
That's what I see now on every Youtube page. No Youtube Icon, the add to favorites is all messed up, and now the video is missing. I disabled all my Greasemonkey scripts, but nothing happened. Everything is fine in Opera, except the video, which is still missing there too. Anybody have ideas? Also, Ubuntu Forums is acting weird too. Its has no background.

EDIT: Now, its 100% okay in Opera, but still not in fx. Also, I noticed when a page starts to load in fx, it flashes the logo for a second, then it goes away.

---

### Post by werries on 2008-08-07
try backing up /home/user/.mozilla/firefox, and then delete it.

Sometimes it can fix things.

And i repeat, BACK IT UP! you'll want to save bookmarks at least.

---

### Post by S3loth on 2008-08-07
Nope. That didn't work.

---

### Post by ercferret18 on 2008-08-07
does this only happen with sites that use flash (like youtube)? if so, reinstall flash player.

sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

---

### Post by ercferret18 on 2008-08-07
does this only happen with sites that use flash (like youtube)? if so, reinstall flash player.

sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

---

### Post by tuxxy on 2008-08-07
Did you try refreshing the page, did it usuallly work or has it never worked, how did you install the flash codec?

---

### Post by mb_webguy on 2008-08-07
It could be that the Flash/PulseAudio incompatibility problem is causing Flash to fail, but isn't crashing Firefox.  If you haven't already done so, try "sudo apt-get install libflashsupport" and see if it helps any.

---

### Post by loligager on 2008-08-08
I KNOW THE SOLUTION
IT IS A CODEC PROBLEM
ok
search for this package in synaptics
keyword:ubuntu restricted extras
install it and restart firefox
it will work
It did for me...

---

