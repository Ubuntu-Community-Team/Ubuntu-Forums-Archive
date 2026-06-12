---
title: "Drivers for Samsung ML-2955DW printer (B&amp;W)"
date: 2012-01-20
forum: Hardware
---

### Post by VinnyJ1701 on 2012-01-20
Hey all,

I'm posting his as Xubuntu, bit I would assume this works on any variant. Yesterday (Thursday Jan 19 2012) I bought a Samsung ML-2955DW Wireless Laser Printer (Black & White).

The software CD includes drivers for "various Linux OSes" But after trying this setup a few times, I stopped. It is quite difficult to get the install GUI to work and when I got it to work, it caused the computer to reboot in the middle of the install.  Useless.

Going back to the Ubuntu printer setup, that comes with Xubuntu, I just kept trying Samsung drivers that I thought might work. Well one did. The Samsung ML-3050, 2.0.0 driver works great.  Hope this information helps someone out there

Peace

Vince
Friday Jan 20 2012

---

### Post by rtalcott on 2012-02-23
Thank You!  That solved my problems with this printer!
rt

---

### Post by VinnyJ1701 on 2012-02-28
> **rtalcott said:**
> Thank You!  That solved my problems with this printer!
rt

Glad to help..

Peace

Vince

---

### Post by mastablasta on 2012-02-28
the ones that come with printer are apparently not good. not sure what theier testing os is and why they include crappy drivers. additionally i don't udnerstand their policy on not using the provided fixes. 
anyway there is a PPA for them: 
[http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)
or here:
[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)
 
works great on Ubuntu as well as Debian.

---

### Post by beatngu13 on 2012-10-04
Due to the fact that the ML-3050 doesn't offer duplex printing, which the ML-2955DW does, this feature is not available. I tried out a couple of other drivers, but the ML-3050 driver is the only one I can print with, so thank you for that!

Any ideas how to use the duplex function?

EDIT: Use the Samsung ML-3051ND, 2.0.0 driver. Works perfect so far!

---

### Post by mmyheqa on 2012-11-14
This works for me!

Link: [http://ubuntuforums.org/showthread.php?t=341621&page=102]("http://ubuntuforums.org/showthread.php?t=341621&page=102")

```
sudo bash -c 'echo "deb http://www.bchemnet.com/suldr/ debian extra" >> /etc/apt/sources.list'

wget -O - http://www.bchemnet.com/suldr/suldr.gpg | sudo apt-key add -

sudo apt-get update

sudo apt-get install  samsungmfp-driver  samsungmfp-configurator-qt4

/opt/Samsung/mfp/bin/Configurator&
```

---

### Post by jmeurin on 2012-11-28
Thanks a lot, I kept getting garbage with the ML-2950 driver, the ML-3051ND-en, 2.0.0 driver seems to be working a lot better.

---

### Post by gkrao on 2013-02-09
The driver for Samsung 3010 version 2.0.0 worked fine for me too. I did not try the other ones. So, if this happens to stop working, then I will try the other ones.

Thanks to the original poster.

Gopal

---

