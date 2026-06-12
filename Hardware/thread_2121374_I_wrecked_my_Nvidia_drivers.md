---
title: "I wrecked my Nvidia drivers"
date: 2013-03-01
forum: Hardware
---

### Post by Nesaskewatch on 2013-03-01
I have an Asus N56 VJ-SH71 that has an NVIDIA GeForce GT 635M. I have been trying to install drivers so I can use the gpu in Ubuntu 12.10. I ran ```
sudo apt-get install nvidia-current
sudo nvidia-xconfig
``` On the next boot Ubiquity stopped working and I had a 640x480 screen. I was unable to open xconfig nor anything else aside from the terminal but I have no idea what I could do in teminal anyway, so I purged that nvidia driver and hoped everything would return to normal. Ubiquity returned but ever since I am stuck with a 640x480 display. I tried to change that in display settings but it shows no other option than 640x480. 

Thanks in advance for any help.

---

### Post by Yellow Pasque on 2013-03-01
Delete /etc/X11/xorg.conf:
```
sudo rm /etc/X11/xorg.conf
```
Then, log out to restart X. Is all back to normal? If so, and your laptop has Optimus/hybrid graphics ('lspci | grep  -i vga' will show intel and nvidia GPU), then you follow: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Nesaskewatch on 2013-03-01
Thanks! I was able to set the display back to normal. I will follow the Bublebee instructions next. Saved my bacon, you did. :)

---

