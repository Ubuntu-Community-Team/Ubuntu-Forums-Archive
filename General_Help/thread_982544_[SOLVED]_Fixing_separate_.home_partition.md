---
title: "[SOLVED] Fixing separate .home partition"
date: 2008-11-14
forum: General Help
---

### Post by deathblossom on 2008-11-14
I screwed my separate home partition up, too, but in a different way from the other poster. 

So, I followed the Psychocats article as well, and got to the part where my partition wasn't working because of permission errors with .dmrc and .ICEauthority. I used their instructions to fix it and after doing so I get a new error where my session lasts less than 10 seconds. This is what it says:

Can't create dir /home/davis/Desktop
Can't create dir /home/davis/Desktop (yes, it says this twice)
Can't create dir /home/davis/Templates
Can't create dir /home/davis/Public
Can't create dir /home/davis/Pictures
Can't create dir /home/davis/Videos
Setting IM through im-witch fo rlocal=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default

(seahorse-agent:13773): libgnomevfs-WARNING **:Unable to create ~/.gnome-2 directory: Permission denied
Could not crate per-user gnome configuration directory home/davis/.gnome2: Permission denied

I added a new user account and have been using it to chage the permissions to different things based on posts from people appearing to have a similar problem, but nothing is working out.

---

### Post by taurus on 2008-11-14
Let's see what kind of permissions and who actually owns /home/davis.  Open a terminal and post the output of this command.

```
sudo ls -la /home/davis
```

---

### Post by deathblossom on 2008-11-14
There's a bit of stuff here, sorry!

drw-r--r-- 104 davis davis   4096 2008-11-14 02:27 .
drwxr-xr-x   6 root  root    4096 2008-11-14 03:44 ..
drwxr-xr-x   4 davis davis   4096 2008-11-14 02:26 .adobe
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:26 .amazonmp3
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:22 .aptitude
drwxr-xr-x   5 davis davis   4096 2008-11-14 02:25 .audacity-data
-rw-------   1 davis davis  12824 2008-11-14 02:06 .bash_history
-rw-r--r--   1 davis davis    220 2008-11-14 01:44 .bash_logout
-rw-r--r--   1 davis davis   2382 2008-11-14 01:49 .bashrc
-rw-r--r--   1 davis davis     85 2008-11-14 01:44 blah.py~
drwxr-xr-x   3 davis davis   4096 2008-11-14 01:44 .cache
drwxr-xr-x   3 davis davis   4096 2008-11-14 01:44 .compiz
drwxr-xr-x  10 davis davis   4096 2008-11-14 02:06 .config
-rw-r--r--   1 davis davis   7351 2008-11-14 02:26 Cydia.png
drwxr-xr-x   3 davis davis   4096 2008-11-14 01:44 .dbus
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:27 .dbus-keyrings
-rw-r--r--   1 davis davis     74 2008-11-14 01:41 .DCOPserver_MACGREGOR-FOUR-THIRTY-TWO__0
lrwxrwxrwx   1 davis davis     52 2008-11-14 01:44 .DCOPserver_MACGREGOR-FOUR-THIRTY-TWO_:0 -> /home/davis/.DCOPserver_MACGREGOR-FOUR-THIRTY-TWO__0
drwxr-xr-x   6 davis davis   4096 2008-11-14 02:22 Desktop
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:22 .desktops
-rw-r--r--   1 davis davis     28 2008-11-14 02:25 .dmrc
drwxr-xr-x   3 davis davis   4096 2008-11-14 02:26 Documents
drwxr-xr-x   3 davis davis   4096 2008-11-14 01:48 Downloads
drwxr-xr-x  23 davis davis   4096 2008-11-14 02:22 .dvdcss
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:25 dwhelper
drwxr-xr-x   7 davis davis   4096 2008-11-14 01:41 eclipse
drwxr-xr-x   5 davis davis   4096 2008-11-14 02:25 .eclipse
drwxr-xr-x   3 davis davis   4096 2008-11-14 01:42 .emacs.d
-rw-------   1 davis davis     16 2008-11-14 01:42 .esd_auth
drwxr-xr-x   8 davis davis   4096 2008-11-14 02:06 .evolution
drwxr-xr-x   6 davis davis   4096 2008-11-14 01:41 .exaile
-rw-r--r--   1 davis davis 519516 2008-11-14 01:41 Firefox_wallpaper.png
drwxr-xr-x   4 davis davis   4096 2008-11-14 01:44 .fltk
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:22 .fluxbox
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:49 .fontconfig
-rw-r--r--   1 davis davis    171 2008-11-14 02:25 font.gtkrc-2.0~
-rw-r--r--   1 davis davis    964 2008-11-14 02:26 forum.txr~
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:44 .fretsonfire
drwxr-xr-x   4 davis davis   4096 2008-11-14 02:25 .frostwire
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:26 .gcjwebplugin
drwxr-xr-x   6 davis davis   4096 2008-11-14 02:27 .gconf
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:41 .gconfd
drwxr-xr-x   7 davis davis   4096 2008-11-14 02:22 .gdesklets
drwxr-xr-x  13 davis davis   4096 2008-11-14 02:27 geany
drwxr-xr-x   5 davis davis   4096 2008-11-14 01:44 .geany
drwxr-xr-x  22 davis davis   4096 2008-11-14 01:49 .gimp-2.4
-rw-r-----   1 davis davis      0 2008-11-14 02:25 .gksu.lock
drwxr-xr-x   4 davis davis   4096 2008-11-14 01:49 .gnome
drwxr-xr-x  25 davis davis   4096 2008-11-14 02:27 .gnome2
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:42 .gnome2_private
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:25 .gnupg
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:41 .gpilotd
-rw-r--r--   1 davis davis      4 2008-11-14 02:26 .gpilotd.pid
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:41 .gstreamer-0.10
-rw-r--r--   1 davis davis    163 2008-11-14 01:44 .gtk-bookmarks
drwxr-xr-x   3 davis davis   4096 2008-11-14 02:25 .gtkpod
-rw-r--r--   1 davis davis    872 2008-11-14 01:41 .gtkr-2.0
-rw-r--r--   1 davis davis    872 2008-11-14 01:42 .gtkr-2.0~
-rw-r--r--   1 davis davis     87 2008-11-14 01:44 .gtkrc-1.2-gnome2
-rw-r--r--   1 davis davis    920 2008-11-14 02:25 .gtkrc-2.0
-rw-r--r--   1 davis davis    920 2008-11-14 02:27 .gtkrc-2.0~
drwx------   2 davis davis   4096 2008-11-14 02:25 .gvfs
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:49 .h264enc
drwxr-xr-x   5 davis davis   4096 2008-11-14 01:44 h264enc-8.5.6
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:25 .hplip
drwxr-xr-x   3 davis davis   4096 2008-11-14 02:22 ical2sqlite
-rw-r--r--   1 davis davis   4275 2008-11-14 02:27 .ICEauthority
drwxr-xr-x   3 davis davis   4096 2008-11-14 01:40 .icons
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:26 .idlerc
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:42 Incomplete
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:44 .infocom
-rw-r--r--   1 davis davis    670 2008-11-14 02:27 Info.plist~
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:22 [INSTALLERCACHE]
drwxr-xr-x   3 davis davis   4096 2008-11-14 02:06 .ipython
drwxr-xr-x   4 davis davis   4096 2008-11-14 02:06 .java
-rw-r--r--   1 davis davis     26 2008-11-14 02:26 justatest.txt~
drwxr-xr-x   3 davis davis   4096 2008-11-14 01:45 .kde
-rw-r--r--   1 davis davis    696 2008-11-14 01:44 lcdbryt.sh
-rw-------   1 davis davis     35 2008-11-14 02:25 .lesshst
drwxr-xr-x  10 davis davis   4096 2008-11-14 01:42 libical-0.27
-rw-r--r--   1 davis davis   1193 2008-11-14 02:22 ljapodifja.txt~
drwxr-xr-x   3 davis davis   4096 2008-11-14 01:42 .local
drwxr-xr-x   3 davis davis   4096 2008-11-14 02:26 .macromedia
drwxr-xr-x   3 davis davis   4096 2008-11-14 01:42 .mcop
-rw-------   1 davis davis     31 2008-11-14 02:22 .mcoprc
drwxr-xr-x   3 davis davis   4096 2008-11-14 02:22 .metacity
drwxr-xr-x   5 davis davis   4096 2008-11-14 02:06 .mozilla
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:06 .mplayer
drwxr-xr-x   5 davis davis   4096 2008-11-14 02:05 .mupen64plus
drwxr-xr-x 214 davis davis  12288 2008-11-14 02:04 Music
drwxr-xr-x   3 davis davis  20480 2008-11-14 01:42 .nautilus
drwxr-xr-x   3 davis davis   4096 2008-11-14 02:26 .openoffice.org2
-rw-r--r--   1 davis davis    677 2008-11-14 02:06 orio~
drwx------   2 davis davis   4096 2008-11-14 02:06 PDF
drwxr-xr-x   4 davis davis   4096 2008-11-14 02:27 Pictures
drwxr-xr-x   3 davis davis   4096 2008-11-14 02:25 .prism
-rw-r--r--   1 davis davis    438 2008-11-14 02:06 problem2.py
-rw-r--r--   1 davis davis    746 2008-11-14 01:44 problem2.pyc
-rw-r--r--   1 davis davis    258 2008-11-14 02:25 problem3.py
-rw-r--r--   1 davis davis    222 2008-11-14 02:27 problem6.py
-rw-r--r--   1 davis davis    566 2008-11-14 02:22 .profile
drwxr-xr-x   5 davis davis   4096 2008-11-14 02:22 .pSX
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:41 .pulse
-rw-------   1 davis davis    256 2008-11-14 01:44 .pulse-cookie
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:22 .qt
-rw-------   1 davis davis  10489 2008-11-14 02:06 .recently-used
-rw-r--r--   1 davis davis 625738 2008-11-14 02:05 .recently-used.xbel
-rw-------   1 davis davis   1024 2008-11-14 02:26 .rnd
-rw-r--r--   1 davis davis   2105 2008-11-14 01:44 runway.py
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:25 .serpentine
drwxr-xr-x   3 davis davis   4096 2008-11-14 02:25 .Skype
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:44 .spamassassin
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:44 .ssh
drwxr-xr-x   3 davis davis   4096 2008-11-14 01:49 .subversion
-rw-r--r--   1 davis davis      0 2008-11-14 02:06 .sudo_as_admin_successful
drwxr-xr-x   4 davis davis   4096 2008-11-14 01:49 .sudoku
-rw-------   1 davis davis  12288 2008-11-14 01:44 .swp
drwxr-xr-x   3 davis davis   4096 2008-11-14 02:26 .sync4j
drwxr-xr-x   4 davis davis   4096 2008-11-14 02:26 syncevolution-0.5
drwxr-xr-x  19 davis davis   4096 2008-11-14 02:25 Templates
drwxr-xr-x   4 davis davis   4096 2008-11-14 02:22 texmf
drwxr-xr-x   3 davis davis   4096 2008-11-14 02:25 .texmf-var
drwxr-xr-x  11 davis davis   4096 2008-11-14 02:25 .themes
drwxr-xr-x   3 davis davis   4096 2008-11-14 01:41 Themes
drwxr-xr-x   4 davis davis   4096 2008-11-14 01:42 .thumbnails
drwxr-xr-x   3 davis davis   4096 2008-11-14 02:22 .tilda
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:06 .tmpAppData
drwxr-xr-x   4 davis davis   4096 2008-11-14 02:22 .tomboy
-rw-r--r--   1 davis davis   4461 2008-11-14 02:22 .tomboy.log
drwxr-xr-x   5 davis davis   4096 2008-11-14 01:44 transfig.3.2.3
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:44 .tsclient
-rw-r--r--   1 davis davis    979 2008-11-14 02:06 untitled.py
-rw-r--r--   1 davis davis    259 2008-11-14 01:44 untitled.pyc
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:49 .update-manager-core
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:25 .update-notifier
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:41 VeohProxy-1.51
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:25 Videos
-rw-------   1 davis davis    511 2008-11-14 02:27 .viminfo
drwxr-xr-x   3 davis davis   4096 2008-11-14 01:44 .vlc
drwxr-xr-x   3 davis davis   4096 2008-11-14 01:45 vmware
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:41 .vmware
drwx------   2 davis davis   4096 2008-11-14 01:41 .w3m
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:49 .wapi
drwxr-xr-x   4 davis davis   4096 2008-11-14 02:22 .wine
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:49 .winefish
-rw-r--r--   1 davis davis    361 2008-11-14 02:27 working.ps~
drwxr-xr-x  17 davis davis   4096 2008-11-14 01:42 workspace
-rw-------   1 davis davis    129 2008-11-14 02:27 .Xauthority
-rw-------   1 davis davis    532 2008-11-14 01:49 .xdvirc
-rw-r--r--   1 davis davis     68 2008-11-14 02:22 .xfigrc
drwxr-xr-x   2 davis davis   4096 2008-11-14 01:41 .xine
-rw-r--r--   1 davis davis    146 2008-11-14 02:05 .xscreensaver-getimage.cache
-rw-r--r--   1 davis davis  30925 2008-11-14 01:44 .xsession-errors
drwxr-xr-x   2 davis davis   4096 2008-11-14 02:05 yam-linux

---

### Post by taurus on 2008-11-14
This could be the problem here.

```
drw-r--r-- 104 davis davis 4096 2008-11-14 02:27 .
```
You should have read, write, and executable permissions to your own $HOME.  Right now, you only have read and write but not execute.

Therefore, change the permission with

```
sudo chmod 755 /home/davis
ls -la /home
```

Now, /home/davis should look something similar to this.

```
drw**[COLOR="Blue"]x[/COLOR]**r-xr-x 104 davis davis 4096 2008-11-14 02:27 .
```
If it is, see if you can log back in as davis this time.

---

### Post by deathblossom on 2008-11-14
OH YES, that did it. Thank you so much.

---

