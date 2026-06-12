---
title: "Downgrade kernel."
date: 2008-09-07
forum: General Help
---

### Post by Peque on 2008-09-07
Hey Guys. 
Since I have upgraded to 8.10-alpha5 - i'd allso get kernel-2.6.27-2 which I woon't use - caurse it seems impossible to have VMware running on that. 

How can I downgrade to another kernel and remove the old(the new one) - so I'm able to use VMware again??

---

### Post by Washer on 2008-09-07
well the only choices are to get it from the repos or compile it from source.

---

### Post by zvacet on 2008-09-07
You probably still have Hardy kernel,because you just did upgrade to new version.If you can not select kernel when comp boot then press Esc button and you will see all kernels.Choose one you want(on you know that VMware is working on).

---

### Post by drs305 on 2008-09-07
You can install StartUp-Manager, a gui app to edit your menu list. Assuming the old kernel is still on your machine, you can make it the default startup kernel. SUM has a lot of other good tweaks as well, such as menu display time,number of kernels to view, etc. You can do all this by editing menu.lst as well but SUM is a less error-prone way of editing it.

To install:
```
sudo apt-get startupmanager
```
To run:
System, Administration, StartUp-Manager or:
```
gksu startupmanager
```

See the link in my signature line for a tutorial on StartUp-Manager.

---

### Post by Peque on 2008-09-08
Great thanks guys.

---

