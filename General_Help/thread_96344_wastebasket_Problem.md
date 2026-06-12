---
title: "***wastebasket Problem***"
date: 2005-11-28
forum: General Help
---

### Post by kickstar on 2005-11-28
Ok I Admit That Im Embarresed To Ask This Question, How Do I Make A Wastebasket Icon On My Desktop Like In Windows (can I Say That Word?)

---

### Post by blkno1 on 2005-11-28
Not sure about ON your desktop.  But you can put one on your taskbar/s.  Just right-click on the taskbar --> Add to Panel... -->  And find the wastebasket applet.  Tada.  Instant trash.

-bk

---

### Post by Tiede on 2005-11-28
kickstar>Next time, do not put a bunch of * in front of your post, Ok. It can be very annoying. (Think of what would happen if everyone else was doing the same;) )
Now to make the Trash icon appear on the desktop, go to Applications->System Tools->Config Editor Gconf
In Gconf, go to Apps->Nautilus->Desktop, and check the trash-icon-visible ;)

---

### Post by kickstar on 2005-11-28
thankyou very much, its my first post so i will remember not to do that in future... sorry

thanx for all your help

---

### Post by melat0nin on 2006-02-26
My gconf-editor won't let me do that, it says the feature will be enabled in a future version? (i used apt-get and I've got the newest version installed).

I want an icon on the desktop because in my icon theme the wastebasket icon is too large for the panel and it looks daft.

Can anyone help?

---

### Post by Greg2 on 2006-02-26
[QUOTE=melat0nin]My gconf-editor won't let me do that, it says the feature will be enabled in a future version?[/QUOTE]
It should work for gconf-editor 2.12.0... which version do you have?

---

### Post by Ramses de Norre on 2006-02-26
Did you choose /apps/nautilus/desktop?
That should be changeable..

---

### Post by dunnerz on 2006-02-28
Hi,

Just found this thread from a search and wanted to say thanks as it solved what i was looking for (just putting the icon on the desktop through the config editor applet).

Cheers.

---

### Post by melat0nin on 2006-02-28
Yep I must have been looking in the wrong place.  Cheers :)

---

