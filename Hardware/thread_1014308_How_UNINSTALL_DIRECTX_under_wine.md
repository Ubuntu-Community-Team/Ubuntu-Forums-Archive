---
title: "How UNINSTALL DIRECTX under wine"
date: 2008-12-17
forum: Hardware
---

### Post by warzt on 2008-12-17
2 days ago I install directx under wine by:
/usr/bin/wine "C:\DIRECTX\DXSETUP.exe"
But now I need to uninstall it and I have no idea about this. I did try
sudo apt-get remove directx
but it doesn't work! help please

---

### Post by Ng Oon-Ee on 2008-12-17
> **warzt said:**
> 2 days ago I install directx under wine by:
/usr/bin/wine "C:\DIRECTX\DXSETUP.exe"
But now I need to uninstall it and I have no idea about this. I did try
sudo apt-get remove directx
but it doesn't work! help please
It seems you're really new, so a bit of a quick explanation.

Firstly, this is a forum for hardware and laptops discussion. There's another one for Wine, you should have posted this question there. In future please check for the right sub-forum, people there will be more likely to know what theyr'e talking about.

apt-get (and aptitude etc) is the installer/uninstaller routine for Ubuntu and other Debian-based distros. This is how you install or uninstall programs within Ubuntu (think of it as add/remove programs on steroids).

Wine is one of those programs you can install. However, to install things within wine, you know that you have to run /usr/bin/wine folllowed by whatever setup needed. This is because you're not installing something to Ubuntu itself, but into the virtual Windows created by Wine.

As for uninstalling DirectX, uninstalling in Wine is a bit flaky. What I'd normally do is just delete the whole Wine folder (in Nautilus, open your home directory, type Ctrl-H to view hidden folders, your Wine install is stored in .wine). Of course, you then lose everything you have installed, including DirectX. If, as I'm guessing, the reason you want to uninstall directX is because of some game, you'll have to reinstall the game, as well.

---

### Post by binbash on 2008-12-17
I suggest removing wine folder instead of deleting directx.For this kind of cases, you can try playonlinux, which will create seperate wine folders.

---

