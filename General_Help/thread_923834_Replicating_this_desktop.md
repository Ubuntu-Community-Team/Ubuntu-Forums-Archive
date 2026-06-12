---
title: "Replicating this desktop"
date: 2008-09-18
forum: General Help
---

### Post by shatteredmindofbob on 2008-09-18
Greetings... [http://www.screenlets.org/images/c/cf/69013-cap.jpg]("http://www.screenlets.org/images/c/cf/69013-cap.jpg")

This is one of the coolest looking Ubuntu desktops I've come across and I'm wondering how to replicate it. I realize it's using a Vista icon pack, but I'm wondering specifically how to get the fancy Ubuntu button in the bottom left corner and how get the "embossed" looking toolbar. 

Thanks.

---

### Post by flatland2d on 2008-09-19
The toolbar looks like the Sidebar Screenlet: [http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28with+docking%29?content=63172](http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28with+docking%29?content=63172)

You must first install screenlets, and I think it has a repository.

---

### Post by shatteredmindofbob on 2008-09-19
> **flatland2d said:**
> The toolbar looks like the Sidebar Screenlet: [http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28with+docking%29?content=63172](http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28with+docking%29?content=63172)

You must first install screenlets, and I think it has a repository.

Sorry, I meant the toolbar on the bottom, with the embossed Ubuntu button and whatnot

---

### Post by anotherdisciple on 2008-09-19
That's actually a gnome panel... I'm not sure how they did it though... look at [www.gnome-look.org](www.gnome-look.org) and see if you can find something like it.

---

### Post by Therion on 2008-09-19
Can't you just adjust the panel properties using the opacity slider to make it transparent?  I'm stuck behind my WinXP office computer right now, but I'm 99% sure that's how I do it.

---

### Post by Therion on 2008-09-19
Yeah, that's how you get the transparency.  Right click on the panel and select Properties/Background tab.  
Select "Solid Color" and use the opacity bar to adjust the transparency.

---

### Post by xj0hnx on 2008-09-20
If you mean the gnome orb button, you need to find the image, try [www.gnome-look.org](www.gnome-look.org). Once you find the image you want to use, save it to you computer. I use a folder for all things like Splashs, Skydomes, icons, wallpaper, icon sets etc, keeps it all organized...

Right click on your panel where you want the "Start menu" and image to be, and add a **Main Menu**. not *Menu Bar*. then you open the terminal and enter...
```
gconf-editor
```

Iin the left pane of Configuration Editor select **apps > panel > objects**, you'll see one or more entries named **object_X** (Object_0, Object_1 etc...). You want to click on them until you find the one that has  the line **object_type   menu-object**. There is a line called custom_icon,** right click > Edit key**, and set the value to the path where you put the file you downloaded, something like this...

/home/john/Pictures/Linux GUI Images/startbutton2.png

Now check the box after use_custom_icon. If you did it right, and are on the correct object, the image will change instantly.

Here's mine...

[img]http://img258.imageshack.us/img258/3865/menupicfp4.png[/img]

here's a link to the DL for it...

[http://www.gnome-look.org/content/show.php/Ubuntu+Startbutton?content=81105](http://www.gnome-look.org/content/show.php/Ubuntu+Startbutton?content=81105)

Just do a search for start in icons, you'll find some others.

---

### Post by alexgre on 2008-09-20
Yeh some nice desktops above.

I guess i'm all for the minimalist/performance warrior. With so many sessions and apps open.

Nice though!

---

