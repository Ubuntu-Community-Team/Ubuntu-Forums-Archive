---
title: "universal applet"
date: 2008-10-19
forum: General Help
---

### Post by krishna1650 on 2008-10-19
how to install universal applet in ubuntu 8.04 through terminal or graphically ?

---

### Post by Sam on 2008-10-19
Maybe I'm missing something, but what is "universal applet" ?

---

### Post by DarknessssenkraD on 2008-10-19
Did you mean "Universal Applets"?
[http://forum.compiz-fusion.org/showthread.php?t=8522](http://forum.compiz-fusion.org/showthread.php?t=8522)

---

### Post by krishna1650 on 2008-10-20
> **DarknessssenkraD said:**
> Did you mean "Universal Applets"?
[http://forum.compiz-fusion.org/showthread.php?t=8522](http://forum.compiz-fusion.org/showthread.php?t=8522)

yes you are right. i want to know how to install it by terminal with apt-get or aptitude command.

---

### Post by DarknessssenkraD on 2008-10-20
Did you follow the link?

Repos for most distros are now here:

```


Deb-based:
deb [http://download.opensuse.org/repositories/home:/some-guy:/screenlets/DISTRO_HERE/](http://download.opensuse.org/repositories/home:/some-guy:/screenlets/DISTRO_HERE/) ./

RPM-based:
rpm [http://download.opensuse.org/repositories/home:/some-guy:/screenlets/DISTRO_HERE/](http://download.opensuse.org/repositories/home:/some-guy:/screenlets/DISTRO_HERE/) ./

Distro names are:
Debian_Etch
Fedora_9
Mandriva_2008
openSUSE_10.2
openSUSE_10.3
openSUSE_11.0
openSUSE_Factory
xUbuntu_7.04
xUbuntu_7.10
xUbuntu_8.04

```
So if you are using Ubuntu 8.04

```
sudo gedit /etc/apt/spurces/list
```

add at the end the right version:
```
deb [http://download.opensuse.org/repositories/home:/some-guy:/screenlets/xUbuntu_8.04/](http://download.opensuse.org/repositories/home:/some-guy:/screenlets/xUbuntu_8.04/) ./
```

then
```
sudo apt-get update
```

```
sudo apt-get install universal-applets universal-applets-extras
```

---

### Post by gdebat on 2008-11-22
> So if you are using Ubuntu 8.04

Code:

sudo gedit /etc/apt/spurces/list



typo correction:


```
sudo gedit /etc/apt/sources.list
```

---

