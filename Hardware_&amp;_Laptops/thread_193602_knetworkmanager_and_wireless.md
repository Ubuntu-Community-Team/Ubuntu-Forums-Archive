---
title: "knetworkmanager and wireless"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by GoldBuggie on 2006-06-10
I'm running knetworkmanager and when I use regulare ethernet cable I get everything I want. I can click on the icon in the systray and see my cable and wireless connection.

But when I pull out my cord or choose the wireless connection the icon in the systray indecates that I do not have a connection. But runing nm-tool shows that I am connected. 

Sometimes I can still click on the not-connected icon and get the info. Sometimes it just states that NetworkManager is not running.

Is there a config file that I need to edit? Since it works for eth1(=cable) but not eth0(=wireless)

Any help is appreciated!

---

### Post by chuvisco on 2006-06-10
What wireless card are you using?  Mine (orinoco) does not work with the newest version (0.6.2-ubuntu7) of NetworkManager, so I am using v. 0.5.1.  I think there are one or two other cards that have the same problem.

---

### Post by GoldBuggie on 2006-06-11
i'm using orinoco...so I guess I'll have to try the 0.51 version. I'll report back if it was succesful.

---

### Post by chuvisco on 2006-06-11
You may already know this, but you can download previous package versions on launchpad.net.  Another caveat is that knetworkmanager requires network-manager 0.6+, so you will have to use nm-applet and use a startup [script]("http://mail.gnome.org/archives/networkmanager-list/2005-December/msg00127.html") to allow it to access the gnome keyring (if you use encrypted networks).  I haven't tried this script yet, but others say that it works.

There's also [this]("http://ubuntuforums.org/showthread.php?t=192281"), which looks interesting, but I don't know if it will work in KDE.

If you try either of these before I do, please let me know how it goes.

---

