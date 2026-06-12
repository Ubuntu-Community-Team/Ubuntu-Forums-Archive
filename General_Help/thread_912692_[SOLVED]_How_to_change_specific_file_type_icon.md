---
title: "[SOLVED] How to change specific file type icon?"
date: 2008-09-07
forum: General Help
---

### Post by Truedream on 2008-09-07
I've a lot of e-books on my computer and most of them are in .lit format. My problem is that the default icons for .lit files is same as the unknown type. How can I change the default icon for .lit files.

Thanks

---

### Post by edge_nabby on 2008-10-15
this is something that i am also curious about.

---

### Post by hellramza on 2008-10-15
I'm also interested in this subject, I could only change icon theme, but there is a way to change specific icons like firefox icon or those .lit files icon isn't it?

---

### Post by loomsen on 2008-10-15
Rightklick on the icon you want to change chosing preferences, the klick on the icon and chose the folder containing your designated icon...

---

### Post by edge_nabby on 2008-10-15
> **loomsen said:**
> Rightklick on the icon you want to change chosing preferences, the klick on the icon and chose the folder containing your designated icon...

This works for only that file. I don't want to change a file's icon. I want to change a file **type**'s icon. (For example, I want to change all rar files' icons.)

---

### Post by loomsen on 2008-10-15
There's a folder called ~/.icons/default

Place your desired icon into it, as *.svg, and soecify which types of files the icon should append to. XML ain't too hard...

---

### Post by edge_nabby on 2008-10-15
> **loomsen said:**
> There's a folder called ~/.icons/default

Place your desired icon into it, as *.svg, and soecify which types of files the icon should append to. XML ain't too hard...

I don't have "default" folder under ~/.icons/ . If I create "default" folder myself, will it work?

Does the image have to be in svg format? If yes, how can I convert a png file to svg?

What is the image file's name supposed to be?

Is that all? Am I done after putting image file? I don't think so.


If you explain it step by step from the beginning, it'll be great. Now, I have a png image for rar file icon. What should I do?

---

### Post by Truedream on 2008-10-16
Sorry about not marking it solved. I actually figured it out by trial and error.

1) In nautilus right click the file type and go to properties.

2) Look for **MIME** type. In my case (.lit) it was **application/x-extension-lit**

3) go to ~/icons folder and than go to mimetype folder in the icon theme that you're using.

4) Create a new icon file (.png, .svg) with a name **application-x-extension-lit.png**.

That did the trick for me. If the mime type already exits simply replace it with a **new icon** but with **same name**.

---

### Post by loomsen on 2008-10-16
Yes, should work if you create it. Do you have any iconsets already installed into that folder?
Like most of the folders and files located in ~ .icons will be parsed by your system in startup, so you don't have to install icons, themes, fonts whatever as superuser, but may also use folders in your $HOME.

If you got a separate partition for your $HOME you'll never use any configs again, which basically is the most work when setting up a new system. So, if you don't have such, I'd take a reinstall into consideration. It should be the last one for a long long time then.

But anyway, if you already extracted icon themes into ~/.icons, you might have noticed a certain common folder structure, which is:

~/.icons/iconthemename/size

[[img]http://img503.imageshack.us/img503/9214/screenshot38mq1.th.png[/img]](http://img503.imageshack.us/img503/9214/screenshot38mq1.png)

So, if you want to use .png you'll have to scale your icons for a whole lot of cases, unless you don't want to suffer from leaks and such.

For example, crystalsvg is such a theme, tho it's called svg. Failed self deception by the guy who made em obv :)

So, I'd recommend getting inkscape and starting right off with svgs.
Besides, it's kind of impressing to see a 4x4 icon strechted to 2400x2400 and still being sharp. 

SVGs you can simply put into a folder called scalable, replacing all of the folders on the shot above. You might as well mix em up, like here:

[[img]http://img413.imageshack.us/img413/2631/screenshot39hi4.th.png[/img]](http://img413.imageshack.us/img413/2631/screenshot39hi4.png)

Further there's also a file in every icon themes parent folder called 
index.theme

This file is the one where the whole thing gets configured (the folders are specified where the icons are located in and so on)


Pretty much self-explainatory... And try and open up *.svg images with a texteditor. Most of them have their configs in them. You won't be able to do so with *.png images...

Nough for the moment? Have fun :)

---

### Post by edge_nabby on 2008-10-16
> **loomsen said:**
> So, if you want to use .png you'll have to scale your icons for a whole lot of cases, unless you don't want to suffer from leaks and such.Actually, I had tried this but it didn't work. I scaled my png file to different resolutions. Then I put every image into its folder like this one: /home/eren/.icons/nuoveXT.2.2/72x72/mimetypes/gnome-mime-application-x-rar.png And then, I restarted my computer (I thought this was necessary). As I said before, it didn't work.

I think what you said (SVG into scalable) and what I had tried (different-sized PNGs into different-size folders) is the same at all. Am I wrong?

---

### Post by loomsen on 2008-10-16
Well, except that you need only one svg for every icon and multiple pngs... The outcome is the same, assuming we won't handle icons larger than 256x256(at least I haven't seen anybody who made larger icons so far)

But, you could as well resize the SVGs as big as the USA for instance, and they'd still look good. Creating icons from png in opposite to this would require creating one large icon, the largest designated, and scaling it down to each specified size. 
SVGs work the other way round. It doesn't matter which size a SVG icon has when created, cause vectors are simply multiplied basic vectors. So there's just no loss of quality even possible. 

While, as I said, you gotta begin with the largest icon when building from png and scale it down to prevent quality losses.

*edit*

Just try it yourself, here are some

the png 24x24 pixels in size, 1,1kb , the svg 744x1052, 3,3kb

You will notice pretty instantly that you're max able to scale the png to sth like 30x30 until it starts splattering into white and black parts. Now try the svg. scale it down to 24x24 too. and see what happens, after you save it and scale it back up to whichever size you like. you could even scale it to 10x10meters or so, it doesn't matter, as it's based on simple arithmetics. Png tho is an absolutely specified format. 

Thats kind of a pretty big difference, one scalable folder replaces all fixed size folders, and even endless more. Cause every vector is just a multiple of another vector, and it's not much of a big thing for a modern PC to $expr X times Y

---

