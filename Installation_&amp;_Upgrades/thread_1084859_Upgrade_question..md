---
title: "Upgrade question."
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by HammerOfDoubt on 2009-03-02
Maybe this is a stupid question, but when updating to a new version of Ubuntu (like 8.10 to 9.04) is this a complete reinstall where I have to back up my data and redo all my settings or does it just sort of work in the background?

---

### Post by oldos2er on 2009-03-02
You should backup your data in any case. The upgrade is just that, not a complete reinstallation.

---

### Post by HammerOfDoubt on 2009-03-02
Oh I'm backed up. I just needed to know what to expect. Thanks for the info.

---

### Post by Pumalite on 2009-03-02
Don't forget to remove all third parties from your /etc/apt/sources.list, including Medibuntu and it's folder if you have it.
Id you had a separate /home; it would be better a clean install.

---

### Post by HammerOfDoubt on 2009-03-02
> **Pumalite said:**
> Id you had a separate /home; it would be better a clean install.

Elaborate please.

---

### Post by Scubdup on 2009-03-03
> **Pumalite said:**
> Don't forget to remove all third parties from your /etc/apt/sources.list, including Medibuntu and it's folder if you have it.Can you explain to this newbie why this is important and how to do it? Sorry to be a pain but I know I added Medibuntu when working through an excellent Audio/Visual tutorial, and now I don't know how to check what apt sources I have, how to remove them (and presumably put them back later) and why it's necessary.

---

### Post by Pumalite on 2009-03-03
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by HammerOfDoubt on 2009-03-04
> **Pumalite said:**
> [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I can figure out how to do it, I just wanted to know the "why" behind removing third party sources.

---

### Post by markusf21 on 2009-03-04
> **HammerOfDoubt said:**
> I can figure out how to do it, I just wanted to know the "why" behind removing third party sources.

You do this because most of the third party repos are version specific. So you disable them until you can get them updated to your new version.

---

