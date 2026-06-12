---
title: "Synaptics broken"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by jeparker on 2009-10-30
I was trying to install the packages for flash player and I didn't download the package I just clicked to open with package installer in firefox. The install messed up and gave me this error

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Now every time I open synaptics package manager it gives me this error and closes. I have since downloaded the package to my downloads folder and every time I double click it I get
gdebi-gtk
could not open
'install_flash_player_10_linux.deb'
the package may be corrupted or you are not allowed to open the file. Check permissions of the file.

I checked the permissions and they are all ok.
I am runnin kaola dual boot with vista. Any help would be appreciated. sorry if this is in the wrong forum.

---

### Post by mac9416 on 2009-10-30
Try these commands:

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

Hope that helps!

---

### Post by jeparker on 2009-10-30
It worked great. Thank you very much!:D
It has been about 15 years since I messed with Linux and really need to brush up on my shell commands.

---

