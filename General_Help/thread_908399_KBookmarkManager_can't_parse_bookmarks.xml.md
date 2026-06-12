---
title: "KBookmarkManager can't parse bookmarks.xml"
date: 2008-09-02
forum: General Help
---

### Post by Heliomance on 2008-09-02
Okay, backstory. Dolphin was acting up in a couple of small ways for me, so I apt-get purged/installed it. At which point it started to act up more. Every time I close a dolphin window, I get this error message:
```
Unable to save bookmarks in /home/thomas/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.
```
and if I try to start up dolphin from console, the console readout does this:
```
thomas@t-laptop:~$ dolphin
d3lphin: WARNING: KBookmarkManager::parse : can't parse /home/thomas/.kde/share/apps/d3lphin/bookmarks.xml
ASSERT: "hasParent()" in /build/buildd/kdelibs-3.5.9/./kio/bookmarks/kbookmark.cc (332)
ASSERT: "hasParent()" in /build/buildd/kdelibs-3.5.9/./kio/bookmarks/kbookmark.cc (332)
ASSERT: "hasParent()" in /build/buildd/kdelibs-3.5.9/./kio/bookmarks/kbookmark.cc (332)
ASSERT: "hasParent()" in /build/buildd/kdelibs-3.5.9/./kio/bookmarks/kbookmark.cc (332)
ASSERT: "hasParent()" in /build/buildd/kdelibs-3.5.9/./kio/bookmarks/kbookmark.cc (332)
ASSERT: "hasParent()" in /build/buildd/kdelibs-3.5.9/./kio/bookmarks/kbookmark.cc (332)
ASSERT: "hasParent()" in /build/buildd/kdelibs-3.5.9/./kio/bookmarks/kbookmark.cc (332)

```
What's going on, and how do I fix it?

---

### Post by Heliomance on 2008-09-02
Hum. This got to the fourth page with no replies. Does no-one know how to solve this?

---

### Post by Denestria on 2008-09-02
You probably ran dolphin as root at some point causing it to save the bookmark file with root permissions.  Try this:
```

sudo chown yourusername:yourusername ~/.kde/share/apps/d3lphin/bookmarks.xml

```

---

### Post by Heliomance on 2008-09-02
Well that half worked. It no longer puts up an error message when I close a window, but the konsole still shouts errors when I run from there.

---

### Post by Denestria on 2008-09-02
I've never seen the terminal errors you are getting and after a bit of searching I couldn't find anything about it either.  I would move bookmarks.xml to a safe place and then start dolphin.  It will create a new bookmarks.xml file and hopefully get rid of your error.  A custom bookmark you added may be causing a problem.

---

