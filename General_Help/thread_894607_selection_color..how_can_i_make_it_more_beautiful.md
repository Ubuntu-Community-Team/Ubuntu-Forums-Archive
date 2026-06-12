---
title: "selection color..how can i make it more beautiful?"
date: 2008-08-19
forum: General Help
---

### Post by bigdee973 on 2008-08-19
im sick of the plain old looking selection color i get when i scroll through the main menu (applications, places, systems) i want to give it a gradient effect or animation of sprites such as snow or leaves falling when something is highligh  if possible..im just tired seeing the normal plain one color effect selection highlight... look at the picture below notice the red circle...the grey hightlight sucks and looks bad..i want to make it gradient ...where i blend the color from purple to blue just like the background color of the menu where it says pictures documents etc...i also want ot make it look like a mac when i highlight and all that...could u do this?

[IMG]http://i94.photobucket.com/albums/l107/blasintildadeath/Screenshot-2.png[/IMG]

---

### Post by billgoldberg on 2008-08-19
> **bigdee973 said:**
> im sick of the plain old looking selection color i get when i scroll through the main menu (applications, places, systems) i want to give it a gradient effect or animation of sprites such as snow or leaves falling when something is highligh  if possible..im just tired seeing the normal plain one color effect selection highlight... look at the picture below notice the red circle...the grey hightlight sucks and looks bad..i want to make it gradient ...where i blend the color from purple to blue just like the background color of the menu where it says pictures documents etc...i also want ot make it look like a mac when i highlight and all that...could u do this?

[IMG]http://i94.photobucket.com/albums/l107/blasintildadeath/Screenshot-2.png[/IMG]

Use this app:

[https://launchpad.net/gnome-color-chooser](https://launchpad.net/gnome-color-chooser)

or take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=377397&highlight=gtkrc](http://ubuntuforums.org/showthread.php?t=377397&highlight=gtkrc)

ps: you can set your user photo in "about me". I'm not sure where it's located as I'm not in gnome right now.

---

### Post by bigdee973 on 2008-08-19
thanks i installed gnome color chooser but im real confused on how it works.. could u help me out.. the other link showed extactly waht i wanted to do to my desktop but it seems very very complex and the guide isnt specific enough... im not much of a coder and dont understand code so well... but thanks man if u have tutorials for gnome color chooser or a better tutorial to code to make stuff more gradient please help me out again thanks i appreicate your help.

---

### Post by billgoldberg on 2008-08-20
> **bigdee973 said:**
> thanks i installed gnome color chooser but im real confused on how it works.. could u help me out.. the other link showed extactly waht i wanted to do to my desktop but it seems very very complex and the guide isnt specific enough... im not much of a coder and dont understand code so well... but thanks man if u have tutorials for gnome color chooser or a better tutorial to code to make stuff more gradient please help me out again thanks i appreicate your help.

I just hunted down the links for you.

I haven't actually done this.

---

### Post by mcduck on 2008-08-20
To change the plain color into gradient or something else you need to use a theme made for some other GTK2 theme engine, they all provide different kinds of buttons and other widgets. Easiest way would be to just find a theme you like from gnome-look.org.

For more special effects like animations and such you'd better learn programming.. I'd say C, Cairo & GTK2 at least.. There aren't any GTK engines with that kind of features yet. DynDyn can do some random textues into buttons but there really isn't anything animated.

edit: just to explain it better, GTK2 is the "language" the programmers use when vcreating the graphical user interface. When you run the program the GTK eengine reads the code and draws the program to your display. Different GTL engines can make different looking buttons and such. GTK theme just tells the engine what colors to use and other details like that. But if you are using GTK engine that draws single-color buttons there is nothing you can do to make them anything else than single color. You need to use a GTK engine that draws gradient buttons.

Most of the time people don't even need to know about GTK engines, as lng as you have the required engine installed you can just pick any theme yu like from gnome-look.org and use it. But if you can't fins a theem you like and instead choose to make one yourself you need to know about the engines and what kind of widgets they draw, and then choose one that you like fo your theme.

---

### Post by bigdee973 on 2008-08-21
> **mcduck said:**
> To change the plain color into gradient or something else you need to use a theme made for some other GTK2 theme engine, they all provide different kinds of buttons and other widgets. Easiest way would be to just find a theme you like from gnome-look.org.

For more special effects like animations and such you'd better learn programming.. I'd say C, Cairo & GTK2 at least.. There aren't any GTK engines with that kind of features yet. DynDyn can do some random textues into buttons but there really isn't anything animated.

edit: just to explain it better, GTK2 is the "language" the programmers use when vcreating the graphical user interface. When you run the program the GTK eengine reads the code and draws the program to your display. Different GTL engines can make different looking buttons and such. GTK theme just tells the engine what colors to use and other details like that. But if you are using GTK engine that draws single-color buttons there is nothing you can do to make them anything else than single color. You need to use a GTK engine that draws gradient buttons.

Most of the time people don't even need to know about GTK engines, as lng as you have the required engine installed you can just pick any theme yu like from gnome-look.org and use it. But if you can't fins a theem you like and instead choose to make one yourself you need to know about the engines and what kind of widgets they draw, and then choose one that you like fo your theme.

thank you, very informative and i was wondering if gtk was a language, but now i see one would have to create an engine for that kind of animation to render..thanks..

---

