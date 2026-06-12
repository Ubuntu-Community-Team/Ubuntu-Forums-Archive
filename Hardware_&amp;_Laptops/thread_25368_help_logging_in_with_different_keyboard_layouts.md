---
title: "help logging in with different keyboard layouts"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by graigsmith on 2005-04-09
hey, im one of those wierd people who use dvorak.  i like being able to log in using dvorak.

but how do i let someone else log in using qwerty?  besides giving them a piece of paper with seemingly random letters and numbers to type   :twisted:

---

### Post by graigsmith on 2005-04-11
bump.  is there some way i can add dvorak and qwerty to the login screen?

---

### Post by nautilus on 2005-04-22
I have the same issue actually..  It seems not, at least, not at this point...

I'm going to bust some heads in KDM-land (my login manager) and see if i can't force some change.

---

### Post by Alexander Kirillov on 2005-04-22
[QUOTE=graigsmith]bump.  is there some way i can add dvorak and qwerty to the login screen?[/QUOTE]
 You can edit xorg.conf file and add more keyboard layout there, even adding an option for switching between layouts, e.g., by pressing both alt keys simultaneously.
Then this will available at login screen 

 Do not remember precise syntax, though: try google search with "xkb keyboard layout".

May I suggest another solution? why not make default system layout to be qwerty, but make dvorak default layout for yourself as user (using keyboard preference tool of gnome)? This way, you'll have to type your name and password in qwerty, but after that, use  in dvorak.

---

### Post by graigsmith on 2005-05-01
"May I suggest another solution? why not make default system layout to be qwerty, but make dvorak default layout for yourself as user (using keyboard preference tool of gnome)? This way, you'll have to type your name and password in qwerty, but after that, use in dvorak."

that would take me forever to log in.  when i retrained on dvorak, i forgot how to use qwerty. --its gone.  plus if my system default was qwerty, i would not be able to use the terminals, like the one you press ctrl-alt-f1 to get to.  im the only one on the system that needs those terminals, so it doesn't make sense to use qwerty for them.  when you change the keyboard layout in gnome, it doesn't affect the terminals that you log into.

---

