---
title: "Asus n53sv touchpad buttons not working"
date: 2014-01-01
forum: Hardware
---

### Post by gsoundsgood2 on 2014-01-01
On latest ubuntu 13.10, touchpad buttons of my Asus n53sv do not work. the touchspad works fine, tapping is ok, but left and right buttons do not work. 

xinput list recogonizes it as "ETPS/2 Elantech Touchpad"

xinput -- test # records properly all movements, but does not show anything for actually clicking on the two left and right buttons of the touchpad. 

I checked out some threads, with no avail. All worked fine in previous ubuntu versions. 

I'm on a fresh install, does not work even in the live version. 

thank you for your support.

---

### Post by simone.milan@gmail.com on 2014-02-27
> **gsoundsgood2 said:**
> On latest ubuntu 13.10, touchpad buttons of my Asus n53sv do not work. the touchspad works fine, tapping is ok, but left and right buttons do not work. 

xinput list recogonizes it as "ETPS/2 Elantech Touchpad"

xinput -- test # records properly all movements, but does not show anything for actually clicking on the two left and right buttons of the touchpad. 

I checked out some threads, with no avail. All worked fine in previous ubuntu versions. 

I'm on a fresh install, does not work even in the live version. 

thank you for your support.


I have problems on n53sv touchpad too!!!

---

### Post by gsoundsgood2 on 2015-01-03
One year later, I have not found any solution, yet. I filed a bug on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1407313](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1407313)

---

### Post by Pilot6 on 2015-01-03
Elantech touchpads are now supported. If you install Ubuntu 14.10 or 14.04 with 3.16 kernel, touchpad should work.

---

