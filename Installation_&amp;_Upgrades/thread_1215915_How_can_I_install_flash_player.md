---
title: "How can I install flash player"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by os56k on 2009-07-17
I downloaded flash player from adobe website but when it was going to be installed the program the program GDebi Package Installer gave me error.

The error was that this program is for x86 system not for 64 bit system .

How can I install flash player ?

I have ubuntu 9.04 64 bit.

---

### Post by oldos2er on 2009-07-17
In a terminal, run
```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

---

### Post by os56k on 2009-07-24
Thank you a lot your guide. Now my Firefox has flash player and I can see all flash-made web sites.:)

But I wonder why its size was so much( 28MB ) and after download it took a lot of time to install.:(

What about downloading from adobe website ( its size is 3.8 MB ).Adobe offers a special .deb file for Ubuntu in [http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP) that you can selecct in the drop down list.

If I can install from this file, tell me how I can because it has less size and easy to download.:confused:

---

### Post by presence1960 on 2009-07-24
a simple solution for 64 bit flash. has worked flawlessly for me in Hardy, Intrepid & Jaunty. This is from our x86 64-bit users section of the forum: [64 bit flash]("http://ubuntuforums.org/showthread.php?t=772490")

---

