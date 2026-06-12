---
title: "switching between kde and gnome"
date: 2008-08-15
forum: General Help
---

### Post by pikaia on 2008-08-15
Hey.

I've configured my ubuntu desktop the way I like it so I don't want to lose it.  However, I've tested out some KDE distros that I really like and wanted to install KDE.  I know its possible to install both and switch at login, my question is:  Is this safe for keeping my current setup, or is it likely that I'll have my Gnome desktop revert to default... or some other horror.  

What could/should I expect by installing the kubuntu-desktop?  And is KDE4 worth installing (stable)?

Thanks for the insight.

---

### Post by ajmorris on 2008-08-15
> **pikaia said:**
> Hey.

I've configured my ubuntu desktop the way I like it so I don't want to lose it.  However, I've tested out some KDE distros that I really like and wanted to install KDE.  I know its possible to install both and switch at login, my question is:  Is this safe for keeping my current setup, or is it likely that I'll have my Gnome desktop revert to default... or some other horror.  

What could/should I expect by installing the kubuntu-desktop?  And is KDE4 worth installing (stable)?

Thanks for the insight.

It is completely safe to install kubuntu-desktop, and keep your gnome settings intact. The install of kde will not affect these, and gnome will not revert to default :) And at your login display, you can just choose between the one you want to log into. As for kde4.... kde4.1 is stable according to upstream... the best you can do is install it and see for yourself ;)

AJ

---

### Post by PCessna on 2008-08-15
> **ajmorris said:**
> It is completely safe to install kubuntu-desktop, and keep your gnome settings intact. The install of kde will not affect these, and gnome will not revert to default :) And at your login display, you can just choose between the one you want to log into. As for kde4.... kde4.1 is stable according to upstream... the best you can do is install it and see for yourself ;)

AJ

IT's 100% safe, You'll have to give up the ubuntu start-up splash, which is sometimes very hard, even impossible to get back, and the shut-down splash too, also login screen which has a VERY easy fix.

---

### Post by tech0007 on 2008-08-15
Only change when you login to either desktop is you'll have additional menus for the applications from the other DE.

---

### Post by pikaia on 2008-08-16
Alright, I bit the bullet and installed.  Its great!  Thanks.  Only problem is that I run Cairo-dock in my Gnome desktop and it runs great, but in KDE its surrounded by a black border/blackground.  I haven't been able to find a cause for this.  Any thoughts?

Thanks again.

EDIT:  Got it working.  Needed to enable translucency in KDE.  Thanks again.  Now to decide whether or not this should be default!

---

### Post by ajmorris on 2008-08-16
> **PCessna said:**
> IT's 100% safe, You'll have to give up the ubuntu start-up splash, which is sometimes very hard, even impossible to get back, and the shut-down splash too, also login screen which has a VERY easy fix.

It is actually extremely easy to get the ubuntu start-up splash back, just do:
```
sudo update-alternatives --config usplash-artwork.so && sudo update-initramfs -u

```

And if you want a custom spash screen, see:
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto) 

AJ

---

### Post by PCessna on 2008-08-16
> **ajmorris said:**
> It is actually extremely easy to get the ubuntu start-up splash back, just do:
```
sudo update-alternatives --config usplash-artwork.so && sudo update-initramfs -u

```

And if you want a custom spash screen, see:
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto) 

AJ

After my failure, I just disable the whole entire usplash and everything related to asking or wanting uspalsh to run or see or whatever and I find a faster bootup and no need to go to the stress of reverting it back.

---

