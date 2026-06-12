---
title: "[SOLVED] 2 questions : shutdown ubuntu and some program to show music playing and mus"
date: 2008-11-03
forum: General Help
---

### Post by tyblos on 2008-11-03
hi guys im using ubuntu 8.10 2 days ago ... and my questions started. in this ubuntu version when i go to turn off button now dont appeares that screen for chosing turn off ..restart..etc now appeares some simple choise .. i wanna know if i can change that option and put it like the other ubuntu version????? 


my other question is if ubuntu have some program like CD art display in windows([http://www.cdartdisplay.com/plugins/p17_image_gallery/images/27.jpg](http://www.cdartdisplay.com/plugins/p17_image_gallery/images/27.jpg)) that small thig that shows music playing and music cover ... i wanna know if existes a program with the same functionalities but for my ubuntu 

that is all for now guys will waiting for answers



thanks

---

### Post by loomsen on 2008-11-03
1)

Create  a launcher(or modify the existing one), and use 
```
gnome-session-save --shutdown-dialog
```

as the command.

2)

Pretty similar, you gotta have conky for this solution too. But there are a lot of ways to achieve this.

---

### Post by tyblos on 2008-11-03
but someone know a media player that show the music cover and have a great style ??? like foobar for windows???? some friend talk me about songbird ... do you know the program???

---

### Post by loomsen on 2008-11-03
Yes, I know foobar. And I still miss it tbh.

But as the link, and my signature shows, I'm using gmusicbrowser now.

It's highly configurable, and layouts are based on Boxes, pretty much like foobar was. 

Actually I'm trying to figure out how I can add a gradient to the dock, and have reflections drawn to the cover/buttons.

Then it shouldn't be to hard to make it look as good as foobar did.

Bummer tho the guy who developed foo made it such windows specific...

You can run foobar as well, but the columns_ui won't work. And without an apropriate design foo wouldn't be what it is...

Anyway, give songbird a try, I didn't like it, but I don't like mozilla in general...

Using gmusic cause it has a lot of non-intuitive, yet great features, like for example clicking on the text showing the current album gives you a list of other albums of the same artist.
It even look at the screenshot, it even divides Mos & Talib, so I can view Mos albums, Talibs albums, and albums they made together.

[[img]http://img255.imageshack.us/img255/8614/screenshot53oi9.th.png[/img]](http://img255.imageshack.us/img255/8614/screenshot53oi9.png)

Whole non-intuitive commands and options are explained 
[HERE. The developer is a very nice and ambitioned guys too](http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html)


Another shot:
[[img]http://img505.imageshack.us/img505/3994/screenshot07lg0.th.png[/img]](http://img505.imageshack.us/img505/3994/screenshot07lg0.png)

Basically any imaginable layout is possible, the page has some too.

---

### Post by tyblos on 2008-11-03
maybe i will give i a try in gmusicbrowser   
but to change skins its easy???? like drag some folders to the gmusicbrowser folder????

because im new in linux world and i dont have sure where programs are instaled(the folder)


thanks

---

### Post by loomsen on 2008-11-03
Actually it's even easier.

You just have to edit a file in your home directory, write a couple of lines to it, restart gmusicbrowser and the layout will be available.

This is because layouts are available systemwide, unlike in Win where every application had it's own layout, and windows decorated the window borders only.

That's another reason why everything is so small in size compared to win, cause applications are able to share ressources.

Win applications always have to ship with everything they shall be able to do for you, linux applications come with dependencies to libraries. Libraries specify some sort of common codeblocks, which are used often in programming. And to avoid having to type that code over and over again, it's written to a library other applications may then rely to.

---

