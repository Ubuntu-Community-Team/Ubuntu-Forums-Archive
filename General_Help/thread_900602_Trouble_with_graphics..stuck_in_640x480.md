---
title: "Trouble with graphics..stuck in 640x480"
date: 2008-08-25
forum: General Help
---

### Post by blop on 2008-08-25
Hi all, 

Im having a random issue installing the nvidia drivers. I have installed them loads of times on different kit but for some reason the pc that worked fine in Gutsy is having an issue in Hardy.

Ubuntu detects correctly i have nvidia hardware and offers the driver from Hardware Drivers. I install it and reboot it, and it states that it is In Use. However i see no benefit and i cant get out out of 640 x 480.

Really weird...

The card is an XFX 7600 GS.

cheers

---

### Post by sricketts on 2008-08-25
In my experience resolution issues can usually be fixed with some surgery to /etc/X11/xorg.conf. 

Now that I think about it those issues were usually caused by switching monitors -- not graphics cards. But you might want to look at your configuration anyway if you haven't already.

-SR-

---

### Post by SammerHammer on 2008-08-25
Enable restricted drivers if you haven't already,install nvidia-settings, sudo aptitude install nvidia-settings, and then start it using gksudo nvidia-settings.

Once in the main window, choose xserver configuration, in the resolution dropdown menu, click Auto, then click save to xorg configuration, exit and reboot computer. If your computer reverts to the old 640x840 after this, use the Screen Resolution menu in System>Administration to try and fix it.

Hope this helps.

---

### Post by blop on 2008-08-25
Thanks for the advice...

I did all the instructions regarding Nvidia settings but none helped...so i switched monitors as hinted at and it works fine!

is it possible my orginal monitor is not supported? 

GBM Ray System Technology INC Model # F173

I know that is capable of high res etc from using it on that terrible OS that we need not mention :lolflag:

---

