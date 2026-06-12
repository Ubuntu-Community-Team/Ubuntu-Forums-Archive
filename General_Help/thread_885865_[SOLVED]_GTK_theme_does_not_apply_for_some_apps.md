---
title: "[SOLVED] GTK theme does not apply for some apps"
date: 2008-08-10
forum: General Help
---

### Post by Sain on 2008-08-10
Hi! I have customized my desktop a bit, and installed Shiftie Black theme. The theme seems to apply to everything, but there are some applications that do not apply the new look; most notably Synaptic.

I think it has something to do with applications that run as root...

Does anybody know how to fix this? This is not an issue just with Shiftie theme, I've tried various themes and some apply to synaptic, some don't.

---

### Post by TenPlus1 on 2008-08-10
This only happens because the theme itself is using user permissions instead of root permissions...

if you move the theme from ~/.themes to /usr/share/themes and select it from there, all programs will use it...

---

### Post by Sain on 2008-08-10
That did the trick. Thanks! 

It's kinda stupid that Gnome installs themes in user profile, and then forgets them when application is run as root, but at least this workaround works.

---

### Post by rainwalker on 2008-08-10
> **Sain said:**
> That did the trick. Thanks! 

It's kinda stupid that Gnome installs themes in user profile, and then forgets them when application is run as root, but at least this workaround works.

Part of the reason is so that it's obvious when apps are run as root, but it would be nice to add a simple checkbox somewhere that asks if you want the theme set for root applications as well

---

