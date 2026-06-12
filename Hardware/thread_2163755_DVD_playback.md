---
title: "DVD playback"
date: 2013-07-19
forum: Hardware
---

### Post by blublood67 on 2013-07-19
New to Ubuntu and just wondering if DVD playback is an issue with anyone else?
Appreciate any comments or help.
Have a great day!!!

---

### Post by 2F4U on 2013-07-19
What exactly is your isssue? Did you install the restricted extras?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by slickymaster on 2013-07-19
DVD decryption is not included by default in Ubuntu because of legal reasons. DVD decryption allows you to watch DVD movies on your computer.
To get DVD decryption, you need to install the restricted formats file. To do it open a terminal window and run the following commands:```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```The first command puts the necessary files on your computer to read the DVD's and the second will install and enable the first command. After that reboot your computer and use Totem or VLC to watch your DVD's.

---

