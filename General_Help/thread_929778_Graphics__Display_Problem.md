---
title: "Graphics / Display Problem"
date: 2008-09-25
forum: General Help
---

### Post by Nanthiel on 2008-09-25
Hey there!

First I'd like to point out that I'm fairly new to linux (user for less than a week now, using Ubuntu 8.04)... anyway, to my problem:

My desktop effects all worked fine (Compiz Fusion). When I first booted Ubuntu, the gfx drivers installed automatically and worked... well, the games had a few problems (3D ones downloaded after), I thought those were graphic driver problems, so I tried reinstalling them and changing them... I don't remember exactly all the steps that I did, in the middle also tried installing Envy...

Either way, I messed it all up, and now when I boot up, Linux comes up with an error that it can't identify my hardware, and that I could manually Configure it, or just let it run at Low Graphics (or something similiar) mode. Configuring it manually does not help.

Now, when I remove all nvidia drivers from Synaptic, the resolution displays fine (it's 640x480/800x600 otherwise), but reinstalling them does this again. I tried removing them with a complete remove (meaning with configuration files), but it didn't help.

So, what must I do to reset all graphics settings? And what must I do with the drivers, or with the system, or with -something-, to make a few games (Scorched 3D, Frets on Fire, Nexuiz,...) work with normal FPS. They don't seem so graphic intense to me to be running at sickeningly low FPS on a 7600GT, the card should handle them fine, or not?

Anyway, please help!


- Nanthiel

---

### Post by Infinite Indefinite on 2008-10-01
Well, it might be helpful to create two different login options - one with XGL and one without.  The latter can be used to run the games, the former to run compiz.

The following link describes how to do this:

[http://ubuntuforums.org/archive/index.php/t-581568.html](http://ubuntuforums.org/archive/index.php/t-581568.html) 

The Compiz Switch may also help:

[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

