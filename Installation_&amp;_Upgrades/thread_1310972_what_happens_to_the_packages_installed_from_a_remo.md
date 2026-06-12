---
title: "what happens to the packages installed from a removed repo?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by gurth4ng on 2009-11-02
Let's say i've added a repository, and installed a few packages from it.

What happens to these packages, if i remove the repository from my system?

---

### Post by gradinaruvasile on 2009-11-02
Nothing. They will be there. 
But u cannot downgrade them easily to the versions (if they exist) that are in the official repos, only hunt them down one by one (As far as i know).
Generally be cautious about repos u add, check what packages they contain exactly (especially sound drivers (alsa, pulseaudio components), codecs or common system dependencies). I myself did an upgrade to libasound2 once and i wanted to revert it to the official versions... I had to remove and reinstall 100 or so packages (many of them gnome components)...

---

### Post by ikisham on 2009-11-02
Specially when upgrading (from one Ubuntu version to the next) it's wise to remove those packages.

---

