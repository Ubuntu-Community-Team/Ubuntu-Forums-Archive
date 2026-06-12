---
title: "Can not install Falsh"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by drdave69 on 2009-04-10
I can not install the flash plugin, I get this error: error wrong architecture 'i386'

---

### Post by RedSingularity on 2009-04-10
So your using a 64 bit linux install?

---

### Post by lisati on 2009-04-10
> **drdave69 said:**
> I can not install the flash plugin, I get this error: error wrong architecture 'i386'

You might find it easier to use the macromedia flash plugin that can be installed through the add/remove software menu item.

---

### Post by RedSingularity on 2009-04-10
I tryed that one originally and it didnt work for my web browser.  If that fails follow [THESE](http://ubuntuforums.org/showthread.php?t=1102050) steps to set it up.

---

### Post by RedSingularity on 2009-04-10
Im sorry ignore that post.....its for java not flash.

---

### Post by drdave69 on 2009-04-10
i chose the adobe flash version for ubuntu
i already have the macromedia flash plugin
I can view videos on youtube but not on my site here is an example:
[http://wittyvideos.net/play.php?vid=450](http://wittyvideos.net/play.php?vid=450)
When I login to windows I can view the videos, so I know the site is functioning properly.

---

### Post by drdave69 on 2009-04-10
Still can not install flash.
Any help would be greatly appreciated.

---

### Post by Cerberus108 on 2009-04-10
Try to open the terminal (click on Applications/Accessories/Terminal) and to put in it

```
sudo apt-get install flashplugin-nonfree
```

You will be prompted to enter your user password, and maybe to confirm you want to install those packages. After it has finished installing, close any opened firefox window, and try re-open it. Let us know what happens :) (it worked for me on my amd64 system)

---

### Post by adalal on 2009-04-10
Try downloading and unarchiving [this file]("http://drop.io/download/49df8595/8a806ec99f4f390a86d696142a18867a7dc27334/065036c0-0823-012c-19da-f674f15b993a/272d6250-0825-012c-18ac-f760f9972690/libflashplayer.so.tar/libflashplayer_so_tar.tar") to /home/<user>/.mozilla/plugins/ and then try going on any flash enabled pages!

Let me know if it works... This is the flash plugin by Adobe and not the plugin from the repository!

The file is available at this drop: [http://drop.io/0yhmf3n]("http://drop.io/0yhmf3n")

---

### Post by Peasantoid on 2009-04-10
The Flash 10 alpha (64-bit) works great for me.
Download: [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
Instructions: [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

---

### Post by adalal on 2009-04-10
Just an update, I saw the Adobe Flash installation on the repository (multiverse)

```
sudo apt-get install flashplugin-installer
```

The description states that this will download the official Adobe plugin from the website...

---

### Post by drdave69 on 2009-04-12
Fixed problem....had a bad installation from Wubi. Caused multiple errors.
Did a clean install on own drive & most everything seems to work now.
Thanks for all the help :)
Dave

---

