---
title: "Different backgrounds on cube?"
date: 2008-11-13
forum: General Help
---

### Post by Amorget on 2008-11-13
I found this tutorial:

[http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/](http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/)

However, losing my dekstop... well, doesn't sit well.  I am using 8.04.

Is there some other way?

Thanks,
Douglas

---

### Post by binbash on 2008-11-13
As far as i know there is no way except that.

---

### Post by Amorget on 2008-11-13
Doh, okay :(

---

### Post by ellalan on 2008-11-18
Hi
I have compiz 0.7.8 in my Intrepid but I do not have Background Image in my Desktop plugin under Appearance. Any help appreciated.

---

### Post by ellalan on 2008-11-18
I am glad that I have found the solution to my problem, its very easy to achieve different wall papers on different work tops.
I have ticked wallpapers plugin in ccsm,then in nautilus under preferences unticked show desktop. The result attached.

---

### Post by binbash on 2008-11-18
> **ellalan said:**
> Hi
I have compiz 0.7.8 in my Intrepid but I do not have Background Image in my Desktop plugin under Appearance. Any help appreciated.

you can compile it with git.It is very easy just go to compiz-fusion forums and navigate to howtos

---

### Post by ellalan on 2008-11-18
Thanx binbash, I have actually found an easy solution with wallpaper plugin.

---

### Post by cptnfool on 2008-12-28
Hi, i am using the wallpapers plugin to use different pictures on each side of the cube, but i seem to be covering it with the gnome desktop wallpaper.  i can see the four different pictures as my computer first logs in, but after it has a few seconds more, it loads the default background picture that is set by right click on the desktop and click 'change desktop background' in the context menu.  
any help appreciated

---

### Post by blampars on 2009-01-02
> **cptnfool said:**
> Hi, i am using the wallpapers plugin to use different pictures on each side of the cube, but i seem to be covering it with the gnome desktop wallpaper.  i can see the four different pictures as my computer first logs in, but after it has a few seconds more, it loads the default background picture that is set by right click on the desktop and click 'change desktop background' in the context menu.  
any help appreciated

press alt-f2
type gconf-editor
click run

goto apps
goto nautilus
goto subfolder - preferences
uncheck box - show desktop
close gconf-editor

check your workspaces :)

---

### Post by Mgiacchetti on 2009-04-07
> **blampars said:**
> press alt-f2
type gconf-editor
click run

goto apps
goto nautilus
goto subfolder - preferences
uncheck box - show desktop
close gconf-editor

check your workspaces :)


again, this makes the icons disappear (as far as I remember, was hardy when I tried it last)

So.. the question still remains, can we have different backgrounds WITH our icons?

extra credit:
Can we have totally seperated workspaces with their own icons and backgrounds??

---

