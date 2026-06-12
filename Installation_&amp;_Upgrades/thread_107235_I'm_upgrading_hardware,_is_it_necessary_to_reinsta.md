---
title: "I'm upgrading hardware, is it necessary to reinstall?"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by dahli.llama on 2005-12-22
I am going to be upgrading my PC with a new ASRock motherboard (with built in ethernet), an Athlon64 3200+ and another .5Gb of RAM.  My video card and disk drives will remain the same.

I usually would just do a complete re-install, but I'm wondering if it would be possibly to just install the necessary drivers and such and keep my existing system.  I assume I wouldn't be able to just upgrade to a 64bit kernel, because the non-64bit stuff wouldn't work, but mostly I want to keep the current setup as useable as possible since I will most likely be installing the 64bit version on a separate drive and I would like to have a working system to troubleshoot with if something goes wrong.

Any thoughts or suggestions would be appreciated.

---

### Post by waster on 2005-12-23
I'm not sure hotplug is up to this. I'd go for a reinstall. What Ubuntu misses is a way to magically record what packages were installed, and to reinstall them. I think there is a hacky way using dpkg on the command line. Otherwise, you can just copy across your home directory, and you're away.

---

### Post by tseliot on 2005-12-23
If you don't install Ubuntu 64bit and keep Ubuntu 32 everything should work. The kernel is the same as well as the modules which come with it by default.

Why do you want to use AMD64 version of Ubuntu? You know you can use Ubuntu 32bit with a AMD64 processor, don't you?

---

### Post by Cpt. Charisma on 2005-12-23
In my experience, Linux handles hardware changes *much* better than Windows.  You should be able to change all of that and more without reinstalling.  The only problem you might run in to is if you try to upgrade from the 32 bit version of Ubuntu to the 64 bit version.  It should work fine, but there are a lot of places where it could break something.

---

### Post by herot on 2006-01-20
i would like some more information on this subject...

lets assume i want to upgrade my motherboard and video card and have decided to reinstall rather than just wing it.  i want to keep all my custom settings in gnome, the pkgs that i have installed, as well as my aliases that i put into my .bashrc file, downloaded files and directories i may have created... 

what is the simplest way to backup all of this... and what would the steps be to get it back into the new installation?

actually i found a good thread for this subject here:
[http://www.ubuntuforums.org/showthread.php?t=80790](http://www.ubuntuforums.org/showthread.php?t=80790)
and here:
[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

---

