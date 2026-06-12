---
title: "Toshiba Protege M205 Tablet PC"
date: 2009-01-14
forum: Hardware
---

### Post by l0c0dantes on 2009-01-14
I am thinking of getting this on craigslist, and putting ubuntu on it. How compatible do you imagine it would be? Would the tablet work fine?

---

### Post by after9 on 2009-01-14
I'm posting from one right now, I just made the conversion from Windows XP a few days ago.

It was fairly painless.  The only thing I'm still struggling with is graphics performance.  I'm not sure if it's my drivers or what, but it takes a few tries for the screen to rotate properly and most windows take a very long time to draw.

Getting the pen working was a breeze and Xournal is a very nice switchover from journal.  I followed the following guide (but went with Kubuntu - don't get me started on KDE 4.1.3 though).

[http://www.intilinux.com/howto/531/toshiba-portege-m200m205-tablets-on-ubuntu/](http://www.intilinux.com/howto/531/toshiba-portege-m200m205-tablets-on-ubuntu/)

Good luck

---

### Post by l0c0dantes on 2009-01-15
Well, the basic install went fine (Used alternate install CD, the regular one has never worked well for me), along with the synaptic updates, However, when I try to sudo gedit /etc/X11/xorg.conf It only populates a very basic setup, without using the nvidia driver at all

---

### Post by Favux on 2009-01-15
Hi l0c0dantes,

That's normal for Intrepid.  With Intrepid Ubuntu started switching over to HAL (hardware abstraction layer) which supports USB hotplugging, etc.  If your tablet pc just has a stylus it's also suppose to work through HAL.  But you can go back to xorg.conf if you want.  Just plug in Hardy Heron or earlier entries.

Go to Hardware Drivers and install nVidia proprietary drivers.  You should see some xorg.conf change associated with that.

---

