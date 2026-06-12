---
title: "Sound output from laptop speaker and jack port"
date: 2010-05-21
forum: Hardware
---

### Post by Link_Octree on 2010-05-21
Hello there,
I bought a new core i3 Laptop (Asus X52F) a few month ago
I installed Lucid 64bits on it, and I only noticed one problem still not solved...

Sometimes I want to use my headphones, or my external speakers, but when I plug them in the jack port, the sound still come from headphones/external speakers AND laptop speaker...

I looked into gnome-alsamixer and didn't see anything who can fix that.
Screenshot: [http://en.zimagez.com/zimage/son29.php](http://en.zimagez.com/zimage/son29.php)

Thank you ;)

---

### Post by Link_Octree on 2010-05-22
Nobody knows ?

---

### Post by pigphish on 2010-05-22
I have the same problem. 

The best bet I have found so far is following the following: 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

This shows how to get the right sound card setup. I believe I have to find the right model for my laptop (panasonic toughbook) as you probably do to.

---

### Post by lidex on 2010-05-23
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Link_Octree on 2010-05-23
@pigphish: I looked your link, but I saw nothing that may apply to me...

@lidex: sure:

uname -a
```
Linux laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.21
```

head -n1 /proc/asound/card*/codec#*
```
==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 5069

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX
```

Now about my laptop: it's an Asus X52F-SX053V
Hardware:
[IMG]http://ipicture.ru/upload/100523/yg5Am2gjMT.jpg[/IMG]

Thanks for your support ;)

---

### Post by lidex on 2010-05-23
Best results with that codec are with the newest alsa version.
Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Next follow the alsa-upgrade link in my sig to get v 1.0.23

---

### Post by marin123 on 2010-05-24
did anyone try alsa upgrade? i have the same problem and it would be great if i could solve it...

thanks!

EDIT: i upgraded alsa and now works perfect :)

---

### Post by jsevi83 on 2010-06-01
Link_Octree, did you solve the problem? I have an Asus A52F and found a solution (maybe not the most ideal one, but better than nothing). You can find it here   [http://ubuntuforums.org/showthread.php?t=1460790](http://ubuntuforums.org/showthread.php?t=1460790)

marin123, is your laptop an Asus X52F too? I am using Alsa 1.0.23 and Kernel 2.6.34, both from ppa:ricotz/unstable. That didn't solve the problem, and also the external microphone is not working. Any advice?

---

### Post by marin123 on 2010-06-02
> **jsevi83 said:**
> Link_Octree, did you solve the problem? I have an Asus A52F and found a solution (maybe not the most ideal one, but better than nothing). You can find it here   [http://ubuntuforums.org/showthread.php?t=1460790](http://ubuntuforums.org/showthread.php?t=1460790)

marin123, is your laptop an Asus X52F too? I am using Alsa 1.0.23 and Kernel 2.6.34, both from ppa:ricotz/unstable. That didn't solve the problem, and also the external microphone is not working. Any advice?

no, i have acer 5942g with kernel 2.6.32-22-generic with alsa 1.0.23.
maybe your problem is in the kernel (unstable)... i ran alsa upgrade script and my sound works perfect...
i read here that people have problems with audio through hdmi cable, but on my laptop  (ati radeon hd 5650 1 gb) everything works perfect :)  lucky me :D

---

