---
title: "Urgent help needed"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by dinkyverma279 on 2009-06-18
Hi experts,
 
I am using ubuntu linux. While cleaning, I deleted under /lib/modules.  So is there any way to recover the modules or i need to go for reinstallation?
 
Regards,
dinky

---

### Post by K.Y.A on 2009-06-18
I don't think you can recover the modules. You might be able to mount the filesystem located on the livecd, and copy the /lib/modules in that virtual filesystem to yours. But that might be a little hard for a beginner, no offense. :)


EDIT: I would backup your data and reinstall.

---

### Post by credobyte on 2009-06-18
It might be possible, but, not the best choice for a beginner. Even if you will be able to restore some part of this folder, it may not function correctly.
Backup all your sensitive data and do reinstall it !

---

### Post by dinkyverma279 on 2009-06-18
Hi,
 
I have kernel source code in /usr/src. So i will try to build it and then install the modules again.
 
regards,
dinky

---

### Post by K.Y.A on 2009-06-18
> **dinkyverma279 said:**
> Hi,
 
I have kernel source code in /usr/src. So i will try to build it and then install the modules again.
 
regards,
dinky

Good luck

---

### Post by iponeverything on 2009-06-18
Just reinstall the kernel package from /var/cache/apt/archives

---

### Post by K.Y.A on 2009-06-18
> **iponeverything said:**
> Just reinstall the kernel package from /var/cache/apt/archives

Good idea. . .

---

### Post by presence1960 on 2009-06-18
what were you cleaning? Ubuntu isn't like windows.

---

