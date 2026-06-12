---
title: "How do I do this with compiz?"
date: 2008-12-01
forum: General Help
---

### Post by gamesnepal on 2008-12-01
I found this picture on the internet and I would like to have an earth rotate instead of a cube. How do I do this?

[[IMG]http://img47.imageshack.us/img47/5977/desktopcustomizatn7smalzp0.jpg[/IMG]]("http://img47.imageshack.us/img47/984/desktopcustomizatn7og4.jpg")

---

### Post by slinkey1981 on 2008-12-01
OK, get ready to take notes....

As far as I know the sphere plugin in only available in 0.7.6 and up, (0.7.9 is out in git, Compiz-Fusion runs better when you build it yourself anyways)[ Here is a little app that will build it for you.....  It's nice.]("http://ubuntuforums.org/showthread.php?t=871165&highlight=fusion+build")

Then you goto Cube Deformation and Reflection, change it to Sphere, and turn reflection off.

The background is a Skydome, just search for [a space looking one]("http://ubuntuforums.org/attachment.php?attachmentid=84072&d=1220569759"). You can change it under "Desktop Cube" (I think)

[The wallpaper itself]("http://ubuntu.hamdi.web.id/compiz/earth-desktop-01.html") could be a little tricky, as I *think* the only way to do that still requires you to [take background drawing away from Nautilus and give it to compiz]("http://ubuntuforums.org/showthread.php?t=17359") so that you can have 4 different wallpapers (and the two cube caps)

Getting the windows to stick out like that is as easy as turning on "3D Windows" and fiddling "Window Space" and "Minimum Cube Size"

That should get you a result that's pretty close to what you see in the screenshot you posted.

---

### Post by Wartender on 2008-12-01
one idea that comes to mind is getting six images that are pieces of the globe, and using compiz to render them on the different workspaces using the wallpaper plugin and the cube caps plugin for the top and bottom. where you can find those images is beyond me.

---

### Post by Usufruct on 2008-12-01
Try this:

[http://gnome-look.org/content/show.php/EarthDesktop?content=84070]("http://gnome-look.org/content/show.php/EarthDesktop?content=84070")

Cheers!

---

### Post by binbash on 2008-12-01
desktop cube + rotate cube + deformation plugin (sphere)

---

### Post by SaintDanBert on 2008-12-01
Is there a quick and clean way to toggle compiz on and off and preserve one's settings?

I use a tablet PC. Compiz makes a lot of sense most of the time. However, when I swap from landscape to portrait, it leaves compiz confused. Until I can discover how to make compiz play tablet, I could simply toggle off, swap, tablet, swap back, toggle on. Grumble but it would work for now.


thanks in advance,
~~~ Dan 0;-D

---

### Post by slinkey1981 on 2008-12-01
> **SaintDanBert said:**
> Is there a quick and clean way to toggle compiz on and off and preserve one's settings?

I use a tablet PC. Compiz makes a lot of sense most of the time. However, when I swap from landscape to portrait, it leaves compiz confused. Until I can discover how to make compiz play tablet, I could simply toggle off, swap, tablet, swap back, toggle on. Grumble but it would work for now.


thanks in advance,
~~~ Dan 0;-D

Compiz Fusion Icon toggles it on and off from an icon in the system tray. Seems to be what you are looking for.

---

### Post by Forlong on 2008-12-01
> **slinkey1981 said:**
> As far as I know the sphere plugin in only available in 0.7.6 and up, (0.7.9 is out in git, Compiz-Fusion runs better when you build it yourself anyways)[ Here is a little app that will build it for you.....  It's nice.]("http://ubuntuforums.org/showthread.php?t=871165&highlight=fusion+build")
cubeaddon is part of Intrepid's Compiz.
The plugin is called **Cube Reflection and Deformation** in ccsm

And even if it wasn't, **[COLOR="Red"]do not advise to compile Compiz from source[/COLOR]**

---

### Post by slinkey1981 on 2008-12-01
> **Forlong said:**
> cubeaddon is part of Intrepid's Compiz.
The plugin is called **Cube Reflection and Deformation** in ccsm

> **slinkey1981]Then you goto Cube Deformation and Reflection, change it to Sphere, and turn reflection off.[/QUOTE]

Not everyone is using Intrepid... I know I'm not. I don't know exactly what is or isn't in it, and unless people clarify which version of Ubuntu they are using, I'll persistently assume that they are using Hardy.

[QUOTE=Forlong said:**
> And even if it wasn't, **[COLOR="Red"]do not advise to compile Compiz from source[/COLOR]**

Actually, I pointed out an app that will download all build essential tools, compiz source and built it for you. If it DOES break, the app has a handy little "Uninstall" button. Which isn't exactly like advising to build from source.

I thought the reason you don't advise newer users to build from source was because of how easy it is to forget one little step and screw up the installation, then having to spend time searching out files and folders so that you could (maybe) install a package.

FusionBuild strips all of the possible user level screwups away, and has a simple GUI that aids in installation.

If you haven't checked it out, maybe you should.

---

### Post by Forlong on 2008-12-01
That application you are referring to has been **"put on hold" two month ago**.
Compiz in git is (sometimes drastically) changing **on a daily basis**.
Additionally, it has never been updated, even though the author found "**strange bugs**".

Those problems alone did I found out by reading the author's blog.
So I fail to see how advising to use such software is good sense.

---

### Post by quanumphaze on 2008-12-08
> **SaintDanBert said:**
> Is there a quick and clean way to toggle compiz on and off and preserve one's settings?

I use a tablet PC. Compiz makes a lot of sense most of the time. However, when I swap from landscape to portrait, it leaves compiz confused. Until I can discover how to make compiz play tablet, I could simply toggle off, swap, tablet, swap back, toggle on. Grumble but it would work for now.


thanks in advance,
~~~ Dan 0;-D

There is a nice little script called [Compiz-Switch]("http://forlong.blogage.de/entries/pages/Compiz-Switch") which adds an entry in Applications>Accessories which you can drag to the panel. This is a one click switch back and forth between Metacity and Compiz, no menus like Fusion-Icon.

For the screen change problem, in ccsm>General>"Display Settings tab" there is the Detect Outputs check box. This feature doesn't like screen size changes and seems to only run when Compiz is started. Disable it and add an entry to the Outputs area. If your screen is 1024x768 make it 1024x1024+0+0. eg: I swap between my 1280x800 LVDS and 1280x1024 VGA so it is 1280x1024+0+0. When I want to dual screen (Intel 945GM is limited to maximum 2048x2048 virtual screen size with compiz enabled) I use 2 entries 1280x1024+0+0 and 1024x800+0+1024. And leaving the 2nd entry doesn't appear to have any problems when I just have the LVDS actually using 1280x800+0+0.

---

