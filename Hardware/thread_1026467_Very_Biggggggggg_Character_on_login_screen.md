---
title: "Very Biggggggggg Character on login screen"
date: 2008-12-31
forum: Hardware
---

### Post by tigga on 2008-12-31
Ihave a bizzard problem, the characters on my login screen are big,very big like this[SIZE="7"]**A**[/SIZE] instead of [SIZE="3"]A[/SIZE].
my graphic card is Intel GMA915.
any one can help me??

---

### Post by namdung on 2008-12-31
This sounds like a bug.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/107320](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/107320)

The following seems to work for many. In xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

Add the following line in Monitor Section
```
Section "Monitor"
       ... #whatevert was in already.
        **Option "DDC" "no"**
EndSection
```

---

