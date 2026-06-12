---
title: "Can I Skype?"
date: 2008-09-16
forum: General Help
---

### Post by pwaugh on 2008-09-16
My fiance is currently in Poland, and on a Windows box.  We both have Skype, but I'd like to be able to not have to dual boot into Windows to use it.

Is there a way I can contact/see her on Skype right from Ubuntu?

Patrick

---

### Post by howefield on 2008-09-16
why not install skype into Ubuntu ?

Press "System -> "Administration" -> "Software Sources".  Under Third Party Software, press Add.

Enter the following and press "Add Source":
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

In terminal type:  wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

In terminal type     sudo apt-get install skype

---

### Post by ManqueM on 2008-09-16
Skype is available for linux and ubuntu.

Go to skypes web page and download the .deb installation file (easy) or add the skype repository to your repositories to get automatic updates (a little more difficult but still easy).

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by MJWitter on 2008-09-16
I use skype on my Ubuntu PC..  I installed it through Synaptic using the MediBuntu Repo's.

Alternatively, go to the Skype website and dowload the .deb file for ubuntu and that should work.

Hope this helps

---

### Post by pwaugh on 2008-09-16
Thanks guys, I thought I had read it wasn't available.  Got it and now I can not miss my girl so much.

Patrick

---

### Post by tommygunner on 2008-09-19
The linux version looks pretty dated compared to the Windows version. If you want more functionality run the Windows version via wine.

---

