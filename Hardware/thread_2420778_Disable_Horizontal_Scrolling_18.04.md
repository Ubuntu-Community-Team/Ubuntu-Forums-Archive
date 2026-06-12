---
title: "Disable Horizontal Scrolling 18.04"
date: 2019-06-10
forum: Hardware
---

### Post by cessanfrancisco on 2019-06-10
Hello,

Does anyone know how to disable the horizontal scrolling feature in Ubuntu 18.04?

Thank you.

---

### Post by Xian on 2019-06-10
This info may be of use:

[https://askubuntu.com/questions/1130149/how-to-disable-horizontal-scrolling-in-ubuntu-18-04-in-terminal?answertab=votes#tab-top](https://askubuntu.com/questions/1130149/how-to-disable-horizontal-scrolling-in-ubuntu-18-04-in-terminal?answertab=votes#tab-top)

---

### Post by cessanfrancisco on 2019-06-10
Thanks. Yes, I did try that.

However when I ran this:

sudo gedit /usr/share/X11/xorg.conf.d/40-libinput.conf

I didn't have anything that referenced horizontal scrolling.

---

### Post by Xian on 2019-06-11
Try installing the xserver-xorg-input-libinput package and then edit the 40-libinput.conf file.

[https://packages.ubuntu.com/bionic/amd64/xserver-xorg-input-libinput/filelist](https://packages.ubuntu.com/bionic/amd64/xserver-xorg-input-libinput/filelist)

---

