---
title: "installing  video player"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by asliyanage on 2009-07-03
i have installed ubuntu 9.04 .there is a default movie player in Application->Sound & Video->Movie Player.but when i tried to play avi file it says
"
The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.
"
how do i installed this plugin.actually i am new to linux world.can anyone tell me what are the steps i need to follow?

---

### Post by oldos2er on 2009-07-03
You can let the program search for and install the proper codec; or you can manually install the package ubuntu-restricted-extras, which contains codecs, Java, and Flash. Open a terminal and run
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by NorthwesternWind on 2009-07-03
I'm completely new to linux/ubuntu and I apologize for asking here but I didn't even really know what to search for to post in the correct thread.  
I was trying to install playonlinux and something failed when I tried.  Now I get :

"
E: Type '--17:32:52--' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: Couldn't read list of package sources
"
when I try to do anything like type "sudo apt-get update" or trying to install vlc player.  I think I then made things worse trying to repair the sources.list file from another thread and now I'm stuck.  Please if you could just even direct me to the right place it would be so greatly appreciated.

---

