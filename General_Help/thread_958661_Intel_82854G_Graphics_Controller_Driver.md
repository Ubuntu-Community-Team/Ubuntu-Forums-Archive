---
title: "Intel 82854G Graphics Controller Driver"
date: 2008-10-25
forum: General Help
---

### Post by Pccw9 on 2008-10-25
I recently installed Ubuntu 8.04 on my desktop computer. The Screen Res, is way out of whack, and i went searching for the driver for my graphics card. I found it on intels website, and it was downloaded as a .tar.gz or something like that. Im new to this, so i dont know exactly how to install this driver on the Ubunutu machine. I downloaded the file with another computer and transfered over with a usb flash drive. 
Also,i accidently deleted the taskbar on the bottom, where the windows get minimized. how do i get that back?

---

### Post by xeth_delta on 2008-10-25
Welcome to the forum.

What do you mean by your resolution problem? Is it perhaps that you have a wide screen and the image is stretched to cover the screen? There is an easy solution to that, but first give us some more information.

Open a terminal and type the following commands. Please post the output of the commands between CODE tags (see the # button in the posting page):

```
lshw -C video
```
```
cat /etc/X11/xorg.conf | grep -i driver
```

---

### Post by Pccw9 on 2008-10-25
its ok, i figured it out, thanks! i just went to screens and graphics and my card was supported as=nd i fixed my screen resolution. Thank you for your help

---

