---
title: "Firefox/shiretoko issues"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by rob22941 on 2009-10-08
Well I was interested in upgrading to Firefox 3.5. I am relatively new to Ubuntu, so please excuse my ignorance on the subject lol. I went to mozilla.com did the upgrade and went on with my night (last). I now turn on my laptop and firefox doesn't work. A friend mentioned Shiretoko. Installed that. To make a long story short here's my issue:

I'd like to either upgrade to Firefox 3.5 or keep using 3.0 which is still on my computer but the links on the system tray are now dead. I do know where firefox 3.0 is in the filesystem. If someone can please guide me through replacing dead icons in the system tray I'd appreciate it. 

Also I'd like to remove Shiretoko. In Add/Remove it says "one or more applications depend on firefox 3.5 branding...use the Synaptic package manager. I try to use the synaptic manager and everything is called firefox-3.5 or firefox, no shiretoko listed. Anyone have an idea here? I'm not sure which files to delete. THANKS IN ADVANCE!

Cheers

---

### Post by rob22941 on 2009-10-08
Well I figured out the icon problem, but this led me to another question. In my firefox-3.0.14 folder there are 2 items that puzzle me. 1 labeled firefox and the other firefox-3.0. Both open browsers and I can't figure out the difference between the 2. Any ideas?

---

### Post by jeremyswalker on 2009-10-08
First, what firefox-3.0.14 folder? Where is it located?
Second, you won't find shiretoko in Synaptic. The package is called firefox-3.5.

---

### Post by rob22941 on 2009-10-08
Here is the location of the 3.0 folder:
Filesystem/usr/lib/firefox-3.0.14

I searched firefox-3.5 in synaptic and I get 855 results how do I know what to choose. If I simply delete the firefox-3.5 folder out of the file system will that solve the problem? I don't want to miss any parts.

---

### Post by jeremyswalker on 2009-10-08
What firefox files do you have in /usr/bin? This will be where any executables or symlinks will be.

If you want to uninstall shiretoko, you should uninstall 'firefox-3.5'. When you search for it, search by name only. The package you will select for removal will only say 'firefox-3.5'. Or, just open a terminal (Applications -> Accessories -> Terminal) and enter the following:
```
sudo aptitude remove firefox-3.5
```

---

### Post by rob22941 on 2009-10-08
I salute to you for the correct code to remove shiretoko!

In usr/bin there is a file firefox-3.0, I clicked it asked if I wanted to run in terminal and/or just run. I just ran and it opened the browser. Now should I use this source for my browser or what I'm assuming is the direct source in usr/lib/firefox-3.0. 
What do you think?

---

### Post by jeremyswalker on 2009-10-08
I would just use the path of /usr/bin/firefox-3.0 (or /usr/bin/firefox if that is there). It is likely just a symlink to the one you refer to, but it won't hurt to use it. That is one of the conventional path folders in Linux, too. (/usr/bin that is)

---

### Post by Meow27 on 2009-10-08
i use swift fox and love it..

make sure to use the right architencture tree or ti will work slower

[http://www.getswiftfox.com/](http://www.getswiftfox.com/)

---

### Post by rob22941 on 2009-10-08
jeremyswalker, I think you've solved my problems. Thanks much!

Meow27 I will have to look into *swiftfox*. Thanks.

---

