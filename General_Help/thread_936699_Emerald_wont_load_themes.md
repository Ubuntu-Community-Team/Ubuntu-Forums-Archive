---
title: "Emerald wont load themes"
date: 2008-10-03
forum: General Help
---

### Post by Vertoxic on 2008-10-03
Hey guys so i got my flash and desktop 3d working on my 64 bit ubuntu, i just installed emerald after importing themes when trying to apply them they wont work :( anyone know why?

---

### Post by Ryadt on 2008-10-03
Do```
emerald --replace
```

---

### Post by Vertoxic on 2008-10-03
> **Ryadt said:**
> Do```
emerald --replace
```
thank you that worked, i also have a question, i got my 3d cube working but everytime i flip it i can see like a bunch of lines while its flipping, it dont lag but seems like it how can i fix that?

specs
Intel duel core 2.0 
4gig ram 
ATI mobility 2600 hd 512 ddr3
ubuntu 8.04 64 bit

---

### Post by Vertoxic on 2008-10-03
> **Ryadt said:**
> Do```
emerald --replace
```

ok so that works and changes my theme, but soon as i exit my terminal i loose all the icons at the top of the bar, like the minimize and close icon

---

### Post by Ryadt on 2008-10-03
> **Vertoxic said:**
> ok so that works and changes my theme, but soon as i exit my terminal i loose all the icons at the top of the bar, like the minimize and close icon
Do Alt+f2 and then type in the command.
Also add it to session (System > Preferences > Sessions).

---

### Post by Vertoxic on 2008-10-03
> **Ryadt said:**
> Do Alt+f2 and then type in the command.
Also add it to session (System > Preferences > Sessions).
im sorry but what do i add in there?
and in the prefs > sessions

---

### Post by Ryadt on 2008-10-03
Under the Startup programs tab, click Add.
Name: Emerald
Command: emerald --replace
comment: anything

---

### Post by Vertoxic on 2008-10-03
> **Ryadt said:**
> Under the Startup programs tab, click Add.
Name: Emerald
Command: emerald --replace
comment: anything

thank u that worked, now do u have any idea how to fix the choppy 3d boxes when i switch em

---

### Post by Ryadt on 2008-10-03
No. Sorry.

---

### Post by qwertymodo on 2008-10-21
If you're on Hardy, rather than adding it to your session you should change the command in Compiz-Fusion.  I had this problem for awhile, but basically the act of actually applying the theme was the job of a package called Beryl, but now Beryl got rolled up with Compiz and now there's Compiz-Fusion.  First off, if you don't have it, install the compizconfig-settings-manager package.  Then click System>CompizConfig Settings Manager and click on Effects.  Then click on Window Decoration (the icon, not the checkbox, although the checkbox needs to be checked if it isn't already), and in the Command box, type

emerald --replace

Does the same thing as the workaround above, but at the same time it removes a possible conflict with Compiz-Fusion maybe fighting with Emerald when you launch emerald the way Ryadt suggested.  I don't know of any problem doing it his way, just why make it a startup item of its own when it's a setting in an existing item designed specifically to encompass all of that kind of stuff.

---

