---
title: "How to get Fx3 plugins to work with epiphany?"
date: 2008-08-03
forum: General Help
---

### Post by The Midnight Coder on 2008-08-03
I am using epiphany and want to get firefox3 plugins to work with it. Is there any way to do this??

---

### Post by The Midnight Coder on 2008-08-04
Err..........Anybody?

---

### Post by tlacuache on 2008-08-04
No, there is no way to do this. Sorry.

---

### Post by x1a4 on 2008-08-05
Hi,
Some FF extensions do actually work with Epiphany.  Create symlinks to the extensions you want in ~/.gnome2/epiphany/extensions/ and see which work and which don't.

---

### Post by The Midnight Coder on 2008-08-05
Problem is I dunnoe where the Fx3 plugins are stored :(

---

### Post by x1a4 on 2008-08-05
~/.mozilla/extensions/
/usr/share/mozilla/extensions/
/usr/lib/firefox-addons/extensions

---

### Post by snowpine on 2008-08-05
Can someone post a for-dummies (like me) guide to, for example, getting adblock plus to work in epiphany?

---

### Post by bingoUV on 2008-08-05
> **snowpine said:**
> Can someone post a for-dummies (like me) guide to, for example, getting adblock plus to work in epiphany?

Install epiphany-extensions from Add/Remove Software. In Tools->Extensions, enable the ad blocker. Now Tools->Adblock Editor and add your filters. Note that the Filterset.G filters are already present in it, so many commonly used filters are already defined.

EDIT: If you have filters defined in firefox, just export them to a file (say adblock.txt) from inside firefox. Now open adblock.txt and remove the first line, the header ([Adblock]). Now copy this text in ~/.gnome2/epiphany/extensions/data/adblock/blacklist and restart epiphany. The filters will be active in epiphany now.

---

### Post by The Midnight Coder on 2008-08-06
I went to those folders and they are empty but I know that I have plugins which I installed manually.

Side Note: Instead o trying to get epiphany to work with Fx3...is there ay way to lower the amount of memory that Fx uses? If not then help me get epiphany to work with the Fx extensions....

---

