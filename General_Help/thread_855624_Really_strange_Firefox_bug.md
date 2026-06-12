---
title: "Really strange Firefox bug"
date: 2008-07-10
forum: General Help
---

### Post by Fixman on 2008-07-10
When I open a html file locally, the back and reload buttons don't show

[IMG]http://24.232.227.106/img/jotalota.png[/IMG]

If I then open another Firefox window, that window shows neither those buttons

[IMG]http://24.232.227.106/img/chau.png[/IMG]

However, if I close both windows and open a new firefox window, it shows normally, but opens the ubuntu greetings page besides of my home page.

[IMG]http://24.232.227.106/img/elenele.png[/IMG]

Can anybody help?

---

### Post by nikgare on 2008-07-10
For the missing buttons, maybe the 2nd part of this will help:
[http://support.mozilla.com/en-US/kb/Back+and+forward+or+other+toolbar+buttons+are+missing](http://support.mozilla.com/en-US/kb/Back+and+forward+or+other+toolbar+buttons+are+missing)

For the home page, what is you HomePage set to in the preferences dialogue box - it's possible to set multiple pages as your home page

---

### Post by Fixman on 2008-07-10
> **nikgare said:**
> For the missing buttons, maybe the 2nd part of this will help:
[http://support.mozilla.com/en-US/kb/Back+and+forward+or+other+toolbar+buttons+are+missing](http://support.mozilla.com/en-US/kb/Back+and+forward+or+other+toolbar+buttons+are+missing)

For the home page, what is you HomePage set to in the preferences dialogue box - it's possible to set multiple pages as your home page

It didn't, and my home page is only that - I know that because if I close the second window (the one with the ubuntu start) and restart firefox only wikipedia appears.

---

### Post by nikgare on 2008-07-11
It sounds like the your best bet would be to:

```
sudo aptitude remove --purge firefox
```

remove your ~/.mozilla/firefox directory and then reinstall firefox

---

### Post by joshsmith on 2008-07-11
the problem is that you have two different versions of firefox installed (check about>firefox in each, and the different shape and color icons)
you have an old ff2 copy that is set as the default file association for html files (so opens when you go to a local file)
and a proper ff3 installation which has the link on your panel (and in the applications menu)
note also that once one version of firefox is running, when you then try to run another instance (either by clikcing on the panel or double clicking a html file) firefox doesnt run firefox as it would normally, but instead just opens a new window in the currently running firefox sesssion (usually what you want). this explains why you have opened a local file, even clicking on the panel keeps the same type of window.
note also that if you run ff2, then run ff3 (ie by closing all instances then clikcing on the panel) it thinks you have just upgraded to ff3 so shows you the greetings page

basically, in the ff2 version you have hidden the icons, in the ff3 you havent

simple fix, remove you ff2 by looking the the package firefox-2.0 in synaptic, or change the default application for html files (right click > properties) and just use the better ff3 from now on

---

