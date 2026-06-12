---
title: "problems updating Vino"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by sfl on 2009-06-07
I've been trying to connect to my Jaunty desktop from a windows box and finally found out that others are having the same problem on certain boxes equipped with an Nvidia video card ([https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126)) . 
The solution seems to be to update Vino to 2.26.2. I couldn't find it in Add/Remove scren so I downloaded it from ftp.gnome.org. When configuring it, I got errors about intltool not being found so I got that as well which required gettext to be updated. Finally I'm back to Vino and ./configure fails with the error below. I've seen posts recommending use of Synaptic but can't seem to find glib-2.0 and others. 
Am I just going about this the wrong way? 
Is it really normal for glib-2.0 not to be found (I thought glib was a fairly standard library, no? 

```

==== Error received when doing ./configure ==== 
checking for VINO_SERVER... configure: error: Package requirements (glib-2.0 >= 2.17.0 gtk+-x11-2.0 >= 2.13.1 gconf-2.0 libglade-2.0 dbus-1 >= 1.2.3 dbus-glib-1 libgnomeui-2.0) were not met:

No package 'glib-2.0' found
No package 'gtk+-x11-2.0' found
No package 'gconf-2.0' found
No package 'libglade-2.0' found
No package 'dbus-1' found
No package 'dbus-glib-1' found
No package 'libgnomeui-2.0' found

```

---

### Post by sfl on 2009-06-07
Turns out I needed the development libraries for each of the reported missing libraries. I installed them via Synaptic and they were usually named lib[libname].. but didn't always bear the exact name reported. 

Now my problem is getting the new 2.26.2 to be used by the desktop. The new config key (as described here [http://www.bani.com.br/lang/en/2009/05/remote-access-and-3d-effectsacesso-remoto-e-efeitos-3d/](http://www.bani.com.br/lang/en/2009/05/remote-access-and-3d-effectsacesso-remoto-e-efeitos-3d/)) is available in gconf-editor but I still get the same symptoms. 
Is there anything else I need to do to get the new version to take (other than make install and log out and back in)? I don't see a version number in System->Administration->Login Window so I'm not sure if the new version is even being used.

---

