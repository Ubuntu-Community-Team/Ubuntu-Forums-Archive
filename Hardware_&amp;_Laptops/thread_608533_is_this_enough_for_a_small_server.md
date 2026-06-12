---
title: "is this enough for a small server?"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by Exonimus on 2007-11-10
Do you guys know these digital photo frames? well, my parents have been asking me to make one myself. (out of an old laptop) this seems to be a nice project, and I've already got all the documentation I need. However, my brother has been asking me to run a small game server for his clan(some kind of training server, locked, with room for about six people or something) for JKA(jedi academy) 
(a quake 3 based game with a Linux server available) next to that, I want to use it for downloading some torrents, and maybe for some remote stuff so I can login at school. I thought: If this photo frame is going to be on all day anyway, why not combine the three things? I mean, the gameserver doesnt need much, and downloading torrents needs nothing extra. However, for this all, I'm thinking of running either ubuntu, or a derivative. Be it fluxbuntu, xubuntu or even ubuntu server. I'm not sure what's better. But since I need to have a slideshow on, I need a GUI on anyway. I'd like some recommendations on what window manager to use, and what sort of laptop I need. I don't want to buy a new one, just a somewhat cheaper one, second hand somewhere. Should a laptop with a 1ghz processor and 256mb RAM be enough? Or is it better to run with more/less ? I know it depends on the version of ubuntu I'm going to use, or whether I'm going to run gnome/kde/etc. I also need to think about heat production, some extra cooling is fine, but it cant be too loud. And, of course, power consumption. And, of course, the costs. 

so, I'd like some advice please! :)

edit:while I'm at it: which application could I use best for full screen slide shows/photo showing?

---

### Post by BoneKracker on 2007-11-10
If that's all you're going to use it for, you don't need X.  

X is a _major_ RAM and CPU hog.  

You might want to consider just rendering the photos directly to the console (i.e., directly to the framebuffer).  Much lighter.  This would leave more resources for your game server etc.
[http://www.svgalib.org/jay/beginners_guide/beginners_guide.html](http://www.svgalib.org/jay/beginners_guide/beginners_guide.html)

Also, I woldn't get a laptop for this.  Laptops suck in just about everyway except that they're portable and have a battery.  You don't have either of those requirements.

Maybe you want a very-small-form-factor PC with a nice little LCD display.  Something like a mini-ATX.  Maybe one of the new $200 Everex machines would do (or something like them).

---

### Post by Jose Catre-Vandis on 2007-11-10
get more ram if you can

---

### Post by BoneKracker on 2007-11-10
[http://www.svgalib.org/rus/zgv/index.html](http://www.svgalib.org/rus/zgv/index.html)

ZVG is a photo viewer that will run on svgalib  (i.e., a photo viewer that you can run without X).  You can run lots of other graphical apps without X as well.

Also check out SDL (Simple Direct Media Layer - another way to directly address the framebuffer and avoid using X):
[http://www.libsdl.org/](http://www.libsdl.org/)

You could have your photoviewer thingy be a multimedia presentation with video etc.  You can even run graphical games like this without X (quake, etc.).  Here is a list of SDL apps:
[http://www.libsdl.org/applications.php](http://www.libsdl.org/applications.php)

---

### Post by Exonimus on 2007-11-10
thanks for the quick replies.

I'm not sure about the small form factor pc's. Thing is, I want the photo frame to hang on a wall,so it can't be that thick. The advantage of a laptop is that it's thin, and that's kind of what I need. Other suggestions are welcome though, but I think these small form factor pc's will just be too big. And, I kind of need the portability(not many cables to get rid of, etc.) I think this will actually be easier than connecting an lcd screen to this small form factor pc(besides, where to place it?) but I'll see if there are other solutions. Other than that, with some cooling, I should be fine.(I hope)

to give you an idea:

[http://www.student.tue.nl/q/j.g.s.v.uden/S4011444.JPG](http://www.student.tue.nl/q/j.g.s.v.uden/S4011444.JPG)

it's not going to look like this, but this is more or less the idea.

---

### Post by BoneKracker on 2007-11-10
I cannot get your picture.

I would think an LCD panel would be less difficult to hang on a wall than a laptop.

The only reason I suggest a "small form-factor pc" is because that's all you need.  It will take up less space below where you hang the display.

Another thing that would work nicely would be one of the iMacs (G4 or G5 models) if you can get a used one.  The G5 itself is kind of like a flat panel, but it's got the whole computer built in.  The G4 (the one with the round base) is kind of like a desk lamp with it's pivoting neck and flat screen.  Either of those might make nice "picture frames".

---

