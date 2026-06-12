---
title: "change entry box color in GDM?"
date: 2008-10-14
forum: General Help
---

### Post by squidmaster on 2008-10-14
Is it possible? I've been trying a bunch of different things including doing an image overlay but can't seem to figure it out.

Basically what I want to do is make the stock username&password entry box a different color besides white. Is this even possible?

---

### Post by squidmaster on 2008-10-15
looks like no one knows how?

---

### Post by loomsen on 2008-10-15
Nope, you're the first one to ask this for sure. I wouldn't have searched neither if I was you---

sudo apt-get install gnome-color-chooser

And, btw, I wouldn't listen to others to much, google ain't that bad.

---

### Post by squidmaster on 2008-10-16
I'm taking you said those things as sarcasm. I did search but didn't find anything.

And GCC is not what I was looking for and does not give me the options I wanted.

---

### Post by loomsen on 2008-10-16
Whut, are you kiddin?

[img]http://wiki.ubuntuusers.de/_image?target=GNOME_Konfiguration%2Fgcc.png] And this picture shows only one of six tabs you got.[/img]

I can hardly imagine what else to change, but well... 

[gnome-color-chooser](http://www.punk-***-bitch.org/gnome-color-chooser/)

Wasn't too hard to find...


*lol*
URL gets ***ed out by the forum :D

punk- a s s-bitch it is anyway

---

### Post by squidmaster on 2008-10-16
Not kidding. I already had GCC but it doesn't change pre-login colors.

---

### Post by jgaray on 2009-07-18
I think I know what you mean. I have exactly the same problem: the input box in GDM is always white, no matter what theme I'm using. And there are some themes created to use different colors, but it doesn't seem to work. Have you found any solution in the mean time? I'm still investigating it...

---

### Post by JackTheDipper on 2009-07-22
Just change the theme in /etc/gdm/gdm.conf

Example:
```
[gui]
GtkRC=/usr/share/themes/Glossy/gtk-2.0/gtkrc
```

---

