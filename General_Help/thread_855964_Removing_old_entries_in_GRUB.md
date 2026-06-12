---
title: "Removing old entries in GRUB"
date: 2008-07-11
forum: General Help
---

### Post by apche93 on 2008-07-11
Hi, is there a way to automatically display the new entries.  Like after a kernel update, is there a way that the grub menu will automatically show the newest kernel, instead of the older ones?

---

### Post by OutOfReach on 2008-07-11
The easiest way would be to use startupmanager
```
sudo apt-get install startupmanager
```
Type that into the terminal and once its done installing access it from System>Administration>StartUp-Manager
Then go to the Advanced tab, and tick the tickbox that says: Limit the number of kernels in the boot menu.
Then select the number of Kernels that you want showing. 

Cheers :popcorn:

---

### Post by iaculallad on 2008-07-11
> **apche93 said:**
> Hi, is there a way to automatically display the new entries.  Like after a kernel update, is there a way that the grub menu will automatically show the newest kernel, instead of the older ones?

You also do that using Synaptics. Navigate to System->Administration->Synaptics Package Manager, click on "Search" and input "linux-image". A list of your kernel will be displayed, right-click on the OLD kernel file and select "Mark for complete Removal". Do the same process for other old kernels installed in your system. When you're finished marking all OLD kernels for removal, click on "Apply".
Your GRUB menu list will be update automatically.

NOTE: You can also leave (1) old kernel just in case something goes wrong when using the updated kernel.

---

