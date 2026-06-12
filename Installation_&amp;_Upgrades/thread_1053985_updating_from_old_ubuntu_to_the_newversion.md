---
title: "updating from old ubuntu to the newversion"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by dxlwebs on 2009-01-29
if i remember correctly when some otherpoeple updated their ubuntu they lost all their files is this true !

will updating the the latest version lose all m files

thanks for your help

---

### Post by taurus on 2009-01-29
Are you talking about your personal files (in $HOME)?  No.

Which release are you running now and which one do you plan to upgrade to?

Applications -> Accessories -> Terminal
```
lsb_release -a
```

---

### Post by dxlwebs on 2009-01-29
currently i use Ubuntu Linux 8.04.1 i would like to update the the latest release

and yes i mean all my personal files and my websites and server settings will i lose them and how would i go about updating thank you for your replies

---

### Post by taurus on 2009-01-29
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by slakkie on 2009-01-29
> **dxlwebs said:**
> currently i use Ubuntu Linux 8.04.1 i would like to update the the latest release

and yes i mean all my personal files and my websites and server settings will i lose them and how would i go about updating thank you for your replies

An upgrade should not impact /most/ of your files. Configuration files can change (this is due to the fact that new directives are added by the application, or they are removed). But usually the upgrade process warns you when this happens and will ask you to make a diff, install it, keep the current version.

Your own files, located in /home/youruser will not be touched by the upgrade. If you have /home on a different slice then your OS is installed you can even switch distro without having to worry about your personal files.

---

