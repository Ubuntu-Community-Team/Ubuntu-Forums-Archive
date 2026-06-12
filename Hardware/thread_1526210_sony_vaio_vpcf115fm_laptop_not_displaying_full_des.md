---
title: "sony vaio vpcf115fm laptop not displaying full desktop"
date: 2010-07-07
forum: Hardware
---

### Post by tthurston on 2010-07-07
I can't seem to get the whole desktop to display. I have the nvidia geforce gt 330m graphics card. Ubuntu recognized it and installed the necessary drivers. I tried to change the resolution but that didn't change anything. The top right corner of the desktop is not visible. M y lcd screen on my Sony VAIO laptop is 16 in. Any help would be appreciated.

---

### Post by lidex on 2010-07-09
Which driver are you using? Have you tried 'System>Administration>Nvidia XServer Settings'?

---

### Post by roskiy on 2010-11-12
Same laptop Sony Vaio VPCF115FM
resolution set by default without installing additional drivers from nVidia is 2048×1536 when screen is capable of 1920x1080 so the right and bottom part of the desktop is not showing
When i try to set resolution to 1920x1080, pixels size is wrong, pixels are double of normal size. in any event default driver does detect additional monitors and to my surprise additional monitors even when mirrored get correct screen resolution and look excellent. that's all about default drivers.

Now i tried to install, proprietary drivers "System &#8594; Administration &#8594; Hardware drivers"
After installing nVidia drivers screens go blank (black actually) additional monitors are not detected and display nothing. Only option was to boot in safe mode and fix xorg.conf file
I have goggled some suggested solutions none of which helped. 
Can someone be so kind and point me right direction solving this problem? 
Also: where can i read something about how pixel size and resolutions are formed?

---

### Post by kevin2849 on 2010-11-12
I went to [http://code.google.com/p/vaio-f11-linux/](http://code.google.com/p/vaio-f11-linux/) and followed the directions for installing NVIDIA driver from source. It is an involved process but if you read the directions and follow the steps you should be ok.

---

