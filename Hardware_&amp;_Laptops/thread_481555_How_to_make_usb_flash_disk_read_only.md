---
title: "How to make usb flash disk read only"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by CortexM3 on 2007-06-22
I have ubuntu Feisty fawn and I want to make the usb flash disk READ ONLY! the use can read from it but will not copy files to it!

Thanks in advance

---

### Post by pickarooney on 2007-06-22
Heh, maybe you should swap your disk with the guy two threads up who can't make his writable :D
If it's a one-off, **chmod a-w /media/disk** or similar should do the trick. Otherwise,
you'll need to add a specific line in the **fstab** file to make it mount with no write access. Can you post up the outputs of **mount** and **cat /etc/fstab** with the disk connected?

---

