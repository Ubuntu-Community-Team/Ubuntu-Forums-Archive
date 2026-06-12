---
title: "ugly line in opera"
date: 2008-08-19
forum: General Help
---

### Post by vixducis on 2008-08-19
I use this very nice skin for opera on ubuntu, that goes perfect with the rest of my theme, but some white line betweens the chrome and the adress really screws it up (see image). 

[[IMG]http://img360.imageshack.us/img360/7857/schermafdrukwq1.th.png[/IMG]](http://img360.imageshack.us/my.php?image=schermafdrukwq1.png)

Dus anyone know how to remove this ugly artefact?

---

### Post by mtbsoft on 2008-08-19
I'd say the line denotes the boundary between the application window and the decorator frame around it - it mimics a bevelled edge catching light from above.  It is probably visible to some extent on all applications, not just Opera, but this is the most prominant for you.

You might be able to remove it by modifying the theme but I've never tried so can't be sure.  If it is an attribute of the Opera main window, however, then you are unlikely to be able to remove it.

Edit: try removing the decorators temporarily in Ubuntu and setting a dark background, this will indicate if the attribute is Ubuntu or Opera sourced.  If Opera you may be able to modify the Opera skin instead.  Which skin is it?

---

### Post by vixducis on 2008-08-20
It's a slightly edited version of [this skin]("http://clonemac.deviantart.com/art/Leopard-for-Opera-80965865"). But the problem is also there with the original version.

I'll try to do what you said in a minute because i am currently working in windows...

---

### Post by vixducis on 2008-08-20
Ok, I don't know whether you mean this but if I change the emerald skin (window manager I use), the white line remains, and if I change the opera skin, it does to.

---

### Post by mtbsoft on 2008-08-20
Sounds like it is neither part of the window manager skin nor the Opera skin but rather a boundary between the two - looks like you may be stuck with it I'm afraid.

---

### Post by Eestlane on 2008-11-07
Finally figured it out
Just use qt4 builds of Opera :)

---

### Post by loomsen on 2008-11-07
Where do you've got them from? I only find qt3 builds of opera, facing a similar problem...

---

### Post by Eestlane on 2008-11-09
[ftp://ftp.opera.com/pub/opera/linux/962/final/en/](ftp://ftp.opera.com/pub/opera/linux/962/final/en/)

---

### Post by loomsen on 2008-11-13
OK, there are only 386 qt4 builds available, unfortunately not suitable for my amd64. However, and weird as this whole thing is, somehow my compiz-deskmenu, where I created a shortcut to opera simply by having the command 
```
opera -nomail -notrayicon -nolirc
```
didn't launch:
```

foobar@tiffany:~$ which opera
/usr/bin/opera
foobar@tiffany:~$ 

```
this, which it actually is supposed to, but instead
[[img]http://www.ubuntu-pics.de/thumb/5601/screenshot_04_qLilZC.png[/img]](http://www.ubuntu-pics.de/bild/5601/screenshot_04_qLilZC.png)

And I'm not having any problems, neither laggy redraws of the window nor any menubar which shouldn't be there. Just Opera. Jeez, I nearly forgot why I'm an opera addict since version 4.0 :D

Another strange thing, as the screenshot shows, there's some kind of gtk-related transparency. The tab showing running processes isn't opaque at all. 
Anyway, to get completely caught up in confusion, this seems to apply to the system monitors window only :?:
Weird. 

Anyway, back to topic, give it a try, works for me... When starting /usr/bin/opera somehow "--style Plastique" is appended to the actual command. Browsing through nearly any config file opera ships with I still wasn't able to find any file where such an appendix would have been specified.

Anyway, try running above command and see what it does.

---

### Post by loomsen on 2008-11-13
Alright, tested this forth and back with different user accounts, and running opera with 
```

/usr/lib/opera/9.62/opera -nomail -notrayicon -nolirc

```
instead of running it with opera or /usr/bin/opera actually does the trick for me. As amazing as it sounds.

---

### Post by tomas.sprlak on 2008-11-15
hi, I'm not sure if I understand: you actually got rid of the ugly line by running opera from /usr/lib/opera/9.62/?  if I get it right, you have qt3 build on a 64bit machine?
'cause I tried it here with qt3 i386 build and the line is still there. moreover opera's pluginwrapper fails to load when I do it...

---

### Post by loomsen on 2008-11-15
> **tomas.sprlak said:**
> hi, I'm not sure if I understand: you actually got rid of the ugly line by running opera from /usr/lib/opera/9.62/?  if I get it right, you have qt3 build on a 64bit machine?
'cause I tried it here with qt3 i386 build and the line is still there. moreover opera's pluginwrapper fails to load when I do it...

Yes, u get it right. Couldn't find any qt4 builds for amd64.
/usr/lib/opera/9.62/opera
works for me. Still some weird behavior - if I click on a link when opera isn't running, it starts with -style Plastik appended...

---

