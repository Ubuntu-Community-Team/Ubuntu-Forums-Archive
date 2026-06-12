---
title: "no write access on my ebook reader"
date: 2020-03-24
forum: Hardware
---

### Post by pickelhaupt on 2020-03-24
Hi,
I have an ebook reader (Tolino Vision 3 HD [https://mytolino.com/service/tolino-vision-3-hd/](https://mytolino.com/service/tolino-vision-3-hd/)) and I use my computer to buy and download my books and I transfer and arrange the folders on the ebook reader from the computer with a USB cable. It appears as a USB memory when plugged in.

I run a dual boot Ubuntu18.04LTS/Win10 system and I can't get write access on the Tolino whilst running Ubuntu. I can read the content but I don't have write access. On the Win10 I can read/write, add/delete/move folders, etc. 

Ubuntu is where I spend most of my time so what can I do to get the Tolino and Ubuntu to communicate properly?

cheers,
/K

---

### Post by pickelhaupt on 2020-03-24
I found the solution here: [https://askubuntu.com/questions/1004827/how-to-fix-read-only-usb-drive](https://askubuntu.com/questions/1004827/how-to-fix-read-only-usb-drive) 
The last entry pointed me to the DISKS utility. I ran the [COLOR=#242729][FONT=Arial]"Repair Filesystem" and after unmount and mount the ebook reader was possible to write to again in ubuntu.  [/FONT][/COLOR]

---

