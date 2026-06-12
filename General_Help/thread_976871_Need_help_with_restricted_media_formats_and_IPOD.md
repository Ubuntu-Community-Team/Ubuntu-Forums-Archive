---
title: "Need help with restricted media formats and IPOD"
date: 2008-11-09
forum: General Help
---

### Post by jdunn on 2008-11-09
I've been a Kubuntu user for years but in light of the 8.10 release, I am not impressed with the new KDE 4 so I decided to switch to Ubuntu with the Gnome desktop.  I have some questions:

1)  I notice there is no default package handler application like there was in Kubuntu.  How do people normally get around this, besides using "Add/Remove Applications" or apt-get from a terminal?

2)  I haven't found any online documentation yet for installing restricted media formats (mp3, commercial DVD, Quicktime, etc) in 8.10.  How do I install these?

3)  Kubuntu would automatically recognize and mount my Ipod via Firewire connection but this isn't happening for me in Ubuntu.  I installed Amarok which I plan to use to access my Ipod.  Are there instructions for getting the Ipod to automount?

---

### Post by m_duck on 2008-11-09
1. In Ubuntu, "synaptic" is the gui package manager (equivalent to adept in kubuntu).
```
sudo apt-get install synaptic
```2. You need the [medibuntu repository](https://help.ubuntu.com/community/Medibuntu) and some packages from it (namely w32codecs (or w64codecs for 64bit) and libdvdcss2) - [Restricted formats in ubuntu]("https://help.ubuntu.com/community/RestrictedFormats")
([Comprehensive Multimedia Howto]("http://ubuntuforums.org/showthread.php?t=766683"))

3. Not sure about ipods.

---

### Post by jdunn on 2008-11-09
Synaptic is already installed but I can't find it in the Gnome Applications or System menus.

---

### Post by SuperSonic4 on 2008-11-09
```
sudo synaptic
``` from a terminal will load it up.
```
gksu synaptic
``` from alt+f2

---

### Post by m_duck on 2008-11-09
It should be under System -> Administration -> Synaptic Package Manager ?

---

### Post by jdunn on 2008-11-09
> **m_duck said:**
> It should be under System -> Administration -> Synaptic Package Manager ?

Thanks.  I am not familiar with Gnome.

Also, why does Totem seem like such a lousy DVD player?  I'm used to Kaffeine.  Totem would be okay if the actions from the "Go" menu worked.  I can't go to previous or next chapters and I can't get to the DVD title menu.

I've got restricted formats, java and flash installed.  Still haven't figured out the Ipod problem yet.

---

