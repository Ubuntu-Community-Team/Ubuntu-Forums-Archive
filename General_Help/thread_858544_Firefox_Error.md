---
title: "Firefox Error"
date: 2008-07-13
forum: General Help
---

### Post by DrTaylor on 2008-07-13
Lately when I open firefox it pops up with this:


ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:get_currentEngine()
9:updateDisplay()
10:init()
11:([object XULElement],7)


Which makes no sense to me at all. Anyone?

---

### Post by tech0007 on 2008-07-13
No clue actually. Did you install any plugin recently? You can try with a new profile to see if it works.

'mv ~/.mozilla ~/.mozilla.bak'
'firefox'

---

### Post by dodle on 2008-07-13
If it has to do with the extensions, you can try deleting the files named extensions.cache, extensions.ini, extensions.rdf, and there might be another called extensions.  They are located en ~/.mozilla/firefox/dl1afknk.default

---

### Post by baju on 2008-07-13
I've read another thread with the same error message.
The problem in that Thread was caused by doing dist-upgrade, which upgrade firefox from 3b5 to 3.0 while firefox was running and then starting a new firefox. They solved it by reinstalling firefox.

Did you do something like this?

---

### Post by UNOwen on 2008-07-13
I don't know if this will help but according to [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239013](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239013) and [http://support.mozilla.com/tiki-view_forum_thread.php?locale=nl&comments_parentId=66205&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?locale=nl&comments_parentId=66205&forumId=1) a simple system restart or re-login should eliminate the problem.

If that doesn't help you might consider posting to [http://forums.mozillazine.org/index.php](http://forums.mozillazine.org/index.php) to see if they have an answer.


UNOwen

EDIT: Forgot to mention that I suspect it has to do with the built in search engine not finding the proper files that it needs to operate correctly so is throwing that error out.

---

