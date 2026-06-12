---
title: "[SOLVED] Firefox"
date: 2008-07-28
forum: General Help
---

### Post by elkade on 2008-07-28
When opening firefox, and attempting to open a site, this popped up.  I have a screenshot attached.

I uninstalled firefox and then reinstalled.  When trying to open up a site, I get the same pop up.

Really don't know what to do and don't understand the pop up.

Thanks for the help in advance.

Larry  :confused:

---

### Post by Nikitas350 on 2008-07-28
Looks like a bug ([https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/251875](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/251875)). Try installing opera if you cannot solve the problem....

---

### Post by UbuntuNerd on 2008-07-28
you can also try installing Firefox2 from synaptic package manager I know FF3 is a little buggy still

---

### Post by Ryadt on 2008-07-28
> **elkade said:**
> When opening firefox, and attempting to open a site, this popped up.  I have a screenshot attached.

I uninstalled firefox and then reinstalled.  When trying to open up a site, I get the same pop up.

Really don't know what to do and don't understand the pop up.

Thanks for the help in advance.

Larry  :confused:

Can you give a link as to which website gives this error.

---

### Post by sailor2001 on 2008-07-28
you have downloads pending...see blue recycle arrows at top

---

### Post by aysiu on 2008-07-28
Can you close Firefox, and paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
firefox -safe-mode
``` If that doesn't solve the problem, then something is truly wrong with your Firefox installation.

---

### Post by silkstone on 2008-07-28
I would start by disabling all add-ons. If that solves it, enable them one at a time until you find the one that causes it.

If that doesn't work, something in your configuration may be corrupted. Reinstalling won't necessarily solve this. You may have to uninstall FF, then delete ~/.mozilla/firefox/xyz.default (where xyz can be anything). Then reinstall FF.

Unfortunately that will lose all your add-ons, configuration and bookmarks (unless you have Foxmarks installed, in which case you can reimport them).

---

### Post by aysiu on 2008-07-28
> **silkstone said:**
> I would start by disabling all add-ons. If that solves it, enable them one at a time until you find the one that causes it.

If that doesn't work, something in your configuration may be corrupted. Reinstalling won't necessarily solve this. You may have to uninstall FF, then delete ~/.mozilla/firefox/xyz.default (where xyz can be anything). Then reinstall FF.

Unfortunately that will lose all your add-ons, configuration and bookmarks (unless you have Foxmarks installed, in which case you can reimport them).
The shortcut way to all of what you just said is *firefox -safe-mode*, which temporarily disables all add-ons and allows you a way to permanently disable them if that's what fixes the problem.

---

### Post by silkstone on 2008-07-28
Thanks for that aysiu - I didn't know that's what safe-mode did.

---

