---
title: "Edit Samba Ubuntu Server (HH)"
date: 2008-08-06
forum: General Help
---

### Post by gpb on 2008-08-06
What are the exact commands to edit the Samba/smb.conf file on Ubuntu Server  8.0(HH) box???? I just want to create a directory to write and save stuff to from Windows. Does Ubuntu server 8.0 have a GUI???

Thanx

---

### Post by geirha on 2008-08-06
It does not have a GUI. To edit the file, do
```
sudo nano /etc/samba/smb.conf
```
nano displays some actions you can do at the bottom. Amongst others it has "^X Exit"
That means hit Ctrl-x to exit (it will then ask you if you want to save).

If you prefer a different editor, just replace nano in the commandline above with your favorite.

---

### Post by jerome1232 on 2008-08-06
To start *most* config files are located in /etc that's the first place to look for those. In my example I'll use nano as the text editor. It's kind of the default one, I prefer vim though.

To find that file I just typed sudo nano /etc/s then I hit tab twice it shows me everything that starts with 's' I see samba so I just typed am then hit tab again and it completes the name, then I just hit tab twice again and see a few files, one is smb.conf, that's our config file.

```
sudo nano /etc/samba/smb.conf
```

Now I prefer to run my server gui-less, as I just ssh into it from my desktop to control it, if you really want a gui you can run one of the following, I'd really recomend sticking to CLI only though.

```
sudo aptitude install ubuntu-desktop  # this is a standard gnome install
sudo aptitude install kubuntu-destkop  # kde
sudo aptitude install xubuntu # xfce
```

There are other more minimal gui's like flux-box, open-box, icewm; which if you want a gui one of those might be better suited (they don't hog resources as much)

---

### Post by Nepherte on 2008-08-06
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

