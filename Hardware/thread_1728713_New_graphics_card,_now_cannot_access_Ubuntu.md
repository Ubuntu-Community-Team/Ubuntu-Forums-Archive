---
title: "New graphics card, now cannot access Ubuntu"
date: 2011-04-14
forum: Hardware
---

### Post by thenovelist on 2011-04-14
I have a 64bit Ubuntu which I cannot access since I updated my graphics card yesterday.  It loads up to the boot sequence page where 4 dots light up whilst its loading.  Then it goes to a black text screen to log in.  It asks me for my log in details and that is it it just has $Tony (not sure about the $ sign but you get my drift).  How is there away to over come this?  Otherwise I shall have to reload Ubuntu and that is not a real option I want to do if poss.  The graphics card is a GeForce GTX 550Ti.  Looking forward to your replies

---

### Post by thenovelist on 2011-04-14
Anyone?  I am sure there is an answer and I can't find it

---

### Post by Hippytaff on 2011-04-14
You might need to install the driver. At the grub menu (the bit where you choose os) highlight ubunt and press e. then change 'quite splash' to 'nomodeset'. Then CTRL+X to boot. If you get to the desktop check system -> administration -> hardware drivers or additional drivers to see if you are offered a driver to install.
 
If you are not dual booting you have to hold down SHIFT at boot to get to the grub screen

---

### Post by Yellow Pasque on 2011-04-14
Support for the card was just added in a pre-release driver: [http://www.phoronix.com/scan.php?page=news_item&px=OTMyNA](http://www.phoronix.com/scan.php?page=news_item&px=OTMyNA)

---

### Post by thenovelist on 2011-04-16
Thanks for all your help and links, but nothing worked.  I shall I think have to reload and hope it supports the card?!  But, I shall hang on for a while to hope that someone has a good idea to resolve it.

Thank you again

---

### Post by Yellow Pasque on 2011-04-16
What version of Ubuntu are yo using? If 10.10, see: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) for latest driver.

---

### Post by thenovelist on 2011-04-16
Yes I am using 10.10, but to load the above I have to have access to Ubuntu, so I would have to reload Ubuntu to access it I guess? :confused:

---

### Post by Yellow Pasque on 2011-04-16
> **thenovelist said:**
> Yes I am using 10.10, but to load the above I have to have access to Ubuntu, so I would have to reload Ubuntu to access it I guess? :confused:
No, just boot to safe mode (hold shift while grub loads to get the menu) and choose recovery console with network access.
If you have an existing xorg.conf, delete it or back it up:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Install new driver:
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers
```

---

### Post by thenovelist on 2011-04-17
Thank you.  It is now working and its been quite a journey getting here!  All that I need to do is get FF4 working as I can't see it on the updates?  Thank you

---

