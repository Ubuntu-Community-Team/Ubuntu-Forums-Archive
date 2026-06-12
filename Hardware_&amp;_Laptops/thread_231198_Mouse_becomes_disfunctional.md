---
title: "Mouse becomes disfunctional"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by Neil Slote on 2006-08-07
I've just installed Dapper on my Latitude c840, and with a little tweaking gotten suspend to work.  Good work!

The problem I have is that after the system was running for a while, the mouse click stopped working outside of the current pane.  I had this problem when I had kanotix on the machine to, but not with the distro before that.

To be more precise, it appears that for the pointer, the current pane spans the whole desktop.  So, for example. if a web browser's rendering pane is the current pane, then the pointer appearance will change over links and clicking them will work.  But moving the pointer over other apps, or the scrollbar results in no change of pointer design.  If I click and drag to the left of the window, I can select text within the window.  If I click below it, the window scrolls down, if I click above it it scrolls up.  But if I right-click, everything behaves correctly.

This is expecially problematic in thunderbird, as the current pane is either the list of messages or the current message.  So either I can't change which message I am viewing, or I can't scroll the message.  I discovered that by switching virtual desktops and switching back again, the first pane I click on will then be the one which all future clicks appear to be part of.

Under Kanotix, this problem came and occasionally went away again appararently randomly.  Leaving the system could result in a change of state.  I haven't had Ubuntu running long enough to notice any patterns.

I've tried searching for someone else having the same problem, but it's hard to search for.  Where is the problem?  My best guess is that it has to be an X problem, but I'm not sure.

Any thoughts greatly appreciated.

Thanks!

---

