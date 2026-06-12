---
title: "Wacom Bamboo Pen tablet not working?"
date: 2011-01-22
forum: Hardware
---

### Post by Siramau on 2011-01-22
Last week, after having issues with my three-month-old install, I reinstalled Ubuntu. Today, I went to use my Wacom Bamboo Pen tablet, and it didn't work. I checked and made sure xserver-xorg-input-wacom was installed, it was. I reinstalled it, rebooted, but it didn't help. After some googling, I ran

[FONT=monospace][/FONT]```
 sudo add-apt-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get install wacom-dkms

```

and rebooted, but it is still not working. Any help is appreciated.

---

### Post by Favux on 2011-01-22
Hi Siramau,

Uninstall the dkms wacom package and follow the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  That should get your Bamboo working.

---

