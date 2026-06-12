---
title: "Tiling windows in GNOME"
date: 2005-11-15
forum: General Help
---

### Post by magnusbb on 2005-11-15
I'm a huge fan om GNOME. I like its simplicity, and I've configured it to work really well with my machine. But there is one thing I miss:

When I have a bunch of windows up at the same time, I want the WM to organize them for me, for example "tile them" over the screen. For example, if I have 5 windows of different folders in Nautilus up, I want them to fill the screen, so they match together.

Of course I use Virtual Desktops, but this is a very important addition to that. The question is: is this possible using Metacity, or do I have to use another WM that does tiling?

I don't want an Expos&#232; like feature. Expos&#232; only organizes the windows virtually, letting you choose one to focus on. My wish is to have "all in focus" at the same time, resizing them to match, like a "puzzle".

BTW: You get this feature in Windows XP by right-clicking on the taskbar and selecting "tile windows vertically" or "tile windows horizontically".

---

### Post by Fisheke on 2005-12-17
Let's bump this one up a bit, i'm extremely interested in it as well.. and none of my quests for anything about it on the web have proven useful..
A it's just a pity not having a good setup for a widescreen monitor..

---

### Post by makhand on 2006-03-28
I would also would find this a useful feature. Sure would be nice if someone who knows about this could instruct us all :-)

---

### Post by GaFFy on 2006-04-05
[QUOTE=makhand]I would also would find this a useful feature. Sure would be nice if someone who knows about this could instruct us all :-)[/QUOTE]

I am guessing since no one has replied with an answer that it is not possible to tile windows in gnome? how about kde?  I miss being able to tile vertically like in windows.

---

### Post by croak77 on 2006-04-05
Not sure if this will work, but you can try devilspie.
[http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)

There's a nice guide here:
[http://wiki.foosel.net/linux/devilspie](http://wiki.foosel.net/linux/devilspie)

---

### Post by GaFFy on 2006-04-06
Well I couldnt figure out devilspie but I did find a simple program that tiles windows perfectly.

[http://freshmeat.net/projects/wmtile/](http://freshmeat.net/projects/wmtile/)

I installed the .deb 
[http://freshmeat.net/redir/wmtile/56365/url_deb/tile_0.7.1_i386.deb](http://freshmeat.net/redir/wmtile/56365/url_deb/tile_0.7.1_i386.deb)

and then I edited the /usr/share/tile/wmprofiles
where it says Gnome2 0 0 36 0
i changed to Gnome2 0 0 24 0
and run tile from terminal using
tile -w -pGnome2

Works as expected nice qick and easy.
Although one thing I have noticed is that a maximized window wont get tiled, except when you unmaximize it you can see it was tiled just not unmax'd

I do have one question if anyone knows,
Is there any way to set this up to run when I click a certain key combination and/or configure it into the right click menu or the toolbar? :-k

---

### Post by ComplexNumber on 2006-04-06
[quote=magnusbb]I'm a huge fan om GNOME. I like its simplicity, and I've configured it to work really well with my machine. But there is one thing I miss:

When I have a bunch of windows up at the same time, I want the WM to organize them for me, for example "tile them" over the screen. For example, if I have 5 windows of different folders in Nautilus up, I want them to fill the screen, so they match together.

Of course I use Virtual Desktops, but this is a very important addition to that. The question is: is this possible using Metacity, or do I have to use another WM that does tiling?

I don't want an Exposè like feature. Exposè only organizes the windows virtually, letting you choose one to focus on. My wish is to have "all in focus" at the same time, resizing them to match, like a "puzzle".

BTW: You get this feature in Windows XP by right-clicking on the taskbar and selecting "tile windows vertically" or "tile windows horizontically".[/quote]
[this]("http://gnomefiles.org/app.php?soft_id=1343") application/applet may interest you.

---

