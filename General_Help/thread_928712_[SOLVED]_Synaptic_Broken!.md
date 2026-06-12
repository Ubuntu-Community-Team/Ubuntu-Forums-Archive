---
title: "[SOLVED] Synaptic Broken!"
date: 2008-09-24
forum: General Help
---

### Post by iThinkergoiMac on 2008-09-24
OK, so... this one's kinda urgent! Apparently I've managed to break synaptic. I was attempting to install some things from the Mac4Lin package, and I was installing the global menu applet, and the computer hardlocked in the middle of the installation. I tried everything I could think of to fix it, but I couldn't get it to unlock, so I had to force it off. Now when I run synaptic, I get the following error:

```
wesley@Finite:~$ sudo apt-get upgrade
[sudo] password for wesley: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package libgtk2.0-common needs to be reinstalled, but I can't find an archive for it.
```

I can't reinstall or uninstall it, but I can't get around it either. So, right now, synaptic will find packages that need to be upgraded, but it can't download them. I was trying out the stuff in a different user, but synaptic is, of course, across the whole system.

Also, for some stupid reason it deleted my main menu in my main user! I put it back, but I can't figure out how to get it to look like it normally does with the places and system menu where they normally are. It's all under one menu, which is a little bit busy.

---

### Post by Elfy on 2008-09-24
You could try

```
sudo apt-get install -f
sudo dpkg --configure -a
```

But I don't believe it's going to work, I have needed to

```
sudo dpkg --remove --force-remove-reinstreq libgtk2.0-common
```

Reinstall it again

```
sudo apt-get install libgtk2.0-common
```

It's likely that the menus got messed up because of it - if you still have problems with them you should be able to restore default menus

---

### Post by dodle on 2008-09-24
you could try downloading the deb package for [libgtk2.0-common]("http://lug.mtu.edu/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.12.9-3ubuntu2_all.deb") from [packages.ubuntu.com]("packages.ubuntu.com") and installing it manually.

---

### Post by iThinkergoiMac on 2008-09-24
When I ran sudo dpkg --configure -a I got this:

```
wesley@Finite:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libgtk2.0-0:
 libgtk2.0-0 depends on libgtk2.0-common; however:
  Package libgtk2.0-common is not installed.
dpkg: error processing libgtk2.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk2.0-examples:
 gtk2.0-examples depends on libgtk2.0-0 (= 2.12.9-4ubuntu3); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing gtk2.0-examples (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk2-engines-pixbuf:
 gtk2-engines-pixbuf depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is not configured yet.
 gtk2-engines-pixbuf depends on libgtk2.0-0 (= 2.12.9-4ubuntu3); however:
  Package libgtk2.0-0 is not configured yet.
 gtk2-engines-pixbuf depends on libgtk2.0-common; however:
  Package libgtk2.0-common is not installed.
dpkg: error processing gtk2-engines-pixbuf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome2-globalmenu-applet:
 gnome2-globalmenu-applet depends on gnome-common; however:
  Package gnome-common is not installed.
 gnome2-globalmenu-applet depends on gnome-pkg-tools; however:
  Package gnome-pkg-tools is not installed.
 gnome2-globalmenu-applet depends on libgtk2.0-0 (>= 2.12.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing gnome2-globalmenu-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-bin:
 libgtk2.0-bin depends on libgtk2.0-0 (>= 2.12.9-4ubuntu3); however:
  Package libgtk2.0-0 is not configured yet.
 libgtk2.0-bin depends on libgtk2.0-common; however:
  Package libgtk2.0-common is not installed.
dpkg: error processing libgtk2.0-bin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgtk2.0-0
 gtk2.0-examples
 gtk2-engines-pixbuf
 gnome2-globalmenu-applet
 libgtk2.0-bin
```

After I tried the force remove option, I was able to reinstall it just fine. Thanks so much!

I did try to reinstall manually, but it wouldn't let me until I'd forced removed it.

Thanks, guys... this was really helpful!

---

### Post by iThinkergoiMac on 2008-09-24
Hmmm... I still can't get the main menu to revert to what it used to be. Right now it's just the drop down menu with all the things below it. It used to be the icon with "Applications, Places, System" like default.

Perhaps this is a function of the software I installed?

---

### Post by Elfy on 2008-09-24
Yea I was pretty sure that the only thing that was going to work was the force command.

Glad you're sorted anyway, if you see this please mark thread solved :)

---

### Post by Elfy on 2008-09-24
Edit the panel - right click it

Add to panel - menu bar

Remove the old menu - right click - delete from panel

---

### Post by iThinkergoiMac on 2008-09-24
Well... I tried that. And nothing seemed to be happening.

I tried it a bunch of times and it seems to have an effect... my icons won't go anywhere but where they are, and I *have* unlocked them. So it's like it's there, but I can't see it or remove it.

---

### Post by iThinkergoiMac on 2008-09-24
Uh... I restarted and all... 20 or so appeared. Strange.

Thanks so much for all your help!

---

