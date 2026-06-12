---
title: "NDiswrapper problem with Internal Wireless"
date: 2005-03-16
forum: Hardware &amp; Laptops
---

### Post by Houmie on 2005-03-16
Hello,

I have a Dell Inspirion 8600 with a Intel Pro 2100 Internal wireless card.

Since I use WAP encryption the built in drivers from Ubuntu 5.02 couldn't help me out.

'root@ubuntu:/media/usbdisk/drivers # sudo ndiswrapper -i w70n501.inf
Installing w70n501

so far it seems it is working, but then...

root@ubuntu:/media/usbdisk/drivers # sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-4-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Operation not permitted? Why?

Any comments?
Thanks
Houmie

---

### Post by Houmie on 2005-03-17
wow no one can help me with that?  :?

---

### Post by songochain on 2005-03-17
[QUOTE=Houmie]wow no one can help me with that?  :?[/QUOTE]
 Try sudo ndiswrapper -l to see if your card is installed. Example: xxx software installed, hardware present
What version of ubuntu have u?
If u're root why do u use sudo???

---

### Post by ktraglin on 2005-03-29
I had a simlar problem with Mepis 3.3.  I compiled it from the source code obtained from the debian repositories.  The solution that worked for me was to remove ndiswrapper-source and ndiswrapper-utils, then install them both from the testing branch, instead of unstable.

Example:
apt-get remove ndiswrapper-source ndiswrapper-utils
apt-get -t testing install ndiswrapper-source ndiswrapper-utils

Now it works just fine.

---

