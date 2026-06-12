---
title: "How do I create a toolbar icon for a folder?"
date: 2008-08-06
forum: General Help
---

### Post by badgaz1 on 2008-08-06
Hi I was wondering how to make an icon for my "Music" folder on Ubuntu in the taskbar like the one I've got on my Windows installation shown here. Probably a simple thing but I can't work it out haha.

[IMG]http://img237.imageshack.us/img237/9899/examplemv2.png[/IMG]

Many thanks

---

### Post by pytheas22 on 2008-08-06
You could create a custom launcher.  Right-click on the Gnome panel and select "Add to panel," then "Custom Application Launcher."  In the "Command" field, enter in this command to open your music folder:
```

nautilus /home/username/Music
```

(obviously, change "username" to your actual username, and if the path to your music folder is different, modify the command to reflect that).

For the other fields fill in whatever you like.  Also you can click on the icon in left of the configuration window to select a different picture.  I'll attach a screenshot as an example.

I think this should work pretty smoothly, but if you run into trouble, please post.

---

### Post by badgaz1 on 2008-08-06
Ahh thank's for the quick reply. The way you described worked but it wasn't quite what I was looking for.

What I am trying to do is make it so that when you click the icon it brings up a list of all the files in the folder like this

[IMG]http://attachments.techguy.org/attachments/110007d1183479393/toolbar-2.jpg[/IMG]

---

### Post by pytheas22 on 2008-08-06
In that case the best suggestion I have is to use the "Drawer" Gnome applet.  You can install your custom music-folder launcher into the drawer, along with launchers to other locations, and when you click the drawer applet, you can select which location to open.  It's not exactly the same, but it's the closest I can think of.

There may well be a better solution, but I don't know.  I don't know what you'd call the thing you have in Windows, so it's hard to come up with good search terms.  Do you know the name of the thing that you installed in Windows to be able to do that?

---

### Post by badgaz1 on 2008-08-06
Ok I will try that thanks for your help.

On Windows you just right click the taskbar - Toolbars - New toolbar then select a folder and it creates one of those.

---

