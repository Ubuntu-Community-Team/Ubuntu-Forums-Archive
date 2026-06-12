---
title: "desktops and wallpaper"
date: 2008-10-21
forum: General Help
---

### Post by zero7404 on 2008-10-21
i am using compiz effects in gnome, i'd like to know if it's possible to use a different wallpaper on each of the 4 desktops i have set up ?

---

### Post by loomsen on 2008-10-21
Yes, click on Customizaments in my sig.

Oh well, [Part I actually](http://ubuntuforums.org/showpost.php?p=5691394&postcount=39)

---

### Post by zero7404 on 2008-10-21
thanks for posting, but this was no real help to me.

one of the things i don't like about this forum is you ask for help and someone points you to a thread that you need to read 3 or more pages in addition to other multi-page threads to figure out how to do something.

so there's no option in the graphical compiz config that will allow me to change the desktop wallpaper for individual desktops, that's all i needed to know.

---

### Post by patryk77 on 2008-10-21
[http://wallpapoz.akbarhome.com/index.html](http://wallpapoz.akbarhome.com/index.html)

I never tried it, but this sounds like it does what you want.

You can get an easy to install .deb here:
[http://www.getdeb.net/app/Wallpapoz](http://www.getdeb.net/app/Wallpapoz)

(Might be in Synpaptic too, didn't check)

---

### Post by Victormd on 2008-10-21
> **zero7404 said:**
> so there's no option in the graphical compiz config that will allow me to change the desktop wallpaper for individual desktops, that's all i needed to know.

No. You can install compiz-git and I believe that has a plugin (still in development and quite buggy) that allows you to do this... The only other alternative is [this]("http://ubuntuforums.org/showpost.php?p=5691394&postcount=39"). There are other similar posts but all have the same principle...

---

### Post by Account1 on 2008-10-21
I bought that exact computer yesterday.

---

### Post by loomsen on 2008-10-21
> **zero7404 said:**
> 
so there's no option in the graphical compiz config that will allow me to change the desktop wallpaper for individual desktops, that's all i needed to know.

?

So, you're like asking but actually don't want help?

Alright, nope, there's not. (There is the wallpaper plugin, but I guess that must be something of that 3 page stuff... And, btw, the wallpaper plugin isn't in compiz just since yesterday...)

---

### Post by cl0ckwork on 2008-10-21
> **zero7404 said:**
> thanks for posting, but this was no real help to me.

one of the things i don't like about this forum is you ask for help and someone points you to a thread that you need to read 3 or more pages in addition to other multi-page threads to figure out how to do something.

so there's no option in the graphical compiz config that will allow me to change the desktop wallpaper for individual desktops, that's all i needed to know.

true, but then again most of the stuff in the forums is in CLI to help new users get accustomed to linux and Ubuntu.

the thread loomsen pointed out is very descriptive but it does take work to get it to work right.

basically what he says is that you need to replace the default gnome file manager (nautilus) and use a different one, because it prevents different wallpapers on each desktop.

hope that clears some things up

---

### Post by patryk77 on 2008-10-21
Or you can just try the link I posted before, because Wallpapoz claims to allow you to do just that, and it says it works in Compiz too...

Seems like the easiest solution to me

---

### Post by loomsen on 2008-10-21
> **patryk77 said:**
> Or you can just try the link I posted before, because Wallpapoz claims to allow you to do just that, and it says it works in Compiz too...

Seems like the easiest solution to me

It doesn't actually... Been searching a tool doing that for quite a while now, cause, the problem is... Conky is able to run without an own window in the meanwhile. It had to because of nautilus. Now, they patched it, but actually it's just the other way round. Conky isn't able to print to any other window than nautilus. 

Wallpapoz is just sth like a workaround. It just draws a layer over nautilus, which, however is redrawn when you change your desktop. So it's just not responsible enough to use it for everyday work. Imho. I use to switch my desks a lot, and this is (well, it was more likely) just not a solution.

---

### Post by cor2y on 2008-10-21
Intrepid ships with the latest compiz-fusion which has the stable new wallpaper plugin which allows you to have a different wallpaper on each workspace or if you are leet to have one massive wallpaper stretched across all workspaces.
The downside is 
1) you will have to disable nautilus icons/launchers on the desktop via gconf (apps->nautilus->preferences->show desktop) to see the wallpapers
2) Conky works wonky on it aka it doesn't display correctly if show desktop is disabled.

But other than those two it works well you still have your panels with their lauchers but you won't be able to do anything on the desktop itself aka right click etc. Universal Applets/screenlets/Awn/Cairo Dock will work on the desktop though.

---

### Post by loomsen on 2008-10-21
Yep, true, so no gain at all in the end... Got intrepid and compiz git. 

Plus I'm really fed up patching nautilus over and over again. Sigh.

Telling conky which window to draw to didn't work, nor did appending a window-ID to compiz. 
So it's still either conky & nautilus, or compiz, different wallpapers, but a conky which will hardly melt with your desktop.

---

### Post by cor2y on 2008-10-23
I got Conky to work in intrepid with the wallpaper plugin.
What i had to do was set a background color for the conky script, add class=Conky to the following Compiz Filters Opacity, Brightness and Saturation Filter, Windows Rules and in there class=Conky is set for Below, Sticky, Non Moveable Window, Non Resizable Window, Non Minimizable Window, Non Maximizable Window,  Non Closable Window, and No Focus in Compiz Config Settings Manager.
That seems to have worked for Conky The Opacity Brightness and Saturation Filter is for setting up how transparent the Conky window/windows will be since it won't work correctly (tranparency) otherwise in compiz.

---

### Post by Solaris3k1 on 2008-12-03
cor2y... can you post your conkyrc file so we can see what you did?  thanks!

---

