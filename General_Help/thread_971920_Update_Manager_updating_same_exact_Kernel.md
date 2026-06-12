---
title: "Update Manager updating same exact Kernel?"
date: 2008-11-05
forum: General Help
---

### Post by VMC on 2008-11-05
I noticed I had updates tagged. When I saw they were the same as I already had, I did a CRC and listing of '/boot' folder. Also 'uname -a'.

After updates it was revealed that there were no change whatsoever. This is happened in the past. Why?

---

### Post by drs305 on 2008-11-05
Today when I updated one of my machines I saw the kernel was among the updates. Although the listing was the same, **linux-image-2.6.24-21**, when I looked at the details they were different. I can't access it at the moment, but it the update was something similar to 2.6.24-21.6 to 2.6.24-21.15 when I viewed the details.

The 'uname -a' command would show no change, staying at 2.6.24-21, even though it was now at .15 or whatever.

---

### Post by VMC on 2008-11-05
Thanks you. That helps!  Details of what, or where?

---

### Post by drs305 on 2008-11-05
> **VMC said:**
> Thanks you. That helps!  Details of what, or where?

There are a couple of ways. If you know there is a kernel update, you could look in synaptic and compare the 'installed version' column to the 'latest version' column. If they differ and you have updates enabled, there is a good chance that is the update being made.

If you use update manager, as you probably saw, it only says the update is, for example, 2.6.24-21. When I begin the update/download, there is an option to 'Show the individual files'. As the linux-image is being downloaded, it shows the entire filename, including the additional version information. I am updating Intrepid at the moment and it shows that 2.6.27-7 is being updated from -14 to -15.

And finally, to beat a dead (or dying) horse, you can see if the kernel (or any other app) has had a recent update by running:
```
aptitude changelog *appname*
```
Example: aptitude changelog linux-image-2.6.27-7

This will show the changes made to the package, although these changes *may or may not be installed on your machine*. One of the pieces of information is the date of the change.

---

