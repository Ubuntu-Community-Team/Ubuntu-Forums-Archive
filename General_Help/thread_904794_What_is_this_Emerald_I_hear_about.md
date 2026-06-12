---
title: "What is this Emerald I hear about"
date: 2008-08-29
forum: General Help
---

### Post by stat30fbliss on 2008-08-29
I have seen the program/word emerald thrown around in a few posts in tandem with Compiz, and I am curious:

What is it?

Do I already Have it?

Thanks

:guitar:

---

### Post by Crafty Kisses on 2008-08-29
Emerald is a 3D window decorator for compositing window managers such as Compiz and Beryl. > [http://swik.net/emerald](http://swik.net/emerald)

---

### Post by mb_webguy on 2008-08-29
Simple version: it makes yer winders look purty.  :biggrin:

Emerald lets you use [themes]("http://www.compiz-themes.org/index.php?xcontentmode=103") for your windows that use blending and transparency.  I personally like the Vista-Q version of [Vista-Linux]("http://www.compiz-themes.org/content/show.php/Vista-Linux?content=42875").

---

### Post by Crafty Kisses on 2008-08-29
There's a lot of great themes/examples over at GnomeLook too.

---

### Post by mocoloco on 2008-08-29
I've never been clear so if someone can elaborate, without emerald compiz just uses your GTK window decoration, is that right?  And you can still use transparency and what not.  So what are the advantages of emerald?

---

### Post by mb_webguy on 2008-08-29
> **mocoloco said:**
> I've never been clear so if someone can elaborate, without emerald compiz just uses your GTK window decoration, is that right?  And you can still use transparency and what not.  So what are the advantages of emerald?

Gnome by default uses Metacity, which does not AFAIK support true transparency.  I believe that Emerald is currently the only window decorator that supports transparent compositing.

Also, Emerald is much more customizable and more easily customizable than Gnome's default window decorator.

---

### Post by enzodad on 2008-08-29
nice post installed emerald my self but im new at this so i wouldent know where to get themes and install them

---

### Post by SunnyRabbiera on 2008-08-29
> **enzodad said:**
> nice post installed emerald my self but im new at this so i wouldent know where to get themes and install them

well doing both should be very easy
Gnome look should have what you need in themes:
[http://www.gnome-look.org/index.php?xcontentmode=103](http://www.gnome-look.org/index.php?xcontentmode=103)
[http://www.gnome-look.org/index.php?xcontentmode=102](http://www.gnome-look.org/index.php?xcontentmode=102)

both have a fair share of emerald themes.

as for the theme installer, its under system> preferences listed as emerald theme manager
in that there is a button marked "import"
and figuring out the app itself should be easy enough.

---

### Post by enzodad on 2008-08-29
K thanks Ill give it a shot.. i always been to scared to try even splash creens. OOO anyone can help me figure how to get/install the hand print one i love it but to complex for me

---

### Post by enzodad on 2008-08-29
well found 1 theme sofar but cant get it to apply.

---

### Post by enzodad on 2008-08-29
I cant apply or use themes when i import them i have no respertories tab

---

### Post by mb_webguy on 2008-08-29
If you haven't installed the compizconfig-settings-manager package, do so by typing "sudo apt-get install compizconfig-settings-manager" in the terminal.  Now go System->Preferences->Advanced Desktop Effects Settings, and go to the Window Decoration plugin.  In the box labeled "command", replace "/usr/bin/compiz-decorator" with "/usr/bin/emerald --replace".  Now exit and restart X with Ctrl-Alt-Backspace.  Now go to System->Preferences->Emerald Theme Manager and select a theme.  It should be applied instantly.

---

### Post by x1a4 on 2008-08-29
> **mb_webguy said:**
> I believe that Emerald is currently the only window decorator that supports transparent compositing.
Xfce's window manager (Xfwm4) has true transparency.

---

