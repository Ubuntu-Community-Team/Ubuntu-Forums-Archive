---
title: "Got 2 graphic cards, advice with one to use"
date: 2011-06-13
forum: Hardware
---

### Post by kompotas on 2011-06-13
Hey guys, 
   I am trying to make my old pc run on ubuntu as best as it can. The thing is it has trouble even playing youtube 480 resolution videos. And if I remember it right, there wasn't a problem with this machine when it was runing it on winxp(with I hated..). Another thing is When I am trying to draw with GIMP the painted line is a lot of times slower than the cursor it self. Seems to me it might be graphic card problem. maybe drivers...
I've got two Ati cards and I am not sure witch one should I use on a machine with ubuntu OS. The first one is MSI ATI RX1600-T2D512E : [http://lt.msi.com/product/vga/RX1600-T2D512E.html#/?div=Overview](http://lt.msi.com/product/vga/RX1600-T2D512E.html#/?div=Overview) 
The other one is built by asus model EAX1300PRO SILENT/TD/256M : [http://www.asus.com/Graphics_Cards/AMD_Series/EAX1300PRO_SILENTTD256M/#specifications](http://www.asus.com/Graphics_Cards/AMD_Series/EAX1300PRO_SILENTTD256M/#specifications) .
   I feel like MSI should be better cause its bigger in RAM  512 than ASUS. But I could be wrong. Even the ubuntu wiki page with supported video cards by ATI doesn't even list the x1600 series, only the X1300 : [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
 So should I use the ASUS 256MB card?
   Doesn't matter which card I put in my pc There are no drivers listed in addition drivers. So I guess it is running on the open source ones. Should I be using the ones provided by ati : AMD Catalyst™ Display Driver 9.3 : [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English) (both cards are listed here x1300 and X1600).

Thank you for any kind of help. And excuse my english mistakes or even maybe this question if it makes no sense.

---

### Post by jake.anq on 2011-06-13
Hi

It sounds more like this being a general slowness problem.  I have had this happen with another older computer as well.  I would suggest using a 'lighter-weight' Linux flavour such as Xubuntu - [http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by Yellow Pasque on 2011-06-13
The X1600 will be a bit faster in 3D, but the X1300 is silent if that matters to you.
> Should I be using the ones provided by ati : AMD Catalyst&#8482; Display Driver 9.3 : [http://support.amd.com/us/gpudownloa...2&lang=English](http://support.amd.com/us/gpudownloa...2&lang=English) (both cards are listed here x1300 and X1600).
No. Catalyst 9-3 won't work on modern distros.

> The thing is it has trouble even playing youtube 480 resolution videos.
[http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)

Also, post contents of /var/log/Xorg.0.log

---

### Post by cascade9 on 2011-06-13
Not a huge amount in it, but the x1600 is slightly faster than the x1300. I'd probably run the x1300 though, fan noise isnt something I like.

---

### Post by kompotas on 2011-06-13
Thanks Temujin, I will avoid catalyst then. I guess the only option is open source drivers, which I am probably using. 
I installed flash aid, and updated everything. No noticeable difference. I guess flash is not the problem...
And finaly :
> **Temüjin said:**
> 

Also, post contents of /var/log/Xorg.0.log

[http://sharetext.org/AKR7](http://sharetext.org/AKR7)

---

### Post by Yellow Pasque on 2011-06-13
The log looks okay. The only other thing I can suggest is trying to turn off KMS: 
```
echo "options radeon modeset=0" | sudo tee /etc/modprobe.d/radeon-kms.conf
```
Reboot. If that doesn't help, change it back:
```
echo "options radeon modeset=1" | sudo tee /etc/modprobe.d/radeon-kms.conf
```

I guess you could also try updated video drivers: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by kompotas on 2011-06-14
Hm, I wonder could it be ram ? too slow, or not enough, or something, that makes my pc lag for example when painting in gimp resolution 1500x1000 and makeing fast strokes with my tablet ? especialy if I am using a more complex brush.
Is there any application that could run and test my ram?

---

