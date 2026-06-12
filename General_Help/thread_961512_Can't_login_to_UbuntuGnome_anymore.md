---
title: "Can't login to Ubuntu/Gnome anymore"
date: 2008-10-28
forum: General Help
---

### Post by nicholaspaul on 2008-10-28
The only 'tinkering' I had done was deleting ~/tmp to free up disk space. Other than that, I have no idea why I cannot login to Ubuntu/Gnome anymore. The error I get is -

> Your session only lasted less than 10 seconds. if you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

View Details (~/.xsession-errors file)
/etc/gdm/Xsession: Beginning session setup ...
Setting IM through im-switch for locale=en_CA
Start IM throuh /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
mkdtemp: private socket dir: Permission denied


When I try to login to Gnome Safe mode - 

> Could not open or create the file "(null)"; this indicates that there may be a problem with your configuration, as many programs will need to create files in your home directory. The error was "Failed to create the file '/tmp/gconf-test-locking-file-PFYXJU': Permission denied " (errno = 13)

I can, however, log in to Terminal and via ssh. Any ideas how I can fix this?

---

### Post by mihaiv on 2008-10-28
Does the folder /tmp exists? If yes, which are its permissions? (type ls -l from /) For the folder /tmp there should be full permissions for everyone.

---

### Post by phidia on 2008-10-28
You can create a test user and try and login with that "sudo adduser test".

The first error you posted is usually about permissions you could google that-I'm sure some hits will point back to the forums here.

The ~/tmp directory you deleted was in your home folder?

---

### Post by nicholaspaul on 2008-10-28
It does exist, yes. I recreated it after having these problems. That's the only bit of 'problem solving I did!!

ls -l gives me this result for tmp

drwxrwxrwx

---

### Post by nicholaspaul on 2008-10-28
> **phidia said:**
> You can create a test user and try and login with that "sudo adduser test".

The first error you posted is usually about permissions you could google that-I'm sure some hits will point back to the forums here.

The ~/tmp directory you deleted was in your home folder?
Yes, tmp was (and is again) in the home folder. 
I tried creating a test user but couldn't login any differently than with the original user.

---

### Post by phidia on 2008-10-28
> **nicholaspaul said:**
> Yes, tmp was (and is again) in the home folder. 
I tried creating a test user but couldn't login any differently than with the original user.

That is NOT a good sign. There is something wrong with the system if you can't login with the newly created test user. 

Did you use sudo to remove that directory and if so were you in the appropriate directory/place when you issued the command?

You might try to issue "sudo apt-get update && sudo apt-get upgrade" to see if that will fix this.

---

### Post by nicholaspaul on 2008-10-28
I'm afraid that I may have used sudo, yes. And probably from within Home.... 
I'll try updating. Thanks!

---

### Post by phidia on 2008-10-28
> **nicholaspaul said:**
> I'm afraid that I may have used sudo, yes. And probably from within Home.... 
I'll try updating. Thanks!

Yeah, I hope that works. You shouldn't need to use sudo in your home folder-in fact you can make hidden files there viewable and just delete them by right clicking. That method shouldn't cause any uncorrectable problems.

When in CLI it's important to know what path you are issuing commands for (use pwd).
Well everyone does this so it's not the end of the world and you can back up from a live cd if you can't recover another way.

---

### Post by nicholaspaul on 2008-10-28
Drat. I tried updating and still can't login. Should I try fixing the permissions on /tmp? How would I do that?

---

### Post by phidia on 2008-10-28
/tmp is different from ~/tmp and that may be the problem.

you can compare the permissions on various system files by issuing "ls -la <filename>"

See the wiki [here]("https://help.ubuntu.com/community/FilePermissions") on permissions.

---

### Post by nicholaspaul on 2008-10-28
I tried removing ~/tmp (tmp in the home folder) and made it again, leaving the permissions as is. I didn't use sudo. 
Same error on login...
Can't see any permission errors. 
> nick@ubuntutu:/tmp$ ls -al
total 24
drwxr-xr-x  5 root root 4096 2008-10-28 14:20 .
drwxr-xr-x 20 root root 4096 2008-10-28 00:28 ..
drwxrwxrwt  2 root root 4096 2008-10-28 00:28 .ICE-unix
-rw-------  1 root root    0 2008-10-28 00:28 tmp.BSEkyY5904
-rw-------  1 root root    0 2008-10-28 14:17 tmp.ktPVUU7374
-rw-------  1 root root    0 2008-10-28 14:18 tmp.lwMnJX5915
-rw-------  1 root root    0 2008-10-28 12:44 tmp.mQUdr13301
-rw-------  1 root root    0 2008-10-28 10:39 tmp.SjXji11339
-rw-------  1 root root    0 2008-10-28 10:41 tmp.UQGLTa5913
-rw-------  1 root root    0 2008-10-28 12:46 tmp.ZeaxXR5916
drwxr-xr-x  2 root root 4096 2008-10-28 14:19 .winbindd
-r--r--r--  1 root root   11 2008-10-28 14:20 .X0-lock
drwxrwxrwt  2 root root 4096 2008-10-28 14:20 .X11-unix


> nick@ubuntutu:~/tmp$ ls -al
total 12
drwxr-xr-x   2 nick nick 4096 2008-10-28 14:13 .
drwxr-xr-x 111 nick nick 8192 2008-10-28 14:21 ..


> nick@ubuntutu:~$ ls -al
total 3192
-rw-r--r--   1 nick nick      0 2007-05-23 02:07 -
drwxr-xr-x 111 nick nick   8192 2008-10-28 14:21 .
drwxr-xr-x   7 root root   4096 2008-10-28 01:20 ..
drwx------   2 nick root   4096 2006-08-11 02:00 .3ddesktop
-rwxr-xr-x   1 nick root    110 2006-08-11 02:02 .61
drwxr-xr-x   4 nick root   4096 2008-02-09 01:57 .adobe
drwx------   2 nick nick   4096 2008-06-25 10:24 .alsaplayer
drwxr-xr-x   2 nick root   4096 2008-09-15 20:27 artwork
-rw-r--r--   1 nick root     24 2006-08-11 02:02 .aspell.en.prepl
-rw-r--r--   1 nick root     22 2006-08-11 02:02 .aspell.en.pws
-rw-r--r--   1 nick nick    967 2007-02-03 10:54 .audacity
-rwxr-xr-x   1 nick nick   9256 2006-08-11 20:12 automatix-installer
-rw-r--r--   1 nick nick   1730 2006-08-05 14:28 automatix.key
-rw-r--r--   1 nick root    342 2006-08-15 13:37 automatix.log
drwxr-xr-x   2 nick nick   4096 2007-05-23 02:47 autosave
-rw-------   1 nick nick   7320 2008-10-28 14:14 .bash_history
-rw-r--r--   1 nick nick    220 2006-08-11 01:10 .bash_logout
-rw-r--r--   1 nick nick    414 2006-08-11 01:10 .bash_profile
-rw-r--r--   1 nick nick   2227 2006-08-11 01:10 .bashrc
drwxr-xr-x   4 nick root   4096 2006-08-11 02:00 .bmp
drwx------   5 nick nick   4096 2007-01-07 04:38 .cache
drwxr-xr-x   2 nick nick   4096 2007-08-04 20:59 .camstream-upload
drwxr-xr-x   7 nick root   4096 2008-01-29 21:32 .cddb
drwxr-xr-x   2 nick root   4096 2006-08-11 02:00 .cddbslave
drwxr-xr-x   3 nick root   4096 2007-10-21 09:58 .checkgmail
drwx------   2 nick nick   4096 2007-08-26 21:26 .chewing
drwx------   2 nick nick   4096 2006-08-31 16:01 .comments
drwx------  15 nick root   4096 2008-09-17 13:06 .config
drwx------   3 nick nick   4096 2008-09-04 16:47 .dbus
drwx------   2 nick nick   4096 2008-04-28 17:08 .dbus-keyrings
-rw-r--r--   1 nick nick     57 2008-10-27 17:10 .DCOPserver_ubuntutu__0
lrwxrwxrwx   1 nick nick     34 2008-10-27 17:10 .DCOPserver_ubuntutu_:0 -> /home/nick/.DCOPserver_ubuntutu__0
drwxr-xr-x   3 nick nick   4096 2008-10-28 00:22 Desktop
drwx------   2 nick nick   4096 2007-10-23 11:06 .dillo
-rw-r--r--   1 nick root   4864 2006-08-11 02:02 diskmounter
-rw-r--r--   1 nick nick    203 2006-11-03 00:43 disk space 
-rw-------   1 nick nick     25 2008-10-28 14:21 .dmrc
drwxr-xr-x   2 nick nick   4096 2008-10-21 09:10 Documents
-rwxr--r--   1 nick nick  15364 2008-10-06 09:01 .DS_Store
drwxr-xr-x  18 nick nick   4096 2008-06-21 11:48 .dvdcss
drwxr-xr-x   2 nick root   4096 2007-10-14 22:31 .dvdrip
drwxr-xr-x   4 nick root   4096 2006-08-11 02:02 .dvdrip-master
-rw-r--r--   1 nick root  21487 2006-08-11 02:02 .dvdriprc
drwx------   3 nick nick   4096 2008-10-15 11:23 .emusic
drwxr-xr-x   6 nick nick   4096 2008-08-15 00:56 emusicdlm
-rw-------   1 nick nick     16 2006-08-11 02:00 .esd_auth
drwxr-xr-x   3 nick root   4096 2006-08-11 02:00 .Eterm
drwxr-xr-x   8 nick root   4096 2007-07-21 11:54 .evolution
drwxr-xr-x   5 nick nick   4096 2008-04-23 16:18 .exaile
lrwxrwxrwx   1 nick nick     26 2006-08-11 01:10 Examples -> /usr/share/example-content
-rwxr--r--   1 nick nick      0 2008-10-28 14:08 file1
-rw-r--r--   1 nick nick      0 2008-10-28 14:08 file2
-rw-r--r--   1 nick nick      0 2008-10-28 14:08 file3
-rw-r--r--   1 nick nick    131 2006-10-17 21:54 Find files
-rw-r--r--   1 nick nick 430177 2007-06-16 13:39 Firefox_wallpaper.png
drwx------   3 nick root   4096 2006-08-11 02:00 .fluxbox
-rwxr--r--   1 nick root  64598 2006-08-11 02:02 fluxbox-generate_menu.in
drwxr-xr-x   2 nick nick   4096 2008-10-27 18:35 .fontconfig
drwxr-xr-x   2 nick nick   4096 2008-01-22 02:41 .fonts
-rw-r--r--   1 nick nick      0 2007-03-28 23:01 .fonts.cache-1
-rw-r--r--   1 nick nick    514 2007-08-05 13:22 .fonts.conf
drwxr-xr-x   6 nick root   4096 2006-08-11 02:00 .fullcircle
drwx------   3 nick root   4096 2007-10-22 23:20 .gaim
drwxr-xr-x   2 nick nick   4096 2007-09-29 00:57 .GalleryRemote
drwx------   5 nick nick   4096 2008-10-27 17:10 .gconf
drwx------   2 nick nick   4096 2008-10-28 00:18 .gconfd
drwx------   3 nick root   4096 2006-08-11 02:02 .gftp
drwxr-xr-x  21 nick root   4096 2007-10-12 01:05 .gimp-2.2
drwxr-xr-x  20 nick nick   4096 2008-10-05 15:52 .gimp-2.4
-rw-r-----   1 nick nick      0 2008-10-26 20:57 .gksu.lock
drwxr-xr-x   7 nick nick   4096 2008-07-22 00:27 .gnome
drwx------  22 nick nick   4096 2008-10-28 00:25 .gnome2
drwx------   2 nick nick   4096 2006-08-11 01:20 .gnome2_private
drwx------   2 nick nick   4096 2006-08-11 15:59 .gnome_private
drwx------   2 nick nick   4096 2006-08-13 12:39 .gnupg
drwxr-xr-x   3 nick nick   4096 2007-06-30 20:41 .google
lrwxrwxrwx   1 nick nick     36 2006-08-15 08:18 googleearth -> /home/nick/google-earth//googleearth
drwxr-xr-x   3 nick nick   4096 2007-02-04 03:39 .gpredict
drwxr-xr-x   5 nick nick   4096 2008-07-06 16:09 .gqview
-rw-r--r--   1 nick nick   1508 2008-01-30 09:58 .grip
-rw-r--r--   1 nick nick     62 2008-01-30 09:58 .grip-lame
-rw-r--r--   1 nick root     85 2006-10-21 21:11 .grip-oggenc
drwxr-xr-x   2 nick nick   4096 2008-10-26 21:26 .gstreamer-0.10
drwxr-xr-x   2 nick nick   4096 2006-09-27 20:36 .gstreamer-0.8
-rw-------   1 nick nick    174 2008-10-27 17:18 .gtk-bookmarks
drwxr-x---   3 nick nick   4096 2007-12-04 03:44 .gtk-gnutella
drwxr-xr-x   5 nick nick   4096 2007-12-04 03:23 gtk-gnutella-downloads
-rw-r--r--   1 nick nick   3682 2007-08-05 17:12 .gtk_qt_engine_rc
-rw-r--r--   1 nick nick     86 2006-08-11 02:00 .gtkrc-1.2-gnome2
-rw-r--r--   1 root root     45 2007-12-15 21:49 .gtkrc-2.0
-rw-r--r--   1 nick nick    285 2007-08-05 11:53 .gtkrc-2.0-kde
drwx------   2 nick nick   4096 2008-06-23 13:51 .gvfs
drwx------   2 nick nick   4096 2007-05-16 21:27 .gxine
drwxr-----   2 nick nick   4096 2007-10-25 01:53 .hplip
drwxr-xr-x  22 nick nick   8192 2007-10-25 02:04 hplip-2.7.10
-rw-------   1 nick nick  20115 2008-10-27 17:10 .ICEauthority
drwxr-xr-x   2 nick nick   4096 2007-08-03 02:05 .icewm
-rwxr--r--   1 nick root   1067 2006-08-11 02:02 iChat Icons
-rw-r--r--   1 nick nick   1718 2006-09-16 12:56 ichthux.asc
drwxr-xr-x   2 nick root   4096 2006-08-20 17:30 .icons
-rwxr--r--   1 nick root 115745 2006-08-11 02:02 ._IMG_0139.JPG
drwxr-xr-x   2 nick nick   4096 2007-12-04 03:43 Incomplete
drwxr-xr-x   3 nick nick   4096 2007-06-22 17:00 .ipodder
drwx------   2 nick root   4096 2007-05-31 00:48 .irssi
drwxr-xr-x   4 nick nick   4096 2007-07-01 00:58 .java
-rw-r--r--   1 nick nick  33686 2006-08-05 14:29 jriddell.key
drwx------   6 nick root   4096 2008-08-27 02:06 .kde
-rw-------   1 nick nick    439 2007-08-05 13:29 .kderc
-rw-r--r--   1 nick root   1730 2006-08-11 02:02 key.gpg.asc
-rw-r--r--   1 nick nick   1730 2006-08-12 15:33 key.gpg.asc.1
-rw-r--r--   1 nick nick   2762 2007-09-03 17:19 .kinorc
drwxr-xr-x   2 nick nick   4096 2006-11-10 03:23 .kipina
drwxr-xr-x   3 nick nick   4096 2008-07-22 15:19 .kompozer
-rw-r-----   1 nick nick      6 2008-02-01 00:58 .ktorrent.lock
-rw-r--r--   1 nick nick 782888 2007-09-13 16:27 launch_desktop.png
-rw-------   1 nick root     35 2006-08-11 20:58 .lesshst
drwxr-xr-x   2 nick nick   4096 2008-02-17 15:47 .lftp
drwxr-xr-x   2 root root   4096 2008-06-25 09:38 lil
drwxr-xr-x   3 nick nick   4096 2008-09-13 08:40 LimeWire
drwxr-xr-x   8 nick nick   4096 2008-10-27 10:13 .limewire
-rwxr-xr-x   1 nick root    102 2006-08-11 02:02 linxstyle
drwxr-xr-x   3 nick root   4096 2006-08-11 02:01 .local
drwx------   3 nick nick   4096 2006-08-15 08:19 .loki
-rwxr--r--   1 nick root     83 2006-12-16 23:01 .lownslo
drwx------   4 nick root   4096 2006-12-04 00:11 .macromedia
drwxr-xr-x   3 nick root   4096 2006-08-11 02:01 .mcop
-rw-------   1 nick nick     31 2008-10-27 10:16 .mcoprc
drwx------   3 nick nick   4096 2006-08-11 01:20 .metacity
drwx------   5 nick root   4096 2008-06-23 13:52 .mozilla
-rw-r--r--   1 nick nick 348442 2008-09-14 10:15 mozilla.ps
drwxr-xr-x   4 nick root   4096 2006-08-11 02:00 .mozilla-thunderbird
drwxr-xr-x   2 nick root   4096 2006-08-15 13:38 .mplayer
drwx------   2 nick nick   4096 2008-08-19 00:19 .murmur
-rw-------   1 root root      9 2008-08-25 00:12 .nano_history
drwxr-xr-x   3 nick nick   4096 2008-10-28 00:25 .nautilus
-rwxr--r--   1 nick root     82 2006-08-11 02:02 ._nick.JPG
-rw-r--r--   1 nick nick  25198 2008-07-22 15:20 Nicks-Links.html
-rwxr--r--   1 nick root     82 2006-08-11 02:02 ._NickToday.jpg
-rwxr--r--   1 nick root     83 2006-08-11 02:00 .nickxp
-rwxr-xr-x   1 nick root    101 2006-08-11 02:01 nlinxstyle
drwxr-xr-x   3 nick root   4096 2006-08-11 02:01 .nvu
drwx------   3 nick root   4096 2008-10-28 00:23 .openoffice.org2
drwxr-xr-x   9 nick nick   4096 2006-11-25 12:28 .opera
drwx------   2 nick nick   4096 2008-10-28 00:14 PDF
-rw-r--r--   1 nick nick    483 2007-07-01 13:39 plugin_stack.trace
drwxr-xr-x   2 nick nick   4096 2008-06-23 13:51 Public
drwxr-xr-x   2 nick nick   4096 2008-06-26 11:28 .pulse
-rw-------   1 nick nick    256 2008-06-26 11:28 .pulse-cookie
drwx------   5 nick nick   4096 2008-10-05 15:27 .purple
drwxr-xr-x   2 nick root   4096 2008-09-04 16:46 .qt
-rwxr--r--   1 nick nick     82 2006-10-05 00:28 ._Ramsey file.pdf
-rw-r--r--   1 nick nick 325199 2007-12-17 08:48 realage
-rw-------   1 nick nick   9122 2008-10-27 18:35 .recently-used
-rw-r--r--   1 nick nick 247948 2008-10-28 00:18 .recently-used.xbel
-rwxr--r--   1 nick root     82 2006-08-11 02:00 .router
-rwxr--r--   1 nick root     87 2006-08-11 02:02 samba
drwxrwx---   3 nick nick   4096 2006-11-21 08:57 .sane
drwx------   4 nick nick   4096 2007-08-26 21:26 .scim
drwxr-xr-x   2 nick nick   4096 2006-11-28 23:51 .serpentine
-rw-r--r--   1 nick nick  17579 2007-08-05 17:21 share.do
-rwxr--r--   1 nick nick   1054 2007-07-16 22:02 signature.html
drwx------   3 nick nick   4096 2008-09-26 01:56 .Skype
-rw-r--r--   1 nick root  10838 2006-08-11 17:52 smb.conf
drwxr-xr-x   2 nick nick   4096 2007-06-12 12:47 sn9c1xx-1.48
-rw-r--r--   1 nick nick      0 2007-12-18 14:53 srtp.log
drwx------   2 nick root   4096 2007-01-01 17:50 .ssh
-rwxr--r--   1 nick root     95 2007-01-22 09:15 .ssh3
drwxr-xr-x  14 nick nick   4096 2008-09-29 01:22 stable
drwxr-xr-x   3 nick nick   4096 2008-09-29 01:21 .subversion
-rw-r--r--   1 nick nick      0 2006-08-11 02:00 .sudo_as_admin_successful
drwxr-xr-x   2 nick nick   4096 2008-06-23 13:51 Templates
-rwxr--r--   1 nick nick     82 2006-08-18 19:36 ._Temp Resume.pdf
-rwxr--r--   1 nick nick     82 2006-08-18 19:37 ._TheLatestPubQuiz.pdf
drwxr-xr-x   2 nick nick   4096 2006-12-16 23:05 Themes
drwxr-xr-x   2 nick root   4096 2006-08-11 02:00 .themes
-rwxr--r--   1 nick root     87 2006-08-11 02:02 .thresher
drwx------   5 nick nick   4096 2008-09-08 00:27 .thumbnails
drwx------   4 nick root   4096 2006-08-11 02:01 .thunderbird
drwxr-xr-x   2 nick nick   4096 2008-10-28 14:13 tmp
-rwxr--r--   1 nick root    118 2006-08-11 02:00 .ubuntunes
-rw-r--r--   1 nick nick   1710 2007-05-01 15:15 ubuntustudio.gpg
drwxr-xr-x   2 nick nick   4096 2007-03-02 00:18 .update-manager
drwxr-xr-x   2 nick nick   4096 2008-06-24 14:30 .update-manager-core
drwx------   2 nick nick   4096 2006-08-11 02:00 .update-notifier
-rwxr-xr-x   1 nick root    289 2006-08-14 23:34 .upgrade
-rwxr--r--   1 nick root     75 2006-08-11 02:00 .val
drwxr-xr-x   2 nick nick   4096 2008-07-06 00:47 .virt-manager
drwxr-xr-x   2 nick root   4096 2008-09-29 01:41 .wapi
drwxr-xr-x   2 nick nick   4096 2007-08-09 01:01 .webcamd
drwx------   4 nick nick   4096 2007-12-18 14:53 .wengophone
drwxr-xr-x   4 nick nick   4096 2008-10-11 20:30 .wine
-rw-------   1 nick nick    173 2008-10-28 14:21 .Xauthority
drwxr-xr-x   3 nick root   4096 2008-04-17 10:16 .xine
drwxr-xr-x   4 nick nick   4096 2006-10-18 20:42 .xmms
-rw-r--r--   1 nick nick  10300 2008-10-21 02:07 .xscreensaver
-rw-r--r--   1 nick nick    396 2008-09-30 08:57 .xscreensaver-getimage.cache
-rw-r--r--   1 nick nick    232 2008-10-28 14:20 .xsession-errors


---

### Post by phidia on 2008-10-28
From the CLI type "cd" press enter or "cd /". You should be in the "/" directory.
Type "ls -la tmp" On a working system I believe the output looks like this > lrwxrwxrwx 1 root root 8 2007-02-21 02:58 tmp -> /var/tmp

I'm in a live cd right now but barring anything really odd something like that.

---

### Post by nicholaspaul on 2008-10-28
This is what I get - 
> nick@ubuntutu:/$ ls -la tmp
total 24
drwxr-xr-x  5 root root 4096 2008-10-28 15:05 .
drwxr-xr-x 20 root root 4096 2008-10-28 00:28 ..
drwxrwxrwt  2 root root 4096 2008-10-28 00:28 .ICE-unix
-rw-------  1 root root    0 2008-10-28 00:28 tmp.BSEkyY5904
-rw-------  1 root root    0 2008-10-28 14:17 tmp.ktPVUU7374
-rw-------  1 root root    0 2008-10-28 14:18 tmp.lwMnJX5915
-rw-------  1 root root    0 2008-10-28 12:44 tmp.mQUdr13301
-rw-------  1 root root    0 2008-10-28 10:39 tmp.SjXji11339
-rw-------  1 root root    0 2008-10-28 10:41 tmp.UQGLTa5913
-rw-------  1 root root    0 2008-10-28 12:46 tmp.ZeaxXR5916
drwxr-xr-x  2 root root 4096 2008-10-28 14:19 .winbindd
-r--r--r--  1 root root   11 2008-10-28 15:05 .X0-lock
drwxrwxrwt  2 root root 4096 2008-10-28 15:05 .X11-unix


---

### Post by volvoguy on 2008-11-11
> **phidia said:**
> /tmp is different from ~/tmp and that may be the problem.

(I'm Nick's "local" support and just catching up on this issue here)

I think this issue hits the nail on the head. To my knowledge, Ubuntu doesn't create a /username/tmp folder. If that's correct, the most that should be messed up is whatever app created that folder or whatever data was there if YOU created the folder. 

As was mentioned already, knowing where you are in the CLI is really important. Even a typo can do major damage. If you were in your home folder (where it should be safe to delete your stuff) and typed:

sudo rm -rf /tmp     (the system temp directory)

instead of:

sudo rm -rf tmp      (a directory created by you or an app)

things could be really hosed. I've never actually had to fix that mistake so I'm not sure if it's possible or what's involved. 

Is there possibly a base system package that Nick could try "reinstalling" that would recreate the essential system files/directories and maybe fix the problem? 

Nick, just to confirm things, was it JUST a directory called "tmp" in your home folder that was deleted, or did something happen so that "/tmp" was deleted? Or both? :-)

Again, as already mentioned, worst case scenario is that you'd have to log in with a livecd, back up your data to a disc or external drive, and reinstall Ubuntu. Time consuming, but easy!

Also, just FYI for others trying to help, this is the contents of my /tmp folder:

drwxrwxrwt  2 root root 4096 2008-09-03 22:08 .ICE-unix
drwxr-xr-x  2 root root 4096 2008-09-03 23:00 .webmin
drwxrwxrwt  2 root root 4096 2008-09-03 22:08 .X11-unix

Obviously at least one GUI related file. Could it's absence be causing Nick's problem?

Aaron

---

### Post by geirha on 2008-11-11
/tmp needs to be writeable to all and have the sticky-bit set. Do ```
sudo chmod 1777 /tmp
``` and reboot to be on the safe side.

---

