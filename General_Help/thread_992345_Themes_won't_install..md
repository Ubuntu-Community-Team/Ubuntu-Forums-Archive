---
title: "Themes won't install."
date: 2008-11-24
forum: General Help
---

### Post by wtfitsRICK on 2008-11-24
I'm a bit curious as to why some of the themes I've been downloading won't install.  I got a few to work with the drag/drop method.  But now, I can't seem to get them to work right.  Here are a couple themes I'm wanting to install:

[http://twigsby.deviantart.com/art/Scaled-Black-Murrina-59093093](http://twigsby.deviantart.com/art/Scaled-Black-Murrina-59093093)
[http://twigsby.deviantart.com/art/Black-29001499](http://twigsby.deviantart.com/art/Black-29001499)

Any help?  I'm really not sure what the problem is.  Then again, I'm fairly new to Ubuntu.  Thanks and all that.  :D

---

### Post by Ivo Moelans on 2008-11-24
They are in the wrong compression format (extension .gz) and, when unpacked, they produce a hidden file.

This will probably help:
example: **Scaled_Black___Murrina_by_twigsby.gz**
1) download or transfer this file to your home directory (not the Desktop)
2) unpack the theme: right-click on the file and click on **Extract Here** in the context menu.
3) press **Control + h**. This makes hidden files visible. You should now see a file **.fr.18010.0.MurrinaScaled.tar**
4) repeat step 2 on this file. You should now see a directory **MurrinaScaled**
5) right-click on this directory and click on **Create Archive...** A window will open and suggest a name and an extension. Make sure the extension is **.tar.bz2**. You should now get **MurrinaScaled.tar.bz2**
6) Open **Appearance Preferences** (*System&#8594;Preferences&#8594;Appearance*). MurrinaScaled.tar.bz2 can simply be dragged into this window and the theme will install.

Maybe there is a reason why the author has made this so complicated and confusing, but if there is I don't know it. Most of the themes on [http://www.gnome-look.org/]("http://www.gnome-look.org/") are easier to install.

Hope this helps.

---

### Post by wtfitsRICK on 2008-11-24
Thanks so much.
That works just fine.  :D

---

