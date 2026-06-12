---
title: "Moving to NetworkManager"
date: 2005-11-23
forum: General Help
---

### Post by kwaanens on 2005-11-23
I'm pondering moving to NetworkManager, which I got used to while using Fedora. What do I need to install/uninstall in order to get NetworkManager working in Ubuntu? How do I run NetworkManager? You see, I briefly tried, but I can't get the thing started.

- Ketil

---

### Post by matthewv on 2005-11-23
All I did was install it (sudo apt-get install network-manager)and then press Alt-F2, type in nm-applet , press enter and you're all set.

---

### Post by NeoChaosX on 2005-11-23
Also, add nm-applet to your start-up programs (System > Preferences > Session) so you can use it all the time.

---

### Post by kwaanens on 2005-11-23
Didn't know about the command nm-applet, in Fedora I think I used NetworkManagerInfo. How do I start nm-applet so that it starts on boot for all users?

- Ketil

---

### Post by matthewv on 2005-11-23
I just typed it that once and it started on boot. If that don't work, just follow the instructions NeoChaosX provided.

---

### Post by kwaanens on 2005-11-23
But System > Preferences > Sessions doesn't affect all users. If that was the case then I would have to give the root password to set it. Right?

- Ketil

---

### Post by Molerat on 2005-11-27
This thread is amazing.  Thank you.

---

### Post by santo on 2005-11-30
I'm also trying to switch to NetworkManager, but the only thing I get when running nm-applet is a little icon in the tray which looks like a network cable.
the context menu only contains the following items:
- Wireless Network Discovery
    -> Always Search
    -> Search Only When Disconnected
    -> Never Search
- Stop All Wireless Devices
- Connection Information
- About

The problem is that it doesn't look like the icon I'm used to from Fedora, which is the same as is shown in the screenshot on the NetworkManager site (4 vertical bars) and that is has totally different menu options.

When I plug in a network cable, I can get on the network/internet but without it (i.e. wireless), nothing happens, I can't select any Access Point, ...

Is this the same NetworkManager application as the one included in Fedora (i.e. [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)) ?
If so, what am I doing wrong ?

---

### Post by santo on 2005-11-30
Never mind, just found out I had to use the left click instead of the right click :oops: 

Still too used to M$ Windows behaviour I guess :eek:

---

