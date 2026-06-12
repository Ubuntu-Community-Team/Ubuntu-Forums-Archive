---
title: "[SOLVED] lost all types of bookmarks system wide?"
date: 2008-11-08
forum: General Help
---

### Post by Hoaxe on 2008-11-08
hi, this looks like a weird one, so props to anyone who knows what's going on.

i was trying to use a movie editing tool on a file that was clearly too large for my laptop. It either made a forced shutdown of my system or it kept playing this one short string of sound over and over again as a result of the movie editor crashing forcing me to reboot to get rid of it.

i tried so many many movie editors today so many times i can't tell which scenario caused this. the point is:

now my firefox bookmarks are gone, my quicklinks are gone, and i can't even use the quick search function. so when i use the google quick search and press enter or click on the magnifier -- nothing happens.

what' ever creepier is my nautlius bookmarks are gone too!! WHY? i don't get it. the nautlius bookmarks are no big deal, but i would reallllllllyyyyy like my firefox bookmarks and quick links and search bars back and working. I noticed there was a bookmarks backup folder in ~.mozilla/*.default/

how do i use those? they are .json extensions...


i am removing all video editing software now...
i learned my lesson...

EDIT: i tried going to bookmarks>organize bookmarks> and import past backups and i got an error: unable to process backup file... can i open it in some way and get the files from inside and create an html file to import from manually?

also, nothing else is effected, passwords and history was kept on firefox and nautilus still works great - it's the bookmarks that suffered.

---

### Post by Hoaxe on 2008-11-08
i just noticed something

not only can i not restor my bookmarks through the bookmark manager, but i can not add bookmarks either. nor can i export bookmarks as .html pages using the bookmark manager.

this is also the case with nautlius, as soon as i add a bookmark, it disappears.  damn it, this is getting serious....

---

### Post by Hoaxe on 2008-11-08
new information:
i get the following errors when trying to open ANY application through the terminal: (in this case, firefox is the app i am using)

```

(firefox:6804): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.

```

also, the following 2 errors appear on firebug for every site i visit:
```

this.bookmarks is undefined
file:///usr/lib/xulrunner-1.9.0.3/modules/utils.js
Line 884

```

and the second:
```

[Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: file:///usr/lib/xulrunner-1.9.0.3/components/nsLivemarkService.js :: anonymous :: line 500"  data: no]
file:///usr/lib/xulrunner-1.9.0.3/components/nsLivemarkService.js
Line 500

```

this is starting to look serious. i want this fixed...

EDIT:
i'll stop making new posts, so here:

i was looking at this bug here: [https://launchpad.net/ubuntu/+source/gksu/+bug/23917](https://launchpad.net/ubuntu/+source/gksu/+bug/23917)

and i noticed i lost my encryption keys. this sucks because i have encrypted files that i use from time to time.


EDIT2:
I can not go backwards or forwards through pages in firefox anylonger because firefox is not keeping track of my browsing history anymore.

I also can not download files to the desktop. or anywhere else for that matter. the save as prompt simply does not appear.

---

### Post by ykcirt on 2008-11-08
I've experienced something like this while I was using a few too many apps simultaneously. Firefox lost my bookmarks and I couldn't make new ones. Don't know about Nautilus though. Strangely enough they all reappeared after I rebooted. Have you tried that?

---

### Post by Hoaxe on 2008-11-08
> **ykcirt said:**
> I've experienced something like this while I was using a few too many apps simultaneously. Firefox lost my bookmarks and I couldn't make new ones. Don't know about Nautilus though. Strangely enough they all reappeared after I rebooted. Have you tried that?

yes, several times. my full bug report/comment is here: 
[https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/23917/comments/25](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/23917/comments/25)

k thx

---

### Post by Hoaxe on 2008-11-09
somehow this error has fixed itself. I had turned the laptop off for an hour and a half and then turned it back on but this time logging onto another user on my machine (i have different accounts for different peope)

The other accounts were not affected by this problem and after logging onto my account, neither was i.

although i don't know what this "solution" did exactly, it fixed my problem and that is all i really care about.

---

