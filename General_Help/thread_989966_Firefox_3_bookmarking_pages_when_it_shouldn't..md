---
title: "Firefox 3 bookmarking pages when it shouldn't."
date: 2008-11-22
forum: General Help
---

### Post by jonboy99 on 2008-11-22
Hi folks.  Am on 8.10 with gnome, clean install. Firefox 3.0.4 but has done this with previous versions of FF3.  Dell 640m.

Sometimes while browsing, i'll left click on the 'Bookmarks' toolbar to bring down the list of bookmarks so I can select one, but instead of bringing down the list like usual, it bookmarks the current page.  Happens often enough to extend my bookmarks quite a lot.
I am using the left button to click, rather than a finger tap on the touchpad, so no funny business with the touchpad going on.

It's getting quite annoying!  Any ideas?

thanks
Jon

---

### Post by detroit/zero on 2008-11-22
+1

I've noticed the same thing as of late.

---

### Post by philinux on 2008-11-22
To see if it's a mouse problem try using alt B to get the drop down bookmarks.

---

### Post by jonboy99 on 2008-11-22
cheers phil, that shortcut works ok now, i'll see if it has the same intermittent problem.  Although to be honest, it's so much quicker than the mouse i'll probably just use the shortcut from now on, so problem pretty much solved!  :)

---

### Post by philinux on 2008-11-22
You could ,backup your bookmarks, close FF then Delete/Rename the .mozilla folder. Start FF then restore your bookmarks. Sometimes there can be corruption of the profile folder.

---

### Post by detroit/zero on 2008-11-24
Using alt+b does workaround the problem for now, but no matter what, when I click on my bookmarks menu for the first time in a browsing session, FF wants to bookmark whatever page I'm on. (This only happens on the first click.)

Making a new user profile doesn't change this behavior.

---

### Post by jonboy99 on 2008-12-23
Anyone found a fix for this yet?  It's really irritating me now.  I've found the easiest work around apart from alt-b is to click on the Tools button, then slide across to Bookmarks when the drop down appears, bu sometimes have to click Tools 2 or 3 times to get the drop down appear - it's like it thinks i'm pressing a modifier key or something along with the mouse click.
Several updates of firefox later haven't fixed it.

Does anyone know what shortcut key gives the bookmark pop up normally?  This might provide a clue.

---

### Post by Aearenda on 2008-12-23
It's a known issue, but I can't remember where I saw it. For me, turning off all assistive technology stuff fixed it. I've seen it occur on Windows XP as well, when a screen reader was active.

---

### Post by jonboy99 on 2008-12-23
Dude, I think you fixed it!  Cheers fella!

---

### Post by detroit/zero on 2008-12-24
> **Aearenda said:**
> It's a known issue, but I can't remember where I saw it. For me, turning off all assistive technology stuff fixed it. I've seen it occur on Windows XP as well, when a screen reader was active.
You mean like Orca and the on-screen keyboard and all that? One of the first things I do to an Ubuntu install is remove all that stuff. I haven't had it turned on, or even had it installed, since 8.04 came out.

---

### Post by Aearenda on 2008-12-24
That's what fixed it for me - and yes, there's no rhyme or reason to it.

---

### Post by jonboy99 on 2008-12-24
> **detroit/zero said:**
> You mean like Orca and the on-screen keyboard and all that? One of the first things I do to an Ubuntu install is remove all that stuff. I haven't had it turned on, or even had it installed, since 8.04 came out.

Maybe double check it hasn't enabled itself during an update or something?  I just went to the system menu, preferences, assistive technologies, and unchecked assistive technologies on that screen.  I certainly don't remember enabling them at any time.

---

### Post by malleus74 on 2008-12-24
THANK YOU! Could you post a list of all the assistive programs you turned off and how you did it (i.e., uninstalled it?) to fix this? This is extremely annoying...

---

### Post by leva on 2008-12-24
I actually had the same problem on a computer with Windows XP.

---

### Post by detroit/zero on 2008-12-24
> **jonboy99 said:**
> Maybe double check it hasn't enabled itself during an update or something?  I just went to the system menu, preferences, assistive technologies, and unchecked assistive technologies on that screen.  I certainly don't remember enabling them at any time.
If that isn't the darndest thing in the whole darn world, I don't know what is.

I checked, and assistive tech was enabled in that dialog. I don't know how, or even what was enabled (as everything is removed) but there it was. I'll post back and let you know if the behavior changes.

Thanks ;)

---

### Post by detroit/zero on 2008-12-25
Well, I can't say I've noticed the behavior since turning off the assistive technologies.

That would appear to be the fix.

---

