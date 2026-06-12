---
title: "Installation driver ati catalyst 9.4"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by fsancho05 on 2009-05-01
[SIZE=2]Hey guys, I'm trying to install the ati catalyst 9.4 for my Hd 4870, but I don't know where to find the some packages like xorg-driver-fglrx_8.593-0ubuntu1_i386.deb, fglrx-kernel-source_8.593-0ubuntu1_i386.deb, fglrx-amdcccle_8.593-0ubuntu1_i386.deb, fglrx-modaliases_8.593-0ubuntu1_i386.deb. 
Can someone help me to find this packages?
 
Thanks!
[/SIZE]

---

### Post by jbrown96 on 2009-05-02
Why are you looking for those packages? That driver is available from System--->Admin--->hardware drivers. You don't need to do anything manually.

---

### Post by fsancho05 on 2009-05-02
Hi, because the driver isnt't available on "hardware drivers".
It shows the follow message: "no drives in use in the system owners"

You can help me?

P.S.: Pardon my english!

---

### Post by jbrown96 on 2009-05-02
Go to [this website]("http://support.amd.com/us/gpudownload/Pages/index.aspx") and download the appropriate driver. Open a terminal (Apps--->Accessories--->Terminal) and run the file. It's either ```
sudo sh ./Desktop/ati
``` or ```
sudo ./Desktop/ati
``` This assumes you downloaded it to your desktop. Once you type the ati part you should be able to hit tab a couple of times and it should complete the rest of the file name. Just follow the dialgog; it's really simple. Reboot and enjoy.

You shouldn't need to get all those .debs.

---

