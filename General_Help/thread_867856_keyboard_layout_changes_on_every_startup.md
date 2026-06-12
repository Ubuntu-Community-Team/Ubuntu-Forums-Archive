---
title: "keyboard layout changes on every startup"
date: 2008-07-23
forum: General Help
---

### Post by killerwhale65 on 2008-07-23
hi,

Whenever i startup lately, i notice my keyboard layout is messed up. When i go into the keyboard configuration, select layout, then it is listed corectly, however the keys i press come out completely wrong. I have then to add a new layout (the same as the one that is already listed), and then it works again.

What could be wrong?

thanks!

Matt

---

### Post by Archimedes0212 on 2008-07-23
hi - danwood76 just solved this problem for me yesterday in a thread I created.

What you need to do is go into /etc/X11/xorg.conf

Locate the "keyboard" section.  There is going to be a layout option and a variant option.  Change those two values to whatever keyboard layout you have.  For me i needed "us" and "basic" respectively.  The next time you restart it should work perfectly fine.

Hope this helps



P.S. - Good name.  :-P  - Matt

---

### Post by killerwhale65 on 2008-07-26
hello,

I have tried this, and it is better, but there are still a few keys wrong. I still have to change the keyboard layout on startup. I have in xorg.conf:

	Option		"XkbLayout"	"be"
	Option		"XkbVariant"	"default"

Before, there used to be something totally different, so i do not understand why there is an option in the kayboard manager to change the layout, if the xorg file is not updated?

Anyway it is still not OK, so what other values should i change in xorg.conf? In the keyboard layout window i set it to Belgium Default.

regards,

Matt

---

### Post by killerwhale65 on 2008-07-27
Hello,

Please is there anyone who can tell me how i get the correct keyboard layout from startup? This used to work fine but all of a sudden it started giving me a keyboard layout on startup that was different from the one i shut down with.

thanks!

Matt

---

### Post by yussri on 2008-07-30
> **killerwhale65 said:**
> Hello,

Please is there anyone who can tell me how i get the correct keyboard layout from startup? This used to work fine but all of a sudden it started giving me a keyboard layout on startup that was different from the one i shut down with.

thanks!

Matt

Same thing here I have to setup Keyboard layouts whenever I restart , this is really very annoying  , is it herdy heron specific cause it started recently after one of herdy  updates

---

### Post by orduek on 2009-10-28
Same problem here, after upgrading to Karmic.

---

### Post by orduek on 2009-11-01
anyone?

---

### Post by EarlGrey on 2009-12-13
Same problem here - no idea what to do with it, I hope it gets fixed - very anoiyng.

---

### Post by zidarsk8 on 2010-02-25
i have the same problem on my netbook ...

i also have carmic on my desktop and leptop computers, but i just see the problems on this small netbook.

can anyone help (i have ubuntu netbook remix).

---

### Post by kresimir-vk on 2010-04-28
i have same problem ...

---

