---
title: "Zepto Znote V11a and touchpad problems"
date: 2009-10-28
forum: Hardware
---

### Post by ReneSDK on 2009-10-28
Hi

I've been trying to get Ubuntu 9.10 up running on my new netbook.
It's a basic netbook with a few twists (hardware-wise):

Zepto Znote V11a (Lengda M11A)
Atom N270
2GB RAM
160GB 5400rpm HDD
Intel GMA 950
1.3MB Webcam
11.1" LED screen @ 1366x768

It features a Synaptics touchpad which can be turned on and off in Windows XP via Fn+ESC. Unfortunately it seems like the touchpad is not detected at all in Ubutnu 9.10. I've tried every single thing regarding trying to get it to work.

What do you guys need from me to try and help me getting the touchpad to work?

---

### Post by ReneSDK on 2010-02-11
I finally found the answer myself.

To get the touchpad working during install do the following:

On BIOS screen press F10
Choose the DVD drive in the list
When the Ubuntu install menu press F6 and add this after the long boot string: "i8042.nomux=1"
Then choose to install Ubuntu 9.10 like you normally do.

The touchpad should now be operational during the install.



To get it working after the complete install, and also when updating the kernel, without having to edit any files do the following: 

Edit the grub files:

```
sudo gedit /etc/default/grub
```

Change this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux=1"
```

then run an update of grub and grub2:

```
sudo update-grub
sudo update-grub2
```

Reboot the netbook and you should be up running.

---

