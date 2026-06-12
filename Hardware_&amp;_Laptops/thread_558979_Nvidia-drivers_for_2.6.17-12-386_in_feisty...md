---
title: "Nvidia-drivers for 2.6.17-12-386 in feisty.."
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by OskarB on 2007-09-24
Hi, I have a really large problem with my computer right now... I've upgraded to feisty fawn and tried to update my nvidia drivers but it just wont work.. It worked fine removing the old ones... but installing the new ones is a whole other matter...

I think that the problem is that the 2.6.17-12-386-packages is not supported in Feisty.. at least it says that the package is to old etc. when I try to download linux-headers-2.6.17-12-386...

I've figured that I should add something in the sources.list to enable all the edgy-packages... but what?

please help!

//Oskar

---

### Post by reckless2k2 on 2007-09-24
you've got to remove all the nvidia stuff first, reboot, then reinstall. you should be getting everything from generic...not i386. i had this issue recently. you have to get rid of nvidia-common i believe and it removes restricted drivers and such. then when you go back in and do the nvidia pull from synaptic, it'll grab the correct restricted package and common...etc...etc..

understand?

---

