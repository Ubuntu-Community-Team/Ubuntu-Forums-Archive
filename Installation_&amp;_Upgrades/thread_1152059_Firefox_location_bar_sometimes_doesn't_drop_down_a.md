---
title: "Firefox location bar sometimes doesn't drop down after jaunty upgrade"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by rfugger on 2009-05-07
Wondering if anyone else has this problem, or can suggest a solution...

Since upgrading to jaunty, the firefox location-suggestion list doesn't always drop down when I start typing something in the location bar.  Actually, it always drops down, but sometimes flickers just very briefly and disappears.  If I move to another desktop and then come back and start typing again, it reappears (not right away, only after I type something new).

Maybe this has something to do with compiz (I have desktop effects enabled)?

Thanks,
Ryan

---

### Post by Hyperqbe on 2009-08-18
I have this problem, both in Firefox 3.0 and 3.5 from the Ubuntu repository.  I haven't figured out how to solve it, but an annoying workaround is to create a new Firefox window when you have the problem.  Somehow creating the new window causes the dropdown bar to work again, for a limited amount of time.  If I really want to use the awesomebar features, I hit Ctrl-N, Ctrl-W (new window, close window), and then I'm able to use the awesomebar.

Let me know if you find a solution to this annoying problem! (I haven't tried, but I bet that disabling desktop effects will solve it.)

---

### Post by burnfromwithin on 2009-08-24
I am having the same problem.  I've noticed that this most often happens after I bring my computer back from sleep mode or after the screen turns off (power-saving setting) and I move the mouse again.

If I close and re-start Firefox, it is fixed, but not having the location bar auto-complete the entries can get annoying.

I will try to execute test cases to determine exactly when it happens and what will bring it back.

Laptop: HP nw8240

---

### Post by larytet on 2009-10-08
same problem here. I have a couple of plugins installed. I tried to disable them and still nothing

---

### Post by larytet on 2009-10-10
Bringing new window (Ctrl-N) and closing the window (Ctrl-W) solves the problem for some time

---

### Post by tonyfrost on 2009-10-25
I have htis same problem as well. ctrl-n does fix it, but it's not the best solution ever. Has anyone else encountered this? My system a latitude d830 with an intel graphics chipset and compiz is running. Thanks!

---

### Post by Xirev on 2010-01-22
I'm using Firefox 3.0, and I get around this problem by pressing SHIFT+TAB, ENTER, then ESCAPE. Pressing CTRL+N then CTRL+W like it's been suggested requires less key pressing, but is much slower performance wise. Hope it helps, and if anyone knows a real solution to the problem please let us know.

---

### Post by zeus77 on 2010-06-01
**Other threads discussing this issue:**
[INDENT][http://ubuntuforums.org/showthread.php?t=1261872](http://ubuntuforums.org/showthread.php?t=1261872)
[http://ubuntuforums.org/showthread.php?t=1308509](http://ubuntuforums.org/showthread.php?t=1308509)
[http://ubuntuforums.org/showthread.php?t=1319054](http://ubuntuforums.org/showthread.php?t=1319054)
[http://ubuntuforums.org/showthread.php?t=1339466](http://ubuntuforums.org/showthread.php?t=1339466)
[http://ubuntuforums.org/showthread.php?t=1374165](http://ubuntuforums.org/showthread.php?t=1374165)
[http://ubuntuforums.org/showthread.php?t=1413575](http://ubuntuforums.org/showthread.php?t=1413575)
[http://ubuntuforums.org/showthread.php?t=1417212](http://ubuntuforums.org/showthread.php?t=1417212)
[http://ubuntuforums.org/showthread.php?t=1489786](http://ubuntuforums.org/showthread.php?t=1489786)[/INDENT]


**Bug reports about this issue:**
[INDENT][https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/428703](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/428703)
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/438868](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/438868)
[https://bugzilla.mozilla.org/show_bug.cgi?id=507269](https://bugzilla.mozilla.org/show_bug.cgi?id=507269)[/INDENT]


**Current "best" fix:**
[INDENT]Minimize the firefox window, then restore it.  Or, press Alt-Tab twice.[/INDENT]


**How to let the developers know that you are experiencing this bug:**
[LIST=1]
[*][Create a launchpad account]("https://login.launchpad.net/+new_account") if you don't have one already.
[*]Click [here]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/428703/+affectsmetoo") and [here]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/438868/+affectsmetoo") to indicate that these bugs affect you, too (only if they truly do, of course!).
[/LIST]


May this bug be fixed one day soon...
zeus77

---

### Post by Xirev on 2010-09-03
Gosh I hate this bug. I have to deal with it at least a dozen time a day. I can't believe something so intrusive is still left unsolved and isn't dealt with yet.

---

