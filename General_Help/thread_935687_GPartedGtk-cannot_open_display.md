---
title: "GParted:Gtk-cannot open display"
date: 2008-10-01
forum: General Help
---

### Post by HousieMousie2 on 2008-10-01
I am getting the same error from Gparted, whether using the LiveCD or the System Rescue CD...

> Gtk - Warning **: cannot open display

Anyone care to chime in on this one?  This passed ridiculous a couple of days ago and is headed off into Twilight Zone turf.

Trying to get the sound card to work, somewhere along the way Hardy blew up, installed Hardy on a new hard drive, but install CD would crash if I chose Manual partition or the second Guided, I ran checks on the CD... now need to create a /home partition, to copy my old /home directory and data to the new hard drive... then I can go back to trying to fix the sound (different sound card now though.)  After that I get to try to tackle the whole XP+SATA+GeForce 9600GT catastrophe... before the return option expires with NewEgg.

I need a drink. lol

Anyway...  anyone know how to solve the Gparted/Gtk error problem so I can take one step closer to enjoying my computer? lol  Or know how to properly copy the /home dir so that it can be used by the system?

Thanks for reading and remember, no matter where you're at, there you are.

---

### Post by modmadmike on 2008-10-01
have you tried the No GUI installer

---

### Post by HousieMousie2 on 2008-10-02
No, I have not tried that... wouldn't know what to do with it either.

Parted seems to work fine, I just don't know how to get it to do what I want without the GUI... Start/End/Huh?


Is it possible that GParted is getting hung up over the video card?  It is the only video output I have in this machine... it sees it as a PCI Express bridge, knows it's name, but that's about it, the remaining entries for it say Unknown.

I have no idea how literally to take that Gtk error message.

---

### Post by argotechnica on 2008-12-08
If you're using Kubuntu, try the following:

```
kdesudo gparted
```

Here's what I found:
[LIST=1]
[*]```
gparted
``` GParted would find the Gtk libraries, but fail to automatically attempt to elevate its privileges. (It would complain about requiring root privileges, but it wouldn't load a "type yr password" window.)
[*]```
sudo gparted
``` GParted had the privileges it needed but was no longer able to find the Gtk libraries.
[/LIST]

By instructing GParted to run with KdeSudo, it was able to both find the Gtk libraries and run with elevated privileges.

---

