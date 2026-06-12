---
title: "Kde 3.5.1"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by thepocketdrummer on 2006-02-15
How in the WORLD do I get KDE 3.5.1 on there? I did those two lines of code, but how do I do the dep part? It makes no sense to me.

---

### Post by niviche on 2006-02-15
You are reffering to this, right?
[http://kubuntu.org/announcements/kde-351.php](http://kubuntu.org/announcements/kde-351.php)

Edit your repositories:

```

sudo kate /etc/apt/sources.list

```

paste this in the file:

```

http://kubuntu.org/packages/kde351 breezy main

```

go to Adept Updater, and update. :) Have fun.

---

### Post by thepocketdrummer on 2006-02-15
But, how exactly do I update it. I've done all that, but I'm still running KDE 3.4.3

---

### Post by thepocketdrummer on 2006-02-15
I tried typing
```
sudo apt-get update
sudo apt-get dist-upgrade
```

and it said that these were held back.

> 
akregator
ark
artsbuilder
kaddressbook
kamera
kappfinder
karm
kate
kaudiocreator
kcontrol
kcron
kdeadmin-kfile-plugins
kdebase-bin
kdebase-kio-plugins
kdegraphics-kfile-plugins
kdelibs-bin
kdelibs4c2
kdemultimedia-kfile-plugins
kdemultimedia-kio-plugins
kdenetwork-filesharing
kdenetwork-kfile-plugins
kdepasswd
kdepim-kio-plugins
kdepim-wizards
kdeprint
kdesktop
kdm
kfind
kghostview
khelpcenter
kicker
klaptopdaemon
klipper
kmenuedit
kmilo
kmix
knetworkconf
knotes
konq-plugins
konqueror
konqueror-nsplugins
konsole
kontact
kooka
kopete
korganizer
kpdf
kpf
kppp
krdc
krfb
kscd
kscreensaver
ksmserver
ksnapshot
ksplash
ksvg
kuser
kwalletmanager
kwifimanager
kwin
libkcddb1
libkonq4
libkpimexchange1
libkpimidentities1
libkscan1
libksieve0
libktnef1

---

### Post by thepocketdrummer on 2006-02-15
I also realized the kubuntu-desktop package is not installed... should it be?

---

### Post by Lord Illidan on 2006-02-15
Try and do the upgrading from synaptic..

EDIT : yes, ubuntu-desktop should be installed.

---

### Post by thepocketdrummer on 2006-02-15
> There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.

This is what it said when I tried to get kubuntu-desktop from adept.

---

### Post by thepocketdrummer on 2006-02-15
when I do
```
sudo apt-get install kubuntu-desktop
```

it says,
> Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kmail but it is not going to be installed
                   Depends: ksysguard but it is not going to be installed
E: Broken packages


---

### Post by thepocketdrummer on 2006-02-15
Now firefox is all messed up... ARGH!!!

---

### Post by thepocketdrummer on 2006-02-15
Please, if anyone knows how to fix this problem, tell me. I have already reformatted 3 times just trying to get Ubuntu on correctly and be able to update it. I finally got the update to work, but now i'm afraid I messed up the OS by trying to get KDE 3.5.1.

PLEASE help.

---

