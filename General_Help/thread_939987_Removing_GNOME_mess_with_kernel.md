---
title: "Removing GNOME mess with kernel?"
date: 2008-10-06
forum: General Help
---

### Post by Inane_Asylum on 2008-10-06
I want to install Ubuntu-eee on an eee 900, install XFCE, then remove GNOME...

Will removing GNOME (and all the packages that go with it) mess with the compatibility of Ubuntu with the eee?  The Ubuntu-eee kernel is specifically made for this computer, and I don't know if removing **packages** will affect the **kernel.**:confused:

---

### Post by secondstage on 2008-10-07
To my knowledge, removing gnome will not affect the kernel. If you would like to use XFCE instead of gnome, then...
1. Open Terminal (Applications > Accessories > Terminal)
2. Type...
```
sudo aptitude install xubuntu-desktop
```
3. Logout
4. Go to sessions, and select XFCE
5. Login With the same username and password.
6. To go back to gnome, repeat steps 4, and 5, but instead of selecting XFCE, select gnome.

NOTE: You may not get the Notebook Remix thing if you run XFCE.

---

### Post by Inane_Asylum on 2008-10-08
Meh, </3 netbook remix...

Got XFCE installed, and it's working great.  The only thing I can't get working is the mic, but that's nothing new.  Apparently, it's not possible, but I've hard that before...not giving up yet.

---

### Post by secondstage on 2008-10-08
thats good to hear and I was glad to help. I sadly don't know anything about how to get the mic working.

---

