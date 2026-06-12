---
title: "XMMS installed, now how to start?!?"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by chirag64 on 2009-06-09
Hello, i just downloaded and installed this package of xmms

[http://www.pvv.ntnu.no/~knuta/xmms/jaunty/xmms_1.2.11-1_i386.deb](http://www.pvv.ntnu.no/~knuta/xmms/jaunty/xmms_1.2.11-1_i386.deb)

but after installing, how do i start it?!? It does not appear Applications > Sound & Video. Nor do i have the option of playing a song by right clicking it and opening it with xmms.

I even tried

> chirag@chirag-desktop:~$ sudo apt-get install xmms


but it says

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xmms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by blackxored on 2009-06-09
Once upon a time: :D

```

sudo aptitude install xmm2
sudo aptitude install xmm2-plugin-all
sudo aptitude install gxmms2


```

Then start xmms2d and you're done.

---

### Post by chirag64 on 2009-06-09
```
chirag@chirag-desktop:~$ sudo aptitude install xmm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "xmm2"
Couldn't find any package whose name or description matched "xmm2"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

---

### Post by dannybuntu on 2009-06-09
xmms or xmms2 ????

You're having problems because you typed xmm2. 

Do not forget the 's'

Now once you have it installed, you have to navigate to your music directory and execute:

$ xmms2 add name.of.song.mp3

Then play it 

$ xmms2 play

Check out my signature.

Now if you want a gui that looks like winamp I suggest that you install 

$ sudo apt-get install audacious

Note: not audacity. audacity is a different program. I hope I helped you.

---

### Post by chirag64 on 2009-06-09
It did appear in Applications > Sound & Video

But when i opened gxmms2, it says gxmms2d is not running

---

### Post by Mark Phelps on 2009-06-10
xmm2 is not xmms.  It's possible that installing the first hosed up the other somehow.

Run the "locate xmms" command and see where it is on your drive.

Mine is in /usr/bin with a hidden .xmms directory in my home folder.

Plus, there's an icon under Applications --> Sound and Video.

If you run "xmms" from a terminal, it should pop open the app with the default skin.

---

### Post by chirag64 on 2009-06-10
I tried starting it by typing xmms in the terminal.

It started, but it says

> Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Message: device: default

After I click play button, a dialog box opens with no text on it.

---

### Post by blackxored on 2009-06-10
You've propably missed things up. What I've actually recommended was xmms2, and in  any version you need to install the daemon and run it properly. 
After that, you could choose from a plethora of guis available or the command-line client. 
starting xmms2d by locating it, and then run it without options.

---

### Post by chirag64 on 2009-06-11
> starting xmms2d by locating it, and then run it without options.

Now how do i do that?!? :|

---

