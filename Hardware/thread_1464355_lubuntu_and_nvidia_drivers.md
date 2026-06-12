---
title: "lubuntu and nvidia drivers"
date: 2010-04-28
forum: Hardware
---

### Post by mark9950 on 2010-04-28
I put lubuntu on a newer machine with nvidia drivers and the default drivers aren't 3d and the hardware drivers tells me there are no proprietary driver on my system,so how do I install the nvidia drivers on my system?The default drivers are no good.

---

### Post by ibuclaw on 2010-04-28
As much as I love Nouveau (and use it on all my systems now), I suppose there may be one or two cases where you will need Nvidia instead.

Check to make sure that the nvidia-common package is installed, that should pull in all dependencies for hardware detection in the restricted drivers program.

Regards

---

### Post by mark9950 on 2010-04-28
Yes full screen on HD youtube videos and HD movies,the nouveau drivers suck.The games too.

In the synaptic repository there are the 185 nvidia drivers,should I uninstall the nouveau drivers and install all the nvidia drivers and everything with the 185s?Or how would I do it because the hardware detectors dont work like on ubuntu.

I like this distro alot.

---

### Post by ibuclaw on 2010-04-29
> **mark9950 said:**
> Yes full screen on HD youtube videos and HD movies,the nouveau drivers suck.The games too.

In the synaptic repository there are the 185 nvidia drivers,should I uninstall the nouveau drivers and install all the nvidia drivers and everything with the 185s?Or how would I do it because the hardware detectors dont work like on ubuntu.

I like this distro alot.

Installing nvidia-common should install all dependencies for hardware drivers to perform the hardware detection correctly.

And the nouveau drivers don't suck at all thanks. (3D works exactly as I require on all my machines) :)

---

### Post by Muley63 on 2010-05-08
Thank You, ibuclaw. I tried switching to the binaries in synaptic because they were not showing up in the restricted hardware program and that caused my comp to blow up. I saw your post and then purged the nvidia drivers and then reinstalled nvidia-common there it was.

---

