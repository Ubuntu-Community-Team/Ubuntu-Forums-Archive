---
title: "Firefox's &quot;Save Tabs&quot; feature keeps breaking."
date: 2008-08-02
forum: General Help
---

### Post by koffeinöverdos on 2008-08-02
I'm using Ubuntu Hardy Heron and Firefox's "Save Tabs" feature keeps breaking rather soon after I fix it. This never happened to me on Windows XP or Vista, so I figure this must be an Ubuntu problem. I tried installing over it multiple times, and the only way I managed to fix it was to delete the .mozilla folder in the home/%user% directory, then I started firefox and it gave me a fresh profile folder. That fixed it for about one day and then it broke again.

What happens is I tell it to remember my tabs for the next session. No matter what the tabs are, the next time I boot up firefox, all I get is one blank tab.

The problem simply reproduces, and deleting the .mozilla folder is the only thing that temporarily fixes it.

---

### Post by koffeinöverdos on 2008-08-03
bump 1 of 3

hopefully somebody knows what is going on, i can't find anyone else with this problem.

---

### Post by koffeinöverdos on 2008-08-04
somebody?

Is there any extra information I should provide?

---

### Post by mb_webguy on 2008-08-04
Try disabling all of your extensions and see if that helps any.

Also, did you upgrade from Gutsy, or do a clean install?  If you upgraded, did you have the Tab Mix Plus extension (or other extension with session-saving ability) in FF2 by any change?  The TMP settings can carry over into FF3 with an upgrade, and cause all sorts of problems (says a voice of experience).

Actually, my advice is to back up your bookmarks and passwords (there's a nice extension called Password Exporter for the latter), use Synaptic to completely remove Firefox (and make sure you delete the ~/.mozilla directory), and then reinstall.  That's what I had to do to fix the lingering configuration problems from FF2 after I upgraded to Hardy and FF3.

---

