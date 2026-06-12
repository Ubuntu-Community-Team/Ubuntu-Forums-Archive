---
title: "Error!"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by Da CalebMan on 2009-08-02
Hey guys, I tried to install Adobe flash, and when I did, I got this error message:

"An error occured, please run package manager from the right click menu or apt-get to see what's wrong. The error message was" 'Unknown Error:'<type 'exceptions.SystemError>' (E:The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.) 'This usually means that you're installed packages have unmet dependencies."

No idea what this means! 

I can't run synaptic, it just shows the same error message and exits.
I don't know any specific commands either. Could someone help me out?

Thanks, 
~Caleb...

---

### Post by Partyboi2 on 2009-08-02
Hi, open a terminal (Applications>Accessories>Terminal) and move the adobe-flashplugin postinst file out of the way
```
sudo mv /var/lib/dpkg/info/adobe-flashplugin.postinst /var/lib/dpkg/info/adobe-flashplugin.postinst.old


```
then try remove the package
```
sudo apt-get remove  adobe-flashplugin
``` then reinstall
```
sudo apt-get install  adobe-flashplugin
```

---

### Post by Da CalebMan on 2009-08-03
Hello again,

I tried what you said, but it just gave me the same error.

> caleb@caleb-desktop:~$ sudo mv /var/lib/dpkg/info/adobe-flashplugin.postinst /var/lib/dpkg/info/adobe-flashplugin.postinst.old
caleb@caleb-desktop:~$ sudo apt-get remove  adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Indigo]E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.[/COLOR]
caleb@caleb-desktop:~$ 
I thought there'd by a more simple way to uninstall broken packages.

---

### Post by Partyboi2 on 2009-08-04
Try
```
sudo apt-get -f install
``` if that does not work try the reinstall option instead of remove.
```
sudo apt-get --reinstall install adobe-flashplugin
```

---

