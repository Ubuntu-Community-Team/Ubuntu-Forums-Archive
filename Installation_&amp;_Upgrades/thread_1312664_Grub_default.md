---
title: "Grub default"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by 2handband on 2009-11-03
I've been running Mint 7 and thought I would give Kubuntu 9.10 a try on another partition. The install went without incident but naturally Kubuntu took control of the grub menu and now is the default OS on bootup. For the time being I'm still using Mint for most things and would like to switch it back over so Mint is the default OS. How can I do this? Thanks!

---

### Post by sliketymo on 2009-11-03
I think you can edit  /etc/default/grub.This kind of takes the place of  the grub/menu.lst in grub2.

---

### Post by 2handband on 2009-11-03
I followed that link and have to admit that the instructions there are way over my head.

---

### Post by sliketymo on 2009-11-03
Run your terminal,and edit your  /etc/default/grub  file.

---

### Post by drs305 on 2009-11-03
If this was a clean Kubuntu install, you now have Grub 2 and the file system has completely changed. There are several good resources for learning about Grub 2:

The Ubuntu community doc: [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

And an extensive post by a Kubuntu user, Qqmike:
[http://kubuntuforums.net/forums/index.php?topic=3106368.0]("http://kubuntuforums.net/forums/index.php?topic=3106368.0")

By far the easiest way to change the default OS is to use StartUp-Manager, a GUI grub tweaker:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

And finally, this also covers how to change the default kernel/OS:
[GRUB 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

---

### Post by 2handband on 2009-11-03
Where can I get my hands on this startup manager? It doesn't seem to be in the repositories... neither does much else. Where the heck is Synaptic? I don't think I like kpackage. Anyway I tried to install it via command line and it says package not found.

---

### Post by drs305 on 2009-11-03
> **2handband said:**
> Where can I get my hands on this startup manager? It doesn't seem to be in the repositories... neither does much else. Where the heck is Synaptic? I don't think I like kpackage. Anyway I tried to install it via command line and it says package not found.

Forgot you were using Kubuntu. StartUp-Manager is in the "universe" repositories. Since you say there isn't much in your repositories, there is a good chance it isn't enabled. I don't run Kubuntu but I would expect you can open adept as root and enable the "universe" repository.

Once you get the repository enabled, you can get StartUp-Manager with:
```

sudo apt-get update
sudo apt-get install startupmanager

```

While StartUp-Manager is a great tool, here is a quick way to change your default menu properties. Open /etc/default/grub with a root text editor.
Find the line:  DEFAULT=0

Run this to determine the current menu items:
```

grep menuentry /boot/grub/grub.cfg

```

The first entry is counted as 0, the second is 1, etc. Count (from 0) and determine the number for Mint. Change the "DEFAULT=" number to match the Mint number. 
Save the file, then run:
```

sudo update-grub

```

---

### Post by 2handband on 2009-11-03
Okay, got the repositories installed and found the program. Whew! This experiment may prove to be very short-lived... so far I'm not having a positive KDE experience. Thanks to everyone who responded.

---

