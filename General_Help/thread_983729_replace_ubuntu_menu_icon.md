---
title: "replace ubuntu menu icon"
date: 2008-11-16
forum: General Help
---

### Post by Snappo on 2008-11-16
I want to replace the default ubuntu menu with this [icon]("http://www.gnome-look.org/CONTENT/content-pre1/92541-1.png"). :)

8.10

---

### Post by cdtech on 2008-11-16
Use the configuration editor
```

sudo apt-get install gconf-editor
sudo gconf-editor

```
From there go to apps > panel > objects.

You will see a series of folders named object_0, object_1, etc. find which of those objects is your menu. 

I found mine to be named menu_bar_screen. Click the checkbox for "use_custom_icon", then right-click on "custom_icon", select "Edit key..." and enter the full path to your chosen icon. (For me: /usr/share/pixmaps/menu.png)

I also had to change the object_type from menu-bar to menu-object for the icon to work....

Then just " killall gnome-panel" to restart the panel with the changes.

---

### Post by Snappo on 2008-11-16
It seems i'm not able to edit the path. 

[IMG]http://www.tehupload.com/uploads/4869ca03f016801Screenshot-1.png[/IMG]

---

### Post by CatKiller on 2008-11-16
use_custom_icon is a true/false setting to say whether the icon specified in custom_icon is used. So set that one to True, and specify the path in the custom_icon field.

How can you read anything with that theme? Black on dark brown looks pretty much invisible to me...

---

### Post by drs305 on 2008-11-16
I would recommend the gconf method if it works for you, but here is alternative that I posted for Hardy. The locations are the same in Intrepid.

[http://ubuntuforums.org/showthread.php?t=932431&highlight=menu+icon#3]("http://ubuntuforums.org/showthread.php?t=932431&highlight=menu+icon#3")

---

### Post by binbash on 2008-11-16
you can do that easly with ubuntu-tweak

---

### Post by Snappo on 2008-11-16
> **CatKiller said:**
> use_custom_icon is a true/false setting to say whether the icon specified in custom_icon is used. So set that one to True, and specify the path in the custom_icon field.

How can you read anything with that theme? Black on dark brown looks pretty much invisible to me...

I'm not here to discuss my theme :)

> **drs305 said:**
> I would recommend the gconf method if it works for you, but here is alternative that I posted for Hardy. The locations are the same in Intrepid.

[http://ubuntuforums.org/showthread.php?t=932431&highlight=menu+icon#3]("http://ubuntuforums.org/showthread.php?t=932431&highlight=menu+icon#3")

I will read upon it now thanks. 

> **binbash said:**
> you can do that easly with ubuntu-tweak

It seems it's missing 
William@Snappo-Linux:~$ sudo apt-get install ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-tweak

---

Never mind, I found the website.

---

