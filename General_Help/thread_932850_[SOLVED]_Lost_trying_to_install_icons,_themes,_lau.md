---
title: "[SOLVED] Lost trying to install icons, themes, launchers etc."
date: 2008-09-28
forum: General Help
---

### Post by Zachx65 on 2008-09-28
Hey there, I'd like my desktop to look almost exactly like this.. [http://www.gnome-look.org/content/show.php/deviant+desktop+%5Bsept.+08%5D?content=89329]("http://www.gnome-look.org/content/show.php/deviant+desktop+%5Bsept.+08%5D?content=89329"). I started first trying to install the icons. I've googled, etc. getting pages like this [http://ubuntuforums.org/showthread.php?t=3757]("http://ubuntuforums.org/showthread.php?t=3757") and in the last post come up with things like ```
Download the Icon file, double click it to extract the files.
Computer -> Home-> View -> Show Hidden Files
Copy or move the extracted icon folder to the .icons folder
Computer -> Desktop Preferences -> Theme -> Theme Details -> Icon Tab -> Select the Icon package just installed.

```

and that's great but I don't see/have Computer -> Desktop Preferences

Any help?

---

### Post by raul_ on 2008-09-28
System->preferences?

---

### Post by Zachx65 on 2008-09-28
> **raul_ said:**
> System->preferences?

Ok, so I go there and all I see as far as the customization of the look of my desktop is 'Appearance'. I click on that and the dialog has Theme, Background, Fonts. Interface, and Visual Effects. I don't see anything about installing icons. I'm on a fresh install of Hardy Heron btw.

---

### Post by raul_ on 2008-09-28
Quoting you

> **Zachx65 said:**
> (...)
```
Download the Icon file, double click it to extract the files.
Computer -> Home-> View -> Show Hidden Files
**Copy or move the extracted icon folder to the .icons folder**
Computer -> Desktop Preferences -> **Theme -> Theme Details -> Icon Tab -> Select the Icon package just installed**.

```


:popcorn:

---

### Post by Zachx65 on 2008-09-28
I've downloaded and extracted the files, and copied them to .icons. 

The next step apparently is Computer -> Desktop Preferneces

Here is what I see under Places -> Computer

[IMG]http://img150.imageshack.us/img150/9273/screenshotst1.png[/IMG]

No desktop preferences, no theme details.

---

### Post by Hairy_Palms on 2008-09-29
go to System->Preferences->Appearance then click the customise button and go to the icons Tab, then choose the icon theme you want.

---

### Post by raul_ on 2008-09-29
You got as far as Theme, you only needed to keep going. The guy who wrote the guide made a poor and very confusing choice of words.

---

### Post by Hairy_Palms on 2008-09-29
> go to System->Preferences->Appearance then click the customise button and go to the icons Tab, then choose the icon theme you want.

the computer menu item has nothing to do with changing your icon theme, i can only assume that those instructions are for the old SUSE slab menu

---

### Post by Zachx65 on 2008-09-29
Thanks for the help guys! :D

---

### Post by airtonix on 2008-09-29
-double post-

---

### Post by airtonix on 2008-09-29
When installing icons and themes i always use this method : 
1 - download the icon package to the desktop
2 - right click the package(usually a tar.gz) and 'extract here...'
3 - open nautilus 
4 - press ctrl + L
5 - type ~/.icons (press enter). If ~/.icons doesnt exist....create it. make a folder called icons in your home folder and rename it to have a full stop infront of the name
6 - drag n drop the icon folder i extracted in step 2 to this folder.

same goes for themes. (which hold all of the themes for gtk,gtk2, openbox, pkwm, metacity etc)
- download the theme, unpack it and move to ~/.themes.

Here is a screenshot of my icons and themes folder opened : 
[[IMG]http://dl.getdropbox.com/u/180039/2008-09-30-034852_1024x768_scrot.png[/IMG]]("http://dl.getdropbox.com/u/180039/2008-09-30-034852_1024x768_scrot.png")

---

### Post by tyblos on 2008-09-29
thanks for the help airtonix im new in ubuntu .. the i should make a folder in home to themes, emerald, screenlets,icons??? because some of my themes cant apply .. appeear some error ... but i dont extract the files... i save the .tz file and put add theme

but the most of them dont work with this method


what is nautilus ???

---

### Post by lanr01 on 2008-09-30
[QUOTE=airtonix;5876978]When installing icons and themes i always use this method : 
1 - download the icon package to the desktop
2 - right click the package(usually a tar.gz) and 'extract here...'
3 - open nautilus 
4 - press ctrl + L
5 - type ~/.icons (press enter). If ~/.icons doesnt exist....create it. make a folder called icons in your home folder and rename it to have a full stop infront of the name
6 - drag n drop the icon folder i extracted in step 2 to this folder.

same goes for themes. (which hold all of the themes for gtk,gtk2, openbox, pkwm, metacity etc)
- download the theme, unpack it and move to ~/.themes.



 Airtonix, I love your desktop theme and icons... What is that? I would love to use that one... Been looking at a few themes, but that one really looks good...

Thanks,

---

### Post by Zachx65 on 2008-09-30
Hey again. Got the icons and stuff working, and like I said I appreciate the help.

New  questions. I installed screenlets, loaded up a sidebar and threw a few screenlets in there. If for some reason I click the actual sidebar, all the screenlets go underneath it, and then I can't click them. If I have "Keep above" selected they stay on top of everything. Here are before/after clicking side bar pics.

[IMG]http://img88.imageshack.us/img88/2892/screenshotso7.png[/IMG]

[IMG]http://img403.imageshack.us/img403/9086/screenshot1nz9.png[/IMG]

One more: I've got AWN installed, and maybe I misunderstood what it is for. I thought it was a quick program launcher thing. All it does for me is show icons of the programs I currently have open. Also I can't find where to mark it for launching on start-up.

Thanks! :KS

---

### Post by Soupcan on 2008-09-30
It took me a while to understand how to get AWN working correctly. Try this [guide.]("http://ubuntuforums.org/showthread.php?t=762363")

Does anyone know what is in the lower left of the screenshot in the OP? Is it conky?

EDIT: I don't think that guide shows how to have AWN run on startup. There are two ways:
1. Right click AWN and then choose Dock Preferences. Then check off "Automatically start AWN on login." I think this only works if you used the installation instructions from the guide I linked above.
2. Go to System>Preferences>Sessions, click "Add", and then name it Avant Window Navigator, and set the command as avant-window-navigator.

Make sure you don't use both of these at the same time, as it will cause AWN to start multiple times.

AWN is like the bar that Macs have. It can be used to open programs, and it also shows those that are currently open.

---

### Post by Zachx65 on 2008-09-30
Woo, think I finally got it looking decent and functional(I'll see I suppose). Filled in the rest of the sidebar with more screenlets, got launchers working w/ AWN, and got rid of the main panel.

Here's the (semi)final product. Let me know if you guys/gals have any ideas or suggestions. Thanks!

[IMG]http://img515.imageshack.us/img515/2599/screenshot2ag9.png[/IMG]

---

### Post by raul_ on 2008-10-01
Post it on the monthly desktop thread in the community cafe :)

---

