---
title: "Problems with Synaptic"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by mbohacek on 2009-02-02
I am new to this Ubuntu thing and recently change the look of it to look like mac following the directions from:
[http://maketecheasier.com/turn-your-...ard/2008/07/23](http://maketecheasier.com/turn-your-...ard/2008/07/23)

Everything looks great but now when I try to open synaptic package manager it says:

E: The package libgtk2.0-common needs to be reinstalled, but I can't find an archive for it.

E: Internal error opening cache (1). Please report.

Anyone know how to fix this problem?

---

### Post by Slowspeed on 2009-02-02
From the terminal you can type :
apt-cache showpkg libgtk2.0-common

this will verify that you have it listed in your repository and show you the version info. If you see that it is listed then you can type:

sudo apt-get install libgtk2.0-common

---

### Post by taurus on 2009-02-02
[http://ubuntuforums.org/showthread.php?t=1058075](http://ubuntuforums.org/showthread.php?t=1058075)

---

### Post by mbohacek on 2009-02-03
I put those commands in the Terminal and it says:

sudo apt-get --reinstall install libgtk2.0-common
sudo: unable to resolve host bo-laptop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package libgtk2.0-common needs to be reinstalled, but I can't find an archive for it.

What can I do from here?

Thanks for the help!!!

---

### Post by Partyboi2 on 2009-02-03
You could try a force remove of the package[FONT=monospace]
[/FONT]```
sudo dpkg --remove --force-remove-reinstreq libgtk2.0-common
```
then reinstall with
```
sudo apt-get install libgtk2.0-common
```

---

