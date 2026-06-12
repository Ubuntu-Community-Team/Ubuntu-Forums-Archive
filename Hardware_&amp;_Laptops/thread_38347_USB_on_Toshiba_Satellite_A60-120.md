---
title: "USB on Toshiba Satellite A60-120"
date: 2005-05-31
forum: Hardware &amp; Laptops
---

### Post by jrev on 2005-05-31
Hi all,
If I clic on the icon strore'n'go on my desktop the USB Key opens and I can read and transfer a file from this USB key
but I cannot write on it or transfer a file to the Key 
the owner of the folder is jean
the permissions are dwrx 
there is no information in fstab about this key 
if I try to clic and move a file to the key I got the message : "you have no write permission"
the file system of the key is fat32 

Where is the fault ?
Thanks

---

### Post by ::DoGG:: on 2005-05-31
Try to mount it with umask=000 option in /etc/fstab

---

### Post by jrev on 2005-06-01
thank you

 the fault is on the key which sometimes fails to give proprer access in writing 
found the solution : change the key type (it works fine on MSWIN$, as usual. :))

I cannot see the need to add a line in fstab :  the key is operative as soon as you PC is running...
plugitin or plugitout and mount/umount is done automatically without fstab 
AFAIK

---

### Post by ::DoGG:: on 2005-06-01
Well, ok...
So of you have the problem you usually stopping all the deamons that are running and try to mount it by yourself - by hand. That`s the best way to find out what are the optionf of mount which in this case MIGHT be a problem (like getting a proper umask for mounting) . I`m just trying to give You a clue whqat`s going on, i never had a problem with that kind of hardware.

---

