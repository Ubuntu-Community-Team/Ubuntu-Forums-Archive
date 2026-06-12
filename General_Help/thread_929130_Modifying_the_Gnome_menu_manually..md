---
title: "Modifying the Gnome menu manually."
date: 2008-09-24
forum: General Help
---

### Post by ODF on 2008-09-24
I'm searching something to manually modify it. Where should I look ? I did many searches about it but it seams complicated.

---

### Post by billgoldberg on 2008-09-24
If you are talking about going into the text files and start hacking, I can't help.

If you just need to remove and add some apps/categories.

Go to "system -> preferences -> main menu" and go crazy.

---

[I]Offtopic:

post 2000![/I]

---

### Post by lisati on 2008-09-24
If it's something that appears on one of the menus (e.g. Applications, places or system) then right click on the heading and look for "Edit menus".
If it's for one of the programs, just right-click on the item, and clock on "properties"

Hope this helps.

---

### Post by ODF on 2008-09-24
> **billgoldberg said:**
> If you are talking about going into the text files and start hacking, I can't help.

If you just need to remove and add some apps/categories.

Go to "system -> preferences -> main menu" and go crazy.

---

[I]Offtopic:

post 2000![/I]

I'm talking about going into the text files and start hacking ... something like that : [http://code.google.com/p/gnome2-globalmenu/](http://code.google.com/p/gnome2-globalmenu/)

I'm still unable to install it on my distribution that is why hehe.

---

### Post by anotherdisciple on 2008-09-25
> **ODF said:**
> I'm talking about going into the text files and start hacking ... something like that : [http://code.google.com/p/gnome2-globalmenu/](http://code.google.com/p/gnome2-globalmenu/)

I'm still unable to install it on my distribution that is why hehe.

If you want to make the top menu bar work like it does in Mac OSX... WOW! You must have a lot of confidence in your ability to program... I wouldn't even try it! haha.. but that's just me!

---

### Post by loomsen on 2008-09-25
Menu entries are usually generated in /usr/share/menu, /usr/lib/menu and\or /usr/share/menu/default. At least if you have menu installed :)

You may as well create a file ~/.menu which will override default settings for you. HF, and let me know about the progress :)

*edit*
After reading your post again you're most likely looking for the menu files generated after a package has been installed right?
Without any menu support programs, wrappers or whatsoever, menufiles are generated in
/usr/share/applications

---

