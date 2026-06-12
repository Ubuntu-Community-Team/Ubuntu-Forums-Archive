---
title: "Nvidia 6600GT problems - any solution?"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by bionnaki on 2007-11-29
hello. I have a Nvidia 6600GT card and im using a fresh install of gutsy. My resolution is very low (800x600) and it appears that I have no 3d acceleration. I have tried the Restricted Drivers tool under Preferences as well as Envy - and it still does not work. 

Anyone have any luck with this card? If so, how do you set it up?

thanks

---

### Post by bionnaki on 2007-11-29
the only clues ive found are here: [http://technical-itch.co.uk/2007/10/19/ubuntu-710-upgrade-first-impressions/](http://technical-itch.co.uk/2007/10/19/ubuntu-710-upgrade-first-impressions/)

can anyone confirm this? how did you get your card to work?

---

### Post by PmDematagoda on 2007-11-29
Try this:-

1) Download the [Nvidia drivers]("http://www.nvidia.com/object/unix.html") and install it through Recovery Mode according to the instructions given.

The following steps can be done in Recovery Mode so that it will be done more easily than in the normal mode.

2) Reconfigure the X-server using:-

```
sudo dpkg-reconfigure xserver-xorg
```
and select the driver as Nvidia.

3) After reconfiguration do:-

```
sudo startx
```

to see if your GUI works.

---

