---
title: "GTK2 Engine error"
date: 2008-11-05
forum: General Help
---

### Post by PinkFloyd102489 on 2008-11-05
When I open the Appearance window, there's an error at the bottom that says:

"This theme will not look as intended because the required GTK+ theme engine " is not installed."

The bad part is, I installed all of the GTK2 engines I could, yet it still doesnt work. My icons do not render correctly because of this. I checked my themes (aero-clone) gtkrc file and the engine bit says "pixmap". I saw a pixbuf engine. Do I need to change pixmap to pixbuf in the gtkrc file?

---

### Post by scylla2 on 2008-11-05
I was just going to post the same question since this is exactly what I'm experiencing when trying to install new GTK+ themes.

To make matters worse, I tried to fix it with the command "sudo apt-get install gtk2-engines-ubuntulooks" but this didn't solve my problem and now other themes like Darkroom (which I really liked) are no longer on my system. Can I somehow undo this command??

Sorry, I don't mean to hijack your thread. I hope this isn't a bug with Intrepid.

---

### Post by PinkFloyd102489 on 2008-11-06
Replacing "pixmap" with "pixbuf" in the theme's gtkrc file give pixbuf module path errors.

---

### Post by Ivo Moelans on 2008-11-08
Look in the theme's gtkrc file for empty engine-tags. These are commonly used in ***style "unstyle"*** which is meant to prevent Sodipodi from crashing while opening the Object-Style dialog.

```
style "unstyle"
{
	engine ""
	{
	}
}
```

Fill the "" with a 'known' engine, e.g. pixmap, so that the code looks like this:

```
style "unstyle"
{
	engine "pixmap"
	{
	}
}
```

This should correct the problem.

---

