---
title: "How do I create GTK Theme Graphics?"
date: 2008-10-11
forum: General Help
---

### Post by lancerocke on 2008-10-11
I Googled "How to Create GTK Themes" and could only find instructions on how to manipulate the actual files. What I want to know is what graphics I need to create for a full GTK theme. I want to know the correct sizes for the graphics such as height and width for the windows border and minimize window button.

---

### Post by Genius314 on 2008-10-11
The sizes of images vary by theme. Also, there's no fixed set of images that you need to create... a theme could have a different image for every type of object, or use one image for everything.

My suggestion is to find a full pixmap theme, and start editing the files there.

---

### Post by aschwerin.moses on 2008-10-18
Yes that is one options to edit an existing theme.. but is there any software using which we can create GTK themes... even i would like to know.. let us know...

---

### Post by Genius314 on 2008-10-18
> **aschwerin.moses said:**
> Yes that is one options to edit an existing theme.. but is there any software using which we can create GTK themes... even i would like to know.. let us know...

It's been asked about before, but it's probably never going to happen. The problem is that there are many different engines (pixmap, clearlook, murrine), each with their own method of coding. To make a program that can use all of these would probably just create a mess of code...

I suppose a program could be made just for the pixmaps engine, but it's pretty much easier to just replace the graphics in an existing theme.

---

### Post by aschwerin.moses on 2008-10-18
so how are GTK themes made..

come on guys.. suggest a software or something as how to create gtk themes.. googled it and found none that were helpful..

---

### Post by JustAboutRealJAR on 2008-10-31
I'm also interested in creating GTK themes... any good resources you know of?

---

### Post by Argama on 2008-11-04
[http://glade.gnome.org/index.html](http://glade.gnome.org/index.html) I searched the web for some time. I think this might be good for u guyz.

---

### Post by aschwerin.moses on 2008-12-13
> **Argama said:**
> [http://glade.gnome.org/index.html](http://glade.gnome.org/index.html) I searched the web for some time. I think this might be good for u guyz.
Thank you.. i downloaded it.. when i tried to configure it.. it gives an error 
[I]
No package 'gtk+-2.0' found
No package 'libxml-2.0' found[/I]

tried to install them, none found in repository...


.... if anyones knows another software.. please let us know guys..

---

### Post by IceReaver75 on 2008-12-13
Try installing the libgtk2.0-dev through snynaptic package manager.

that might give you everything you need

One theme i has tried to complie complained about gtk+ 2.0 not being found and i installed that and it didnt complain anymore

the other package you might need is the libxml2-dev package

---

### Post by RuleMaker on 2009-04-12
> **Argama said:**
> [http://glade.gnome.org/index.html](http://glade.gnome.org/index.html) I searched the web for some time. I think this might be good for u guyz.

This is a **GTK user interface designer**, not theme designer.

---

### Post by Keith Hedger on 2009-04-12
Try these two howtos:
[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)
[http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)

don't forget that there are three main parts to a theme, the window styles (title bar, close box etc), the gtk theme (buttons, scroll bars etc), and the icons you see on the desktop and in the toolbars.

I agree with the other posters, the best way to learn is to pull apart someone elses theme, have patience and you'll get there.

---

