---
title: "Network Admin Grayed Out"
date: 2008-08-31
forum: General Help
---

### Post by adamorjames on 2008-08-31
I use a laptop and wireless is essential so this problem is a real problem. The first sign that something was wrong was when the default Ubuntu network item on the panel was missing. I then tried to go around that by using Network Admin and manually entering the network name instead of using roaming. I found to my suprise that Network Admin wasn't working. Below is a screenshot and other information.

Distro: Ubuntu Studio 8.04
Condition: Clean install besides my home folder

Screenshot:
[IMG]http://img402.imageshack.us/img402/5483/screenshotnetworksettinlr8.png[/IMG]

```

$ sudo network-admin 

(network-admin:7224): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:7224): CRITICAL **: Unable to lookup session information for process '7224'

```

```

$ ls -l network-admin 
-rwxr-xr-x 1 root root 139016 2008-04-21 11:06 network-admin

```

---

### Post by Rocket2DMn on 2008-08-31
You need to Unlock, but don't do it from sudo.  Just run network-admin as your own user, then Unlock with your username and password.

For other graphical programs that you DO need to use root privileges for, don't forget to use graphical sudo (gksudo or kdesu)

---

### Post by adamorjames on 2008-08-31
Ah, that fixes that. I wonder why the network item that shows the wireless networks won't show up on the panel?

---

### Post by Rocket2DMn on 2008-08-31
Are you using Intrepid?  I know they were switching over to network-admin 0.7.  Either way, you might not be running nm-applet.  Check System->Preferences->Sessions.

---

### Post by adamorjames on 2008-08-31
That's it. nm-applet wasn't checked. Thanks for the help. I :lolflag: at myself.

---

