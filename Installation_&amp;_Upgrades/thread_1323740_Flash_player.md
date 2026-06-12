---
title: "Flash player"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by lolp12 on 2009-11-12
hello
 
i was yesterday installing flash player then something happen and the linux has crashed now every time i try to install or delete something he write me this:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.



please help me i cant install nothing

---

### Post by aysiu on 2009-11-12
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get remove --purge adobe-flashplugin
```

Then download this file from the Adobe website
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

Double-click the file.

---

### Post by mac9416 on 2009-11-13
Hey, lolp12,

It's going to take a little more than 'apt-get remove --purge'. adobe-flashplugin is stubborn. Try these commands...

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

You may want to replace the last command with aysiu's instructions to install flashplayer.

Good luck!

---

