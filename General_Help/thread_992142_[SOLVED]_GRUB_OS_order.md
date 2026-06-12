---
title: "[SOLVED] GRUB OS order"
date: 2008-11-24
forum: General Help
---

### Post by 4uvak91 on 2008-11-24
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ecb341b1-e3bc-4b90-bf69-472d8aeda3dc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ecb341b1-e3bc-4b90-bf69-472d8aeda3dc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ecb341b1-e3bc-4b90-bf69-472d8aeda3dc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ecb341b1-e3bc-4b90-bf69-472d8aeda3dc ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ecb341b1-e3bc-4b90-bf69-472d8aeda3dc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

How can i change os order in GRUB?? I wanna that my vista is first in the list...

---

### Post by philinux on 2008-11-24
Install startupmanager and tell it the default is vista.

either from synaptic
sudo apt-get install startupmanager
or firefox address bar
apt://startupmanager

The menu item appears in system>admin

---

### Post by 4uvak91 on 2008-11-24
ok..i try. Do you know what drivers/things i need to install for my graphic card?? i have ati radeon hd 4850

---

### Post by philinux on 2008-11-24
Whats offered in System>admin>hardware Drivers?

---

### Post by 4uvak91 on 2008-11-24
i tried last...then my resolution ****** up after rebooting...wrong hz..

---

### Post by 4uvak91 on 2008-11-24
so how can i fix it if that happend??

---

### Post by philinux on 2008-11-24
I would personally uninstall the driver that you're using and get the linux ati driver direct from ATI. Unless thats what you've already installed.

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

You'll have to read the wiki to install it. [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

---

### Post by 4uvak91 on 2008-11-24
yup that i'm talking about....

---

### Post by 4uvak91 on 2008-11-24
Tyvm!:)

---

### Post by 4uvak91 on 2008-11-24
"dude it fialed....i downloaded the driver and after rebotiing  --> black screen 74,9/60hz...max. is 60hz So how can I fix this???"

HELP??

---

### Post by philinux on 2008-11-24
Start a new thread in Absolute Beginners Talk forum.
Title
Black screen:  ati radeon hd 4850. need help with driver.


You'll get more replies in there. Since my card is nvidia I cant give anymore help.
Seems ati can be a pain though.

---

