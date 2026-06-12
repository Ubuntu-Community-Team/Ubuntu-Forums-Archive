---
title: "Firefox pixels top left of screen"
date: 2008-08-01
forum: General Help
---

### Post by Raine on 2008-08-01
I have noticed lately that whenever I use firefox there seems to be a small box at the top left of the screen. Whenever I close firefox the box goes away and it seems as the more I use firefox the darker the shadow gets which i can only assume it means it opens more and more boxes for some reason. I have tried completely wiping firefox and all settings and it didn't help. Any ideas? I have included a picture 
[IMG]http://i36.tinypic.com/33b1jqp.png[/IMG]

Thanks a bunch.

---

### Post by kostkon on 2008-08-01
An bad extension may cause this. When you say you completely wiped Firefox, do you also mean that you started with a fresh and clean profile?

---

### Post by Raine on 2008-08-01
i completely uninstalled using synaptics and removed the .mozilla directory in the home folder and uninstalled all of my addons. It seems to occur whenever new flash content is loaded.

---

### Post by kostkon on 2008-08-01
> **Raine said:**
> i completely uninstalled using synaptics and removed the .mozilla directory in the home folder and uninstalled all of my addons. It seems to occur whenever new flash content is loaded.
OK. Which flash plugin do you use and how did you install it? Did you try to completely remove it and install it again as you did with Firefox?

---

### Post by Raine on 2008-08-01
I am using flashplugin-nonfree and yes it was removed and reinstalled the same way as firefox

Edit: The problem I am experiencing seems to be a flash problem. I uninstalled the flash plugin and there were no pixel boxes but when it is installed again the boxes come back.

Another Edit: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/210241](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/210241) confirms same problem and at bottom of the page shows a theory as to why. (Has to deal with wmode in flash player 9 and some flash content in flash player 10)

---

