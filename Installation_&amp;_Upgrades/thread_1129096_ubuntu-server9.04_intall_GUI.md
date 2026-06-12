---
title: "ubuntu-server9.04 intall GUI"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by sheepjxx on 2009-04-18
I want install ubuntu-server9.04 to my lop-top and I only have the wireless connection.
I can't configure the wireless without GUI.

How to install GUI ?

I change the /etc/apt/sourcelist , add the cdrom to source
mount cdrom 
**sudo mount /dev/cdrom /media/cdrom0/**
and when I type 
**sudo apt-get install ubuntu-desktop**
 
still couldn't find the path.
Is the desktop package included in the 9.04 disk?

---

### Post by shabazzk on 2009-04-18
I'm no expert, but I believe the server edition doe NOT com with GUI. So trying to install GUI from a server edition CD may be a moot point. 

Since you configured the wireless connection, and assuming it's setup correctly and connected to the Internet. If you add the correct sources, then running that command should simply download and install GUI tools. Then type startx or reboot the puter after it is done.:popcorn:

Hey! This is both our first cup of Ubuntu.

---

### Post by sheepjxx on 2009-04-19
The question is I only have wireless Internet connection and I can't configure this in terminal.

---

### Post by rmayer32 on 2009-04-19
Don't know about the wireless, but to for the gui, sudo apt-get install ubuntu-desktop

---

### Post by sheepjxx on 2009-04-19
TO make it clear, I don't have internet access.
so 
**sodu apt-get install ubuntu-desktop **
doesn't work.

Is there any method that I can install from CDROM.
Is the server Edition of CD including the ubuntu-desktop package?
Can I use desktop Edition to install the ubuntu-desktop?

---

### Post by zvacet on 2009-04-19
These are possible solutions for configuring wireless with CLI:

[http://crunchbang.org/archives/2007/12/18/configure-wireless-on-the-command-line/]("http://crunchbang.org/archives/2007/12/18/configure-wireless-on-the-command-line/")

[http://ubuntuforums.org/showthread.php?t=571188]("http://ubuntuforums.org/showthread.php?t=571188")

[http://ubuntuforums.org/archive/index.php/t-956761.html]("http://ubuntuforums.org/archive/index.php/t-956761.html")

When you sort that then 

```
sudo apt-get install ubuntu-desktop gdm
```

---

