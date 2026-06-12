---
title: "[SOLVED] Ubuntu Boo Screen"
date: 2008-10-04
forum: General Help
---

### Post by cocopeanut on 2008-10-04
When I boot my computer, the Ubuntu boot screen's resolution is too high for my monitor, therefore the logo is off center and not clear and my monitor says "out of range". It fixes itself as soon as the desktop environment loads. I know I'm just being petty, but I would like it to look nice. Any way I can change the resolution on that boot screen?

I'm a noob so detailed instructions would be greatly appreciated. :) I'm running Ubuntu 8.04.

-=-Oscar-=-

---

### Post by cocopeanut on 2008-10-11
I found an answer to my problem on the following website: [http://techupdate.blogvis.com/2008/02/05/ubuntu-boot-screen-problems/](http://techupdate.blogvis.com/2008/02/05/ubuntu-boot-screen-problems/)

In short:

1) Go to Applications-->Accessories-->Terminal
2) type: > sudo gedit /etc/usplash.con
3) This opens up a file where you can enter you X and Y values for your resolution. For example, for 1024x768:

> # Usplash configuration file
xres=1024
yres=768

4) Save the file and exit
5) In the same terminal window type: > sudo update-initramfs -u -k `uname -r`

6) Reboot

Thanks,

-=-Oscar-=-

---

