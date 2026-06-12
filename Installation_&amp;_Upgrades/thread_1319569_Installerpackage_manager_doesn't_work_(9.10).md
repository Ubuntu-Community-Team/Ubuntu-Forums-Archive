---
title: "Installer/package manager doesn't work (9.10)"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by usawrestler_9 on 2009-11-08
hey all,
I've recently installed 9.10 and after installing the updates and getting my computer set up I cant install anything, not from the software library or even flash. there is a red circle with a white line in it on my status bar and when I roll over it it says... *An error occurred, please run package manager from the right-click menu or apt-get in a terminal to see what is wrong.  the error message was: 'unknown error: '<type 'exceptions.systemerror'>' (E:the package adobe-flashplugin needs to be reinstalled, but i can't find and archive for it.)'this usually means that your installed packages have unmet dependencies*

---

### Post by jacquez on 2009-11-08
I am seeing this same problem.  Any luck fixing it?

---

### Post by qianshiming on 2009-11-09
me too!

---

### Post by michy99 on 2009-11-09
Make sure you have enabled the partner repositories.

---

### Post by usawrestler_9 on 2009-11-09
how do i do that?

---

### Post by michy99 on 2009-11-09
Go to System->Administration->Software Sources. Click on 'Other Software' tab. Make sure that these line are checked:```
http://archive.canonical.com/ubuntu karmic partner
http://archive.canonical.com/ubuntu karmic partner (Source Code)
```Exit and try updating again.

---

### Post by usawrestler_9 on 2009-11-09
looks like that did the trick...thanks michy

---

### Post by GGU on 2009-11-11
It does not work for me. 
The update don't work ("canot remove flashplugin-nonfree" ) and ask me to do a reinstall it.
the reinstall is not possible using the Sympatic manager.
I tryed  "sudo apt-get install --reinstall flashplugin-nonfree" but the answer is :
unsatisfied dependencies, try "apt-get -f install".

how can I cut this deadlock?

---

### Post by mac9416 on 2009-11-11
Hey, GGU,

Try these commands. They have worked for a lot of folks...

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

Good luck!

---

### Post by GGU on 2009-11-12
Thank you Mac.

The adobe-flashplugin package was not installed but I try your commands on flashplugin-nonfree and it worked.

---

