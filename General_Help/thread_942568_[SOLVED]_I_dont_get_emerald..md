---
title: "[SOLVED] I dont get emerald."
date: 2008-10-09
forum: General Help
---

### Post by semitone36 on 2008-10-09
Ive tried my hardest, but seriously, what the heck is this?  

I can download emerald themes, tweak even the tiniest details, make the most perfect theme I have ever seen, and that's it.  No apply button, no HOWTOs anywhere that I can find. I can not for the life of me figure out how to get my theme from emerald to my desktop. Even the Emerald wiki was no help!

Ive enabled "Windows decorations" in compiz.  Ive built themes before using "Appearances" under System.  But I seriously cant figure emerald out... Can anyone help me out or direct me to a HOWTO thats been eluding me?

---

### Post by sub2007 on 2008-10-09
You have to install Emerald as well as Compiz. Then you can open the theme manager to replace themes (should be located in System somewhere, I don't use GNOME so can't tell you where it is).

---

### Post by semitone36 on 2008-10-09
Yup I have emerald and I have compiz.  I am very familiar with compiz and I have a general understanding of how to manipulate themes using emerald.  My problem is that I **can not** apply themes created using emerald to my desktop.

---

### Post by sub2007 on 2008-10-09
Make sure emerald is running by pressing ALT+F2 and entering 

```
emerald --replace
```

Then just double click on the theme you want to use in Emerald theme manager.

---

### Post by semitone36 on 2008-10-09
Ah. That would probably be it then.  Im not on my comp ATM but ill give it a try later and see if that works.

---

### Post by sub2007 on 2008-10-09
OK, well if that is the problem then you can set Emerald to autostart. You can do that in the Compiz control panel > Window Decorations and then in the "command" line put 

```
emerald --replace
```

You can also install Fusion Icon (which also simplifies disabling Compiz) and set the window decorator to Emerald in there.

---

### Post by semitone36 on 2008-10-09
hmmmm.  Well thank you sub2007 that got emerald to work.  But for some reason my frames are gone... as in nothing borders any of my windows.  Ill have to look into that tomorrow though.  No time now.

---

### Post by sub2007 on 2008-10-10
You can increase the thickness of the frame borders in Emerald settings. Some themes are set without any window borders, in which case you'll need to get a theme that does have them.

---

### Post by semitone36 on 2008-10-13
Aha. The reason my themes were disappearing was because I was running emerald --replace through my terminal.  The theme would run so long as my terminal was open but if I closed it my themes would disappear.  

This was solved though as you said by putting emerald --replace into the command line for windows decorations.  Thank you so much for your help sub2007!:)

---

