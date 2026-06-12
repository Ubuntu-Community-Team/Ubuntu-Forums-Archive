---
title: "Firefox Problems"
date: 2008-08-12
forum: General Help
---

### Post by jdenicholls on 2008-08-12
When I went on holiday my Firefox 3 was working fine. However I did not quit Firefox before I shut down my PC and now when I load Firefox several features do not work. Firstly it does not open onto the homepage, just a blank screen, secondly all my bookmarks have gone and I can no longer add them. Lastly the address bar does not follow where I am going, although I can still use it to navigate to websites when I click hyperlinks the URL does not change accordingly. Because of this the forward and back buttons on the browser do not work, however the ones on my mouse do.

I've tried reinstalling it twice, I also tried installing Firefox 2 but the same problems occur.

---

### Post by kostkon on 2008-08-12
I believe your *Firefox* profile got corrupted. Try to create a new one and see if it works ok.

To do it, open a terminal and give
```
firefox --profilemanager
```
create a new profile and test it. I don't know if you can recover your bookmarks. *Firefox* makes regular backups of the bookmarks file, so go to the folder of your old profile and check if you can find the *bookmarks.html* file. Also, check in the *bookmarkbackups* folder. This is the folder where *Firefox* puts the bookmarks file backups. Your profile folders are in
```
~/.mozilla/firefox
```

From personal experience I can say that *Firefox* exits gracefully when you log out without closing it first. But it seems, this does not happen when you shutdown the PC. Or maybe it was just a random occurrence.

---

