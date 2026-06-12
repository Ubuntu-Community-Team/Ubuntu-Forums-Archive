---
title: "Nvidia drivers fail to install"
date: 2013-08-06
forum: Hardware
---

### Post by birch2 on 2013-08-06
I'm trying to install official nvidia drivers after a new install and it fails everytime. I've tried deleted nouveau before, but still nothing. It just says install fails and to check a file. The file is just the questions it asked me and nothing else. I've had to reinstall several times because of this since even the ctrl+alt+F1 thing won't open.
I also tried using jockey and the x-swat ppa but they don't work either. Im using the latest ubuntu and have a gtx 570 if that matters.

Can someone suggest anything? This problem is quite aggrevating :mad:

---

### Post by grahammechanical on 2013-08-07
I do not think it is good to delete the Nouveau driver as you then do not have a video driver except a basic VGA driver. Someone once gave me instructions for installing Nvidia drivers using the command line. I never used these instructions as I prefer using the Additional Driver utility to change video drivers. But from those instructions I see that we have to stop lightdm before we run the command to install the Nvidia driver and then we have to start lightdm once the driver is installed. I see nothing about deleting Nouveau.

```
sudo service lightdm stop
```
```
sudo service lightdm start
```

Regards.

---

### Post by birch2 on 2013-08-07
I've tried that since it's required. It doesn't do anything

---

### Post by birch2 on 2013-08-07
Fixed it myself, jockey decided to work :tongue:

---

