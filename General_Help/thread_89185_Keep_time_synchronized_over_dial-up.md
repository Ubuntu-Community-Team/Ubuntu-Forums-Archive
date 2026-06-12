---
title: "Keep time synchronized over dial-up"
date: 2005-11-12
forum: General Help
---

### Post by david_finlayson on 2005-11-12
I am on a dial-up connection to the internet. What is the best way to keep my system and hardware clocks synchronized with a time server? 

There used to be a program called chrony to do this, but when I tried to install it Synaptic wanted to remove ntpdate ubuntu-base and ubuntu-minimal. That seemed dangerous to me.

Currently, I am just Synchronizing manually using the Adjust Date and Time Panel. I have disabled the Clock Synchronization service (ntpdate) at start-up because my machnine isn't connected to the internet on a regular basis. I read there is an ntpd burst mode that does the same job as chrony, is that a possibility?

David

---

### Post by Xian on 2005-11-12
[QUOTE=david_finlayson]There used to be a program called chrony to do this, but when I tried to install it Synaptic wanted to remove ntpdate ubuntu-base and ubuntu-minimal. That seemed dangerous to me.[/QUOTE]
The two meta-pkgs (ubuntu-base and ubuntu-minimal) are only used during the initial system installation and are no longer needed. They  only serve as a means to install a set of needed files. You can remove them with no ill effects. Chrony has a conflict with ntpdate and so you must choose one over the other.

---

### Post by Xian on 2005-11-12
Then of course you can do it the 'Debian Way': [Maintain Your System Clock](http://www.crazysquirrel.com/computing/debian/ntp.jspx)

---

### Post by david_finlayson on 2005-11-12
[QUOTE=Xian]Then of course you can do it the 'Debian Way': [Maintain Your System Clock](http://www.crazysquirrel.com/computing/debian/ntp.jspx)[/QUOTE]

ntp won't work over dial-up, will it?

---

### Post by Xian on 2005-11-12
Did you receive an error when you issued the 'ntpq -p' command?
Or, just install Chrony as you've used that before.

---

### Post by david_finlayson on 2005-11-12
I went ahead and installed chrony.

The reason I was hesitant is 6 months from now, when I am updating to Dapper, I don't want to have to remember what meta-packages I removed.  dist-upgrade can fail if a critical meta-package is updated and the user no longer has it installed (even if they still have all of its original dependencies). Remember all the problems people had upgrading to Breezy when they had removed desktop-base (which was necessary to install OpenOffice.org2 in Hoary).

As for time synchronization, most home users don't need to get anal about it. But, I DO need good time keeping at work (I'm a scientist) and it drives me crazy when my home computer is out of synch with the one at work. I imagine astronomy buffs would like to keep their clocks accurate as well.

The current default set up in Ubuntu (with ntpd) is designed for an always-on connection to the internet it fills your logs with error if you go off line and it can get seriously out of sorts if you shut the machine off at night (where the hardware clock is even worse than the system clock). Chrony solves all of those issues. Since chrony also works fine for the always connected situation (even as a time server) I wonder if it wouldn't make sense to use chrony as the default time daemon instead of ntpd? People who need ntp's advanced features know to install it.

David

---

### Post by Xian on 2005-11-12
[QUOTE=david_finlayson]The current default set up in Ubuntu (with ntpd) is designed for an always-on connection to the internet it fills your logs with error if you go off line and it can get seriously out of sorts if you shut the machine off at night (where the hardware clock is even worse than the system clock). [/quote]
I shutdown Ubuntu overnight quite often and have never seen it cause problems for the accuracy of the system clock. I can certainly understand how if you have it set up for consistent time syncs it would cause log errrors if there is no connection, but I'm unsure why this would be something anyone would take notice of at the desktop level.

[QUOTE=david_finlayson]I wonder if it wouldn't make sense to use chrony as the default time daemon instead of ntpd? People who need ntp's advanced features know to install it.[/QUOTE]
Well, there's that dep issue that is lingering around. I would just end up removing the application since I want the better configuration options of ntp. But the dep problem should be solved since chrony is a great program and is useful to many people. Perhaps you should file a bug on that and see if it can get corrected.

---

