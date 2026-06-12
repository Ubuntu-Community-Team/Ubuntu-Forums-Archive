---
title: "Installing Kubuntu over Ubuntu"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by Alkser on 2009-11-10
Hello there guys,
I recently got Kubuntu 9.10 that I ordered. 
Right now I'm dual booting windows xp with ubuntu.
 
So i searched around the forums a bit on how to install Kubuntu over Ubuntu. 
 
I read somewhere that when I get to partitioning phase to select manual partition. Ok I did that but I don't know which one to choose since there's no "/" or w/e I need to do with it.
 
Any help would be appreciated.

---

### Post by Mighty_Joe on 2009-11-10
If you select manual partitioning, GParted will not identify the existing root directory.  Look for one formatted ext3 or ext4. That will be the Linux partition. The existing Windows partition should be formatted NTFS. You will likely have a smaller swap partition as well.

---

### Post by kio_http on 2009-11-10
Manual partitioning in the installer. You go in options where it will ask you mount point of partition you tpe "/" without quotes and install.

---

### Post by snowpine on 2009-11-10
There is a *much* easier way:

From your existing Ubuntu install, open a terminal and type:

```
sudo apt-get install kubuntu-desktop
```

Log out, and select Sessions->KDE from the login screen.

If you want to remove Gnome, read here: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by Alkser on 2009-11-11
Thanks guys, I've installed it without any problems :)
 
Added SOLVED tag

---

### Post by kio_http on 2009-11-11
Also this is already discussed in the FAQ on kubuntu.org

---

