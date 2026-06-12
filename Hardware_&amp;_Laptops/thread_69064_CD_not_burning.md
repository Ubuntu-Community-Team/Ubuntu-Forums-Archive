---
title: "CD not burning"
date: 2005-09-25
forum: Hardware &amp; Laptops
---

### Post by DoeRayMe on 2005-09-25
I have been trying to burn cds, it works but cannot play after

the default CD Writer wont work, just says insert blank disc, whens its CD-R

and GnomeBacker is the program i used

---

### Post by mlomker on 2005-09-25
> and GnomeBacker is the program i used

Have you tried K3B?

---

### Post by DoeRayMe on 2005-09-25
[QUOTE=mlomker]Have you tried K3B?[/QUOTE]
 when i install it, it doesnt show up on the menu

how do i install so it appears?

---

### Post by tehwa on 2005-09-25
[QUOTE=DoeRayMe]when i install it, it doesnt show up on the menu

how do i install so it appears?[/QUOTE]
Press F2 and type
```
killall gnome-panel
```
Since it may have added a menu reference (dunno, never used k3b) but this command will refresh the gnome menu to show it.

Else, press F2, type k3b. A menu entry can be added manually using smeg:

[http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor)

---

### Post by DoeRayMe on 2005-09-25
> root@ubuntu:/home/will # k3b
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
/usr/X11R6/bin/iceauth:  creating new authority file /root/.ICEauthority
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
kbuildsycoca: WARNING: '/usr/share/applications/themus-theme-applier.desktop' specifies undefined mimetype/servicetype 'application/x-gnome-theme-installed'
kbuildsycoca: WARNING: '/usr/share/applications/nautilus-folder-handler.desktop' specifies undefined mimetype/servicetype 'x-directory/gnome-default-handler'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifies undefined mimetype/servicetype 'application/rss+xml'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifies undefined mimetype/servicetype 'application/rdf+xml'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifies undefined mimetype/servicetype 'x-directory/webdav'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifies undefined mimetype/servicetype 'x-directory/webdav-prefer-directory'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/bmp'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/jpg'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-gray'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-icb'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-png'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-portable-anymap'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-portable-graymap'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-psd'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-xbitmap'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-xpixmap'
kbuildsycoca: WARNING: 'kcertpart.desktop' specifies undefined mimetype/servicetype 'application/binary-certificate'
kbuildsycoca: WARNING: 'fontthumbnail.desktop' specifies undefined mimetype/servicetype 'ThumbCreator'
kbuildsycoca: WARNING: '/usr/share/applications/xine.desktop' specifies undefined mimetype/servicetype 'video/x-anim'
kbuildsycoca: WARNING: 'Multimedia/xine.desktop' specifies undefined mimetype/servicetype 'video/x-anim'
kbuildsycoca: WARNING: '/usr/share/applications/gfloppy.desktop' specifies undefined mimetype/servicetype 'x-device/floppy'
kbuildsycoca: WARNING: 'katepart.desktop' specifies undefined mimetype/servicetype 'text/x-fortran'
kbuildsycoca: WARNING: 'videothumbnail.desktop' specifies undefined mimetype/servicetype 'ThumbCreator'
kbuildsycoca: WARNING: '/usr/share/applications/gnome-stones.desktop' specifies undefined mimetype/servicetype 'application/x-gnome-stones'
kbuildsycoca: WARNING: 'knotify.desktop' specifies undefined mimetype/servicetype 'KNotify'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-ar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-bzip-compressed-tar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-compressed-tar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-gtar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-lhz'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-rar-compressed'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-zip-compressed'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/zip'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'multipart/x-zip'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-war'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-ear'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-java-archive'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-cd-image'
k3b: WARNING: KGenericFactory: instance requested but no instance name or about data passed to the constructor!
k3b: ERROR: (K3bSongManager) Can't open file /root/.kde/share/apps/k3b/songlist.xml
k3b: ERROR: (K3bSongManager) Can't open file /root/.kde/share/apps/k3b/songlist.xml


i get that when i type k3b

---

### Post by mlomker on 2005-09-25
[QUOTE=DoeRayMe]i get that when i type k3b[/QUOTE]

Try running it as a regular user, not root.

---

### Post by DoeRayMe on 2005-09-25
get this now 

> will@ubuntu:~$ k3b
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kdeinit: Aborting. No write access to '/home/will/.ICEauthority'.
k3b: WARNING: KGenericFactory: instance requested but no instance name or about data passed to the constructor!
k3b: ERROR: (K3bSongManager) Can't open file /home/will/.kde/share/apps/k3b/songlist.xml


---

### Post by DoeRayMe on 2005-09-25
someone please help, i just re-booted, now i cant log in, i get an error and can only log into the terminal safe mode bit

---

### Post by DoeRayMe on 2005-09-25
fixed, had to chmod it

---

### Post by mlomker on 2005-09-25
The errors that you are getting are not normal (obviously).  I think there is a larger problem with your system than not being able to run K3B.

You need to provide more information about the error messages on your screen.  If it is a video card problem then you could run **dpkg-reconfigure xserver-xorg** but I don't know if that's the problem or not.

You could also try updating your box if you haven't recently.

```

apt-get update
apt-get upgrade

```

---

### Post by DoeRayMe on 2005-09-25
[QUOTE=mlomker]The errors that you are getting are not normal (obviously).  I think there is a larger problem with your system than not being able to run K3B.

You need to provide more information about the error messages on your screen.  If it is a video card problem then you could run **dpkg-reconfigure xserver-xorg** but I don't know if that's the problem or not.

You could also try updating your box if you haven't recently.

```

apt-get update
apt-get upgrade

```[/QUOTE]
 look at this 

> will@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  gaim k3b k3blibs k3blibs-dev
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

---

