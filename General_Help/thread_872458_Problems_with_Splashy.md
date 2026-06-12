---
title: "Problems with Splashy"
date: 2008-07-28
forum: General Help
---

### Post by quantum-positron on 2008-07-28
I have installed splashy and followed [http://splashy.alioth.debian.org/wiki/](http://splashy.alioth.debian.org/wiki/) theme installation and FAQ my problem is the theme works on shutdown and reboot however on start up it shows the default "Tux" theme not the theme I installed. I have also followed this post [http://ubuntuforums.org/showthread.php?t=369912](http://ubuntuforums.org/showthread.php?t=369912) and copied the contents of my installed theme into the default theme folder to no avail. any help would be much appreciated.

---

### Post by jombeewoof on 2008-07-28
I've noticed the exact same bug. 
I also noticed that if you change to one of the other "official" themes. The startup screen will update like it should. If you then change to a custom theme the shutdown screen changes but startup does not. 

I have copied an "official" theme (debian-cubism) which only has 1 image. background.png and copied over that with a custom background.png and again same thing works on shutdown, not on startup.

I compressed, deleted and reinstalled the modified debian-cubism. Exact same issue, at this point the original background.png didn't even exist in that directory anymore.

I then renamed the theme, installed it and set it as my theme. Again I'm seeing the debian-cubism image at startup, but my custom image at shutdown. 

this is the extent of what I was able to do before something shiny caught my eye and I started doing something else.

Anyone have any ideas beyond what I've done?

---

