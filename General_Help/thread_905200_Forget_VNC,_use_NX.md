---
title: "Forget VNC, use NX"
date: 2008-08-30
forum: General Help
---

### Post by CaptSaltyJack on 2008-08-30
Just some advice I wanted to pass along to anyone who wants to have graphical remote login access to their Linux box.  VNC I've found is slow over WAN, not to mention insecure (unless you're doing it through an SSH tunnel).  Best bet, I've found, is to use NX Free Edition by NoMachine.  Screen redraws are FAST.. I can be at work connected to home, and it almost feels like I'm on a LAN.  Security-wise, NX operates on port 22 (SSH), so it's secure by default.

Install is really easy.

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

Choose either DEB i386 or DEB x86_64.  Download the client, node, and server packages, install in that order (dpkg -i file.deb), and it's done.

Now grab an NX client for either Linux, Windows, or Mac OS, and you can connect to your Linux box remotely AND securely.  Blows the pants off VNC.

Enjoy.

---

