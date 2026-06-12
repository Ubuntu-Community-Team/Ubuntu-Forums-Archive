---
title: "envy help needed"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by woop on 2009-05-16
following the steps here

[http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver+hardy]("http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver+hardy")

and this happens when I run the second command
anthony@anthony-desktop:~$ sudo apt-get install envyng-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libconvert-binhex-perl libsoap-lite-perl libuser-perl libmime-types-perl
  libcrypt-ssleay-perl libnet-ssleay-perl gdesklets-data libossp-uuid-perl
  libmime-tools-perl python-utidylib libossp-uuid15 libtidy-0.99-0
  python-soappy libio-stringy-perl libnet-google-perl python-feedparser
  libemail-date-format-perl nullmailer hddtemp libwww-search-perl
  libmime-lite-perl libfcgi-perl python-fpconst libjcode-pm-perl
  libio-socket-ssl-perl python-chardet
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  envyng-core
The following NEW packages will be installed:
  envyng-core envyng-gtk
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 123kB of archives.
After this operation, 930kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe envyng-core 2.0.1 [120kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe envyng-gtk 1.1.1ubuntu3 [2606B]
Fetched 123kB in 0s (199kB/s)   
Selecting previously deselected package envyng-core.
(Reading database ... 138435 files and directories currently installed.)
Unpacking envyng-core (from .../envyng-core_2.0.1_all.deb) ...
Selecting previously deselected package envyng-gtk.
Unpacking envyng-gtk (from .../envyng-gtk_1.1.1ubuntu3_all.deb) ...
Processing triggers for man-db ...
Setting up envyng-core (2.0.1) ...

Setting up envyng-gtk (1.1.1ubuntu3) ...
anthony@anthony-desktop:~$ envyng-t
bash: envyng-t: command not found
anthony@anthony-desktop:~$ 


anybody know how to help?

card is a nvidia 7300

---

### Post by Partyboi2 on 2009-05-16
Hi, try putting a space between the envyng-t so try,
```
envyng -t
```

---

### Post by woop on 2009-05-16
it worked thank you
now Ive got floppy windows

few things were off though like the collapse all windows icon was slightly hiding in the corner of the screen so I adjusted the resolution
I made to an incorrect one...........then my window theme/icon theme changed
when I changed back the gnome menu was all over the place and gnome do is blurry

I need help 
the menu looks like this
[IMG]http://i265.photobucket.com/albums/ii220/Woop_012/Screenshot.png[/IMG]

---

### Post by Partyboi2 on 2009-05-16
What graphics card are you using?

---

### Post by Cillys on 2009-05-23
> **Partyboi2 said:**
> What graphics card are you using?
 
no wonder i cannot get help .. no one reads the posts ...
 
he clearly said nvidia 7300 in his orginal post

---

