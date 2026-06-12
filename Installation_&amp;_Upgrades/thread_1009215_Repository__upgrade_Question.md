---
title: "Repository / upgrade Question"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by drizzamed on 2008-12-12
1. I am by far, not a linux expert so feel free to talk to me like a child.

2. I am wanting to updrade from 6.06 Dapper to 8 Hardy.

3. My checklist states to be sure that the "dapper-updates" software channel is enabled.

4. I have performed the: gksu update-manager command and downloaded my updates, then checked again but get the following repository error.

Could Not Download All Repository Indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://ports.ubuntu.com/ubuntu-ports/dists/dapper-backports/main/debian-installer/binary-powerpc/Packages.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/dapper-backports/main/debian-installer/binary-powerpc/Packages.gz:) 404 Not Found

My question is, what do I do to fix this or edit this link to the correct location and, is it necessary that I have this working to upgrade to Hardy using Update Manager?

---

### Post by zvacet on 2008-12-12
Go to your source list by typing in terminal

```
gksudo gedit /etc/apt/sources.list
```

and put # sign in front of backports line.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```


Afer that follow [this]("https://help.ubuntu.com/community/HardyUpgrades") instructions.

---

### Post by az on 2008-12-12
> **drizzamed said:**
> 1. I am by far, not a linux expert so feel free to talk to me like a child.

2. I am wanting to updrade from 6.06 Dapper to 8 Hardy.

3. My checklist states to be sure that the "dapper-updates" software channel is enabled.

4. I have performed the: gksu update-manager command and downloaded my updates, then checked again but get the following repository error.

Could Not Download All Repository Indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://ports.ubuntu.com/ubuntu-ports/dists/dapper-backports/main/debian-installer/binary-powerpc/Packages.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/dapper-backports/main/debian-installer/binary-powerpc/Packages.gz:) 404 Not Found

My question is, what do I do to fix this or edit this link to the correct location and, is it necessary that I have this working to upgrade to Hardy using Update Manager?

Try disabling the dapper-backports repository, updating your package list and try again.

---

### Post by drizzamed on 2008-12-12
In terminal, when I do the gksudo edit part of it, I'm receiving error:
(gksudo:18896): Gtk-Warning **: cannon open display:
root@mini-mac:~:

---

### Post by Ifaistos on 2008-12-12
May I suggest a more radical solution?

If you have /home on another seperate disk, or even in a different partition, why don't you try to make a bootable 8.1 ISO disk and install everything from the beginning.

If you have your /home on a different disk, you can format the boot disk as well.  All your settings and preferences will remain, as well your e-mails or backup files.

If you are not absolutely sure, then try to backup your boot disk, to be on the safe side.

Hope that helps.
:-)

---

