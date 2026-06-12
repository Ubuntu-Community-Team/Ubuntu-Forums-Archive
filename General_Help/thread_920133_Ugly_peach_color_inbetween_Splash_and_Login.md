---
title: "Ugly peach color inbetween Splash and Login"
date: 2008-09-14
forum: General Help
---

### Post by Minipalmer on 2008-09-14
Hey there,

I recently installed custom splash and login windows. They boot up and look great, but after my splash there is Ubuntu's horrid peach color, then the login window. The same color comes up after the login as my desktop is loading up.

The color also presents itself when I select my name on the login window, and it throws off the whole theme and looks nasty.

Is there a way I can change this color to something neutral, like grey, so it fits in with all my themes?

Thanks,
Taylor

---

### Post by cl0ckwork on 2008-09-15
> **Minipalmer said:**
> Hey there,

I recently installed custom splash and login windows. They boot up and look great, but after my splash there is Ubuntu's horrid peach color, then the login window. The same color comes up after the login as my desktop is loading up.

The color also presents itself when I select my name on the login window, and it throws off the whole theme and looks nasty.

Is there a way I can change this color to something neutral, like grey, so it fits in with all my themes?

Thanks,
Taylor

go to system>admin>login window
and under the local tab there should be an area to select the back ground color

i owuld also suggest changing the background color for your desktop if you havent alredy done so
system>pref>appearance   in the background tab

---

### Post by Minipalmer on 2008-09-17
Thanks, that work.

The problem I have now is my login screen selects my user account when I type it in, and of course it highlights it in that same peach color. I can't find out where it's coming from. Any thoughts?

---

### Post by leef on 2008-09-17
That could be either a problem with either the gtk theme or the gdm(login screen) theme if you haven't changed from the default. It's most likely the gtk theme. The gtk them can be changed with;

System>Preferences>Theme

or if you are using a window manager instead of gnome try;

```

sudo apt-get install gtk-chtheme
gtk-chtheme

```

to select a new theme

---

### Post by Minipalmer on 2008-09-17
I have a customized theme said in Gnome, with controls, colors, and window borders all pulled from different themes. However, all of these are based around gray colors, no orange. :mad:

---

### Post by leef on 2008-09-18
what is "GtkTheme=" set to in /etc/gdm/gdm.conf? if it's set to human, thats where the orange is coming from.

---

### Post by Genius314 on 2008-09-18
The color actually isn't in the GTK or GDM theme.

[Here's a post]("http://ubuntuforums.org/showpost.php?p=3672448&postcount=2") that I found, explaining how to change the color.

Hope that helps. :)

---

### Post by Minipalmer on 2008-09-18
Hey there, that looks like a good find. But didn't fix it :D

I fixed the background color, but for some reason when the login selects my account it highlights it in peach, and I can't find where that's coming from.

---

### Post by I wanted to leave on 2008-09-18
boundingbox-0-2.png

I think this is what you're looking for. In gdm/themes/humanlist

---

### Post by Minipalmer on 2008-09-18
I'm a bit of a coding newb and don't know how to access stuff in the terminal. Can anyone tell me how to to access that, and how to change it?

Couldn't I just edit that .png and make it gray or something? (I don't know what it is...)

---

### Post by Braduntu on 2008-09-19
My first post, yay....


Got this from lifehacker, who got it from here...

[http://ubuntuforums.org/showthread.php?t=753261](http://ubuntuforums.org/showthread.php?t=753261)

Tells how to load with background image instead of color.

Haven't tried it yet myself, but comments seem promising.

---

