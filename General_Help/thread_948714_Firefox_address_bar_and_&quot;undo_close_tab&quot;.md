---
title: "Firefox address bar and &quot;undo close tab&quot; problems"
date: 2008-10-15
forum: General Help
---

### Post by miko777 on 2008-10-15
I have Firefox 3 and Firefox 2 on my Hardy Herron. I mainly use FF2.

Recently I used FF3, then reverted to FF2, which meant I'd lost access to some of my extensions. As suggested elsewhere, I deleted the extensions. rdf etc files.

Now FF2 doesn't always load the content its saved tabs, even though it opens them, but it does come back when I close then re-open.

Also, when I open a new tab, the address of the last visible tab remains, rather than clearing, and the address bar has no focus.

When I undo a "close tab", a new tab opens, with an empty address bar and no content is loaded.

Is there a simple solution to this? I suspect it has something to do with user profiles, since a new user profile doesn't have this problem.

---

### Post by Altay_H on 2008-10-15
Perhaps the [Tab Mix Plus extension]("https://addons.mozilla.org/en-US/firefox/addon/1122") can help you. It has its own way of restoring deleted tabs and reloading past sessions. It's not a perfect solution, but it could work.

Personally, I'd suggest reinstalling Firefox. Chances are anything you've messed up would be fixed with a reinstall.

---

### Post by mssever on 2008-10-15
> **Altay_H said:**
> Perhaps the [Tab Mix Plus extension]("https://addons.mozilla.org/en-US/firefox/addon/1122") can help you.+1 to Tab Mix Plus. It's far better than what's built in to FF.
> Personally, I'd suggest reinstalling Firefox. Chances are anything you've messed up would be fixed with a reinstall.
Reinstalling Firefox probably won't help. The problem is most likely with your profile. Try renaming ~/.mozilla. Firefox should then create a new, pristine profile. If it works, then you've solved it. If not, then revert your profile to the way it was.

---

