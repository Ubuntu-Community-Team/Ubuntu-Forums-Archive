---
title: "Firefox profile gone after karmic upgrade"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by kdfox on 2009-11-08
I am using Swiftfox & reg Firefox.  

upgraded to karmic

profile is set at default in both.

how do i get my bookmarks/addons/themes/ back?

Help!

---

### Post by Scunizi on 2009-11-08
Open your file manager (nautilus).. hit CTRL+h to allow it to view hidden directories (they start with a ".") .. Look for .mozilla-<xomething>. You might see two different ones.  One will be your current settings, bookmarks etc., the other will be your old one from the previous version.  You'll be able to recover them there.

---

### Post by kdfox on 2009-11-08
thanks for pointing me in the right direction.  here's how i fixed it: navigated in nautilus to my .mozilla folder.  inside there was "firefox" and "firefox.3.0-replaced"  the first was the default profile, the second my old profile.  after backing up my old one and deleting the default i changed the name of "firefox.3.0-replaced" to "firefox"

problem solved.

thanks!

---

