---
title: "Reset emerald theme to default"
date: 2008-08-16
forum: General Help
---

### Post by CapinPete on 2008-08-16
I added an emerald theme which I do not want any longer.  I have Compiz Fusion Icon installed and I used the Emerald Theme Manager and deleted the theme in question.  However, it didn't change my windows.  Basically, how do I get my windows to look like they did when I first installed Ubuntu?

---

### Post by rune0077 on 2008-08-16
Remove Emerald from your startup list. System > Preferences > Sessions, then located Emerald on the list and remove it. Next time you boot, it won't load. You'd might as well uninstall it, if you don't plan on using it.

---

### Post by CapinPete on 2008-08-16
It's not that I don't want to use Emerald at all.  I have a fresh Ubuntu install and when I first loaded up the Emerald Theme Manager, it was empty, it contained no themes.  I added one from gnome-look.org and I didn't really like it so I removed it from Emerald Theme Manager (it contains no selectable themes again) but the theme persists.  My titlebars and all that still look like that theme.  I want to get rid of just that one theme and go back to the ubuntu default.

For reference, this is the theme I tried out: [Dark Ice Emerald]("http://gnome-look.org/content/show.php/Dark+Ice+Emerald?content=70284").

---

### Post by rune0077 on 2008-08-16
> **CapinPete said:**
> It's not that I don't want to use Emerald at all.  I have a fresh Ubuntu install and when I first loaded up the Emerald Theme Manager, it was empty, it contained no themes.  I added one from gnome-look.org and I didn't really like it so I removed it from Emerald Theme Manager (it contains no selectable themes again) but the theme persists.  My titlebars and all that still look like that theme.  I want to get rid of just that one theme and go back to the ubuntu default.

For reference, this is the theme I tried out: [Dark Ice Emerald]("http://gnome-look.org/content/show.php/Dark+Ice+Emerald?content=70284").

But the Ubuntu default is *not* an emerald theme. If you remove it from the start-up list as mentioned in my previous post, on next boot up, you should be back to the default theme.

The default theme uses metacity, not emerald.

---

### Post by CapinPete on 2008-08-16
I don't know how else to explain it.  Using the default installation I had compiz installed and had the wobbly windows, cube and all that jazz.  This all worked fine and looked just like the default Ubuntu install.

Now, I can use compiz fusion icon to switch the window manager to metacity but I lose all of the wobbly windows and eye candy for obvious reasons.  Switching to metacity does make the windows appear like the default installation.

I just want my compiz to go back to the way it was before I tried that Dark Ice theme.

---

### Post by rune0077 on 2008-08-16
Right, and I'm telling you, remove Emerald from your start-up list :)

This really is all you need. System > Preferences > Sessions, and delete Emerald from the list. Now reboot, and, as long as compiz is running, things should be back to normal.

Again, you don't need to disable Compiz (that's what's controlling your wobbly windows), only Emerald. Emerald only controls the window-decorations, nothing else, so there's no danger in disabling it or even uninstalling it. Compiz and Emerald is not the same thing.

---

### Post by CapinPete on 2008-08-16
Gotcha.  I didn't remove emerald from the start-up list.  I did go through compiz fusion icon and change the window decorator back to GTK instead of Emerald.  This way I still have the option of trying out new themes.

Sorry for the confusion.  I am a relative noob with linux.  As crazy as it sounds I think the fact that there are so many options is what's confusing.  I find that it's difficult to figure out what works with what and which options need to be tinkered with to achieve the desired effects.

Anyway, you get a thanks from me.

---

### Post by rune0077 on 2008-08-16
> **CapinPete said:**
> Gotcha.  I didn't remove emerald from the start-up list.  I did go through compiz fusion icon and change the window decorator back to GTK instead of Emerald.  This way I still have the option of trying out new themes.

Sorry for the confusion.  I am a relative noob with linux.  As crazy as it sounds I think the fact that there are so many options is what's confusing.  I find that it's difficult to figure out what works with what and which options need to be tinkered with to achieve the desired effects.

That's quite okay. And yes, it's confusing in the beginning. You'll figure it out as you go a long. And if not, that's what these forums are for.

Glad you sorted out it.

---

