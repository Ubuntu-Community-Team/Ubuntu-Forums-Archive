---
title: "I have no xorg! And im running ubuntu?"
date: 2008-08-09
forum: General Help
---

### Post by recondev on 2008-08-09
I tried sudo /etc/x11/xorg.conf and it gives me a blank file , i look in /etc/x11/ and there is not xorg.conf only back ups. How can i fix this i need to disable my touchpad.

---

### Post by tamoneya on 2008-08-09
you need a capital "X" in "X11"

---

### Post by oldos2er on 2008-08-09
> **recondev said:**
> I tried sudo /etc/x11/xorg.conf and it gives me a blank file , i look in /etc/x11/ and there is not xorg.conf only back ups. How can i fix this i need to disable my touchpad.

 Try "gksudo gedit /etc/X11/xorg.conf"

 Linux is case-sensitive.

---

### Post by recondev on 2008-08-09
Blank* , should I do a xorg fix?

---

### Post by recondev on 2008-08-09
jay@jay-laptop:~$ sudo dpkg-reconfigure xserver-xorg
md5sum: /etc/X11/xorg.conf: No such file or directory

---

### Post by zxscooby on 2008-08-09
its gotta be somewhere

 /etc/X11/<cmdline>
           /usr/etc/X11/<cmdline>
           /etc/X11/$XORGCONFIG
           /usr/etc/X11/$XORGCONFIG
           /etc/X11/xorg.conf-4
           /etc/X11/xorg.conf
           /etc/xorg.conf
           /usr/etc/X11/xorg.conf.<hostname>
           /usr/etc/X11/xorg.conf-4
           /usr/etc/X11/xorg.conf
           /usr/lib/X11/xorg.conf.<hostname>
           /usr/lib/X11/xorg.conf-4
           /usr/lib/X11/xorg.conf

---

### Post by PmDematagoda on 2008-08-09
If there is a backup, just rename one of the backups to xorg.conf with:-
```
sudo cp name-of-backup xorg.conf
```
which might allow you to start the X-Server properly with the proper drivers loaded.

---

### Post by InfinityCircuit on 2008-08-09
X.org 7.3 and newer have better autodetection, so they can run without a /etc/X11/xorg.conf.  If you need to generate one from scratch, you can use the following tools:

X -configure
xorgcfg

---

### Post by recondev on 2008-08-10
jay@jay-laptop:/etc/X11$ dir
app-defaults		 xorg.conf.1			xorg.conf.failsafe.bak
cursors			 xorg.conf.2			xorg.conf.fglrx-0
default-display-manager  xorg.conf.20080724152337	xorg.conf.xgl
fonts			 xorg.conf_backup		Xresources
rgb.txt			 xorg.conf_backup_200807241319	xserver
X			 xorg.conf_backup_200807241454	Xsession
xinit			 xorg.conf_backup_200807241837	Xsession.d
xkb			 xorg.conf_backup_200807271545	Xsession.options
xorg.conf		 xorg.conf_backup_200808091147	XvMCConfig
xorg.conf~		 xorg.conf.failsafe		Xwrapper.config
jay@jay-laptop:/etc/X11$

---

