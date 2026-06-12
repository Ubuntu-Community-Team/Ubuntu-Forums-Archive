---
title: "complete re-install of X ? (Solved)"
date: 2005-11-30
forum: General Help
---

### Post by stack445 on 2005-11-30
Is there a way to reinstall  X from strach. I've try to install Nvidia Driver following the how-to that i found in the forum. Now, X wont start, and i dont have any error message or log of anything saying why. The install log of the nvidia driver seem's fine. Iv'e try the nvidia installer for the latest driver. When i try to switch back the the nv driver that comes with ubuntu, it's the same thing. I've got a mx440 nvidia card. 

Is there a way to actualy re-install X without to much problem ? 
Like Xreconfig something abracadebra-it's-fixed. :-)

---

### Post by Xian on 2005-11-30
Does [THIS](http://www.ubuntuforums.org/showthread.php?t=97078) thead help?

To reinstall X:

```
$ sudo apt-get install --reinstall x-window-system-core
```

To reconfigure X:

```
$ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by stack445 on 2005-11-30
Thanks, i'me gonna try this when i get home.

Should i actually un-install everything before ?

---

### Post by oofnik on 2005-11-30
I wouldn't, because a whole bunch of things depend on X and you will make yourself crazy trying to re install them.

---

### Post by stack445 on 2005-11-30
THANK YOU VERY VERY MUCH !!! It is working.
I kept a note of those command.

Again, thanks everyone.

---

