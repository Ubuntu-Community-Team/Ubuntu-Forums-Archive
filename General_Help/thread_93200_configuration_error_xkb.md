---
title: "configuration error xkb"
date: 2005-11-21
forum: General Help
---

### Post by patrickfromspain on 2005-11-21
Hi there!

Today I've realized that I've good a problem.. my keyboard. I live in spain, and here we some special characters as: &#224; &#225;, &#232; &#233; and so on, &#241; and one more. Well the &#241; doesn't work. If I would press it nothing comes out.. as I hadn't touched nothing. the ones &#224; &#225; go fine, but. Also, I do Alt Gr + 3 nothings turns out, and # should appear...

I've tried in sistem -> preferences -> keyboard and there I already have spanish distribution.. I've tried to select latin amercian and.. Error on activating XKB configuration. It says it could happen by many causes:

libxklavier
x server fail
x server with incompatible impletation of libxkfile... 

It also says that if I want to talk about this as an error I should  run: 

patrick@ubuntu:~$ sudo xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "es", "es", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "es", "es", ""
patrick@ubuntu:~$


and:

patrick@ubuntu:~$ conftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
bash: conftool-2: command not found
patrick@ubuntu:~$

reinstalling libxklavier and kbdutils hasn't solved anything, and if I try to change the keyboard style the same error appears..

So.. anyone knows what's happening? Any solution?

Thanx!

---

### Post by Burning Bronx on 2005-11-23
Hola, Patrick! 
The problem you have is pretty common with the Breezy installation on non-US systems. There have been heavy discussions on Bugzilla and some of the people have found acommodating solutions. You can read lots about it on the above mentioned [bug topic in bugzilla](http://bugzilla.ubuntu.com/show_bug.cgi?id=15372#c35). Comment 35 and later are particulary about your problem.

Read, try and say how it went. Vaya con dios, hombre ;)

---

### Post by patrickfromspain on 2005-11-23
Muchas gracias! I'll have a look in there and see if I can solve it.


Adios y gracias!

---

