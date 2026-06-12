---
title: "Will I lose my applications after an upgrade?"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2009-05-03
When I was about two steps through my upgrade I check the details windows. It shows that it would uninstall lots of packages including blender(3D modelling package). Will i lose this application after the upgrade?

---

### Post by aysiu on 2009-05-04
You shouldn't lose any applications during an upgrade, but if you do, you can always just reinstall them. All your settings will still be there even if you uninstall and reinstall.

---

### Post by lovinglinux on 2009-05-04
Just to be safe, do this before upgrading:

```
dpkg --get-selections > ~/my-packages
```

This will save a file called *my-packages* in your home directory. 

If something goes wrong during the update, you can use the file *my-packages* to restore all installed software with this commmand:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

It will download and install all the programs for you, except those that you installed manually, if they are not already in the new repository.

This method is particularly useful if you want to do I clean install and reinstall all your favorite software at once, but I think it can also be used on upgrades, because if something is already installed it won't be installed twice.

---

