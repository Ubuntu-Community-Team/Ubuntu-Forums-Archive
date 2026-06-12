---
title: "Lacie Porsche Desktop 250gb Extern Usb 2.0"
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by topic58 on 2005-11-05
Hi, I'm thinking of buying an extern harddrive with USB 2. Anyone who has the one mentioned above or similar in Ubuntu 5.10? I just want to know that it will work properly in my Ubuntu 5.10 Breezy, just plug & play with no problems. Will just use it as ackup, nothing else. Any answers in this matter is more than welcome. ::KS

---

### Post by malacandra on 2005-11-05
Hi. I bought a Seagate Externa HD, 160GB at Wal-Mart. When I plug it in, after a few seconds, Ubuntu mounts it as SEAGATE and opens a file-browser window on the external HD. It works fine. When finished, you just right click the icon and select Unmount. That's it.

I noticed, however, when using a different Window Manager (XFCE) that the drive was not automatically mounted (XFCE has no desktop icons.)

So, when you insert the external drive cable, you need to do the following:

**dmesg|tail** to see where it mounts. Give it a few seconds. It will usuall be something like **sdb or sdc** . Once you know which one, you can create a driectory like this:

**mkdir /media/seagate** Then mount the drive (as root) like this:
**mount /dev/sdb1 /media/seagate**

But all that is only if you're using a desktop with no icons. Again, Breezy with Gnome will automatically load it.

Buy one! And have fun!

---

### Post by topic58 on 2005-11-05
Hey, thanks a lot for your answer here. I have just ordered my USB-disc now. :razz:

---

