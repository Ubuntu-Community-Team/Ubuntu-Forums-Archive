---
title: "Installing Updates"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by themagicmanfromtrent on 2008-12-22
Ubuntu, for some strange and malformed reason, will not allow me to install any updates.

I get the "There are 161 Updates available arrow in the top right corner, and I click on it, where it displays all the updates available - in this case a total of 151MB. I then click install and it asks me for my password. I type in my password, and wait. It says reading package information, and then goes back to how it was before, after doing nothing.

How productive.

Can anyone help with this?

---

### Post by Kevbert on 2008-12-22
Please enter the following in terminal and post the result:
```
sudo apt-get update
```
What version of Ubuntu are you using ? You can find this out in terminal with
```
uname-a
```
Please also post your /etc/apt/sources.list file.

---

### Post by themagicmanfromtrent on 2008-12-22
```
dannyl@DAN:~$ sudo apt-get update
Hit http://archive.canonical.com intrepid Release.gpg
Ign http://archive.canonical.com intrepid/partner Translation-en_US
Hit http://archive.ubuntu.com intrepid Release.gpg
Ign http://archive.ubuntu.com intrepid/main Translation-en_US
Hit http://archive.canonical.com intrepid Release
Hit http://archive.canonical.com intrepid/partner Packages
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid-updates Release.gpg
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid-security Release.gpg
Ign http://archive.ubuntu.com intrepid-security/main Translation-en_US
Hit http://archive.canonical.com intrepid/partner Sources
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid-proposed Release.gpg
Ign http://archive.ubuntu.com intrepid-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-proposed/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com intrepid-proposed/universe Translation-en_US
Hit http://archive.ubuntu.com intrepid Release
Hit http://archive.ubuntu.com intrepid-updates Release
Hit http://archive.ubuntu.com intrepid-security Release
Hit http://archive.ubuntu.com intrepid-proposed Release
Hit http://archive.ubuntu.com intrepid/main Packages
Hit http://archive.ubuntu.com intrepid/restricted Packages
Hit http://archive.ubuntu.com intrepid/restricted Sources
Hit http://archive.ubuntu.com intrepid/main Sources
Hit http://archive.ubuntu.com intrepid/multiverse Sources
Hit http://archive.ubuntu.com intrepid/universe Sources
Hit http://archive.ubuntu.com intrepid/universe Packages
Hit http://archive.ubuntu.com intrepid/multiverse Packages
Hit http://archive.ubuntu.com intrepid-updates/main Packages
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://archive.ubuntu.com intrepid-updates/main Sources
Hit http://archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://archive.ubuntu.com intrepid-updates/universe Sources
Hit http://archive.ubuntu.com intrepid-updates/universe Packages
Hit http://archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://archive.ubuntu.com intrepid-security/main Packages
Hit http://archive.ubuntu.com intrepid-security/restricted Packages
Hit http://archive.ubuntu.com intrepid-security/restricted Sources
Hit http://archive.ubuntu.com intrepid-security/main Sources
Hit http://archive.ubuntu.com intrepid-security/multiverse Sources
Hit http://archive.ubuntu.com intrepid-security/universe Sources
Hit http://archive.ubuntu.com intrepid-security/universe Packages
Hit http://archive.ubuntu.com intrepid-security/multiverse Packages
Hit http://archive.ubuntu.com intrepid-proposed/restricted Packages
Hit http://archive.ubuntu.com intrepid-proposed/main Packages
Hit http://archive.ubuntu.com intrepid-proposed/multiverse Packages
Hit http://archive.ubuntu.com intrepid-proposed/universe Packages
Hit http://archive.ubuntu.com intrepid-proposed/restricted Sources
Hit http://archive.ubuntu.com intrepid-proposed/main Sources
Hit http://archive.ubuntu.com intrepid-proposed/multiverse Sources
Hit http://archive.ubuntu.com intrepid-proposed/universe Sources
Reading package lists... Done

```

Ibex:

```
Linux DAN 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux
```

---

### Post by taurus on 2008-12-22
Now run

```
sudo apt-get upgrade
```

---

### Post by Kevbert on 2008-12-22
Am I right in saying that proposed updates should not be selected, in Software Sources, due to stability or dependency issues ?

---

### Post by themagicmanfromtrent on 2009-01-20
turns out i had to remove the lock file:

(/var/cache/apt/archives/lock)

Thanks for your help!

---

