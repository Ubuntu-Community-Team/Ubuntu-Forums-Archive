---
title: "[SOLVED] Intrepid 8.10 minor problems"
date: 2008-10-30
forum: General Help
---

### Post by lariosa42 on 2008-10-30
I just installed Intrepid 8.10 and I'm loving it so far.  I have a few minor problems though.

1) Google Toolbar in shows up in Firefox 3.0.3, but it has no search bar in the toolbar.  The gmail, etc. buttons show up, but no search bar.  View-->Toolbars doesn't seem to help either.

2) Google Earth now looks even worse than it did in Hardy (running Google Earth version 4.2.0205.5730.  Hardy didn't like GE 4.3 with my Intel 943/940GM video card.)

Any suggestions?

EDIT:

3) Firefox also does not save the items I place in the main menu (such as the "new tab" button).  I tried to chown, but this did not seem to fix it.

---

### Post by lariosa42 on 2008-11-01
Comment #6 on this thread fixed problems (1) and (3):

[http://ubuntuforums.org/showthread.php?t=964055](http://ubuntuforums.org/showthread.php?t=964055)

Close all instances of firefox and then run

```

firefox -safe-mode

```

Basically you just need to fully disable the Firefox Ubuntu add-on using Firefox's safe-mode.  (See the link for more details.)

---

### Post by Jim Danner on 2008-11-01
That's a link to *this* thread. Where did you find that Firefox solution?

---

### Post by Braedley on 2008-11-02
> **lariosa42 said:**
> Comment #6 on this thread fixed problems (1) and (3):


Close all instances of firefox down and then run

[http://ubuntuforums.org/showthread.php?t=964441](http://ubuntuforums.org/showthread.php?t=964441)

Basically you just need to fully disable the Firefox Ubuntu add-on using Firefox's safe-mode.

That's all fine and dandy, if you had linked to the proper thread.  I have the same problem and would really like to fix it.

---

### Post by lariosa42 on 2008-11-02
My apologies, I must have been very tired when I wrote that.  The posted is edited above and should now be correct.

---

