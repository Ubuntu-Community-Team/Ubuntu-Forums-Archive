---
title: "Amd ati radeon hd 2400 pro problem"
date: 2015-11-13
forum: Hardware
---

### Post by antolbestg4 on 2015-11-13
So about a week ago i installed ubuntu on my pc but i realized that the drivers were not working. I searched all over the internet and i found that i had to install the amd legacy drivers . I installed them but nothing changed ... I tried also the repository of makson96 but it didn't work either.
Can you help me ? I am stuck with the resolution of 1280x768 and I cannot change to 1366x768. Do you have any alternative ? 8-[:sad::?

---

### Post by QIII on 2015-11-13
Please edit your post and remove the all-caps or I will remove it from public view and allow you to post again.  That is considered to be shouting and is rude on a web forum.

There is no proprietary AMD driver for your GPU.  AMD dropped Linux support for it years ago and there is no way to use an AMD driver with any release of Ubuntu after 12.04.1.  You will need to uninstall any proprietary driver you attempted to install and use the default open source driver installed with Ubuntu.

I have no experience with the makson PPA other than recommending very strongly against its use several years ago.  So I can't help you with regard to how to uninstall anything from it.

---

### Post by antolbestg4 on 2015-11-14
I removed the all caps. Nice pic by the way.

---

### Post by Yellow Pasque on 2015-11-14
> but i realized that the drivers were not working
How did you come to this conclusion? Post or pastebin your /var/log/Xorg.0.log

>  I am stuck with the resolution of 1280x768 and I cannot change to 1366x768
Was that before or after you tried the PPA?

---

