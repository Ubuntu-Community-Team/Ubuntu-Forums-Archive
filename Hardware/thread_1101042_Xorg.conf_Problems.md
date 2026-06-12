---
title: "Xorg.conf Problems"
date: 2009-03-19
forum: Hardware
---

### Post by JermusDoggus on 2009-03-19
I am having the hardest time getting this file set up correctly. First, I couldn't get my native resolution for one reason or another. I reinstalled Ubuntu and I was finally able to get the native resolution for my monitor. But since I have two, I wanted to get dual support. Once (I thought) I activated TwinView, I'm back to "Low Graphics Mode".

I've been working on this for about a week now and I've run ```
sudo dpkg-reconfigure xserver-xorg
``` about a million times now. I does nothing except reset the Xorg.conf to a useless state.

Is there a way to automatically detect settings (monitors, drivers, screens, etc) like at installation without actually re-installing Ubuntu... again?

Thanks.

---

### Post by nbo10 on 2009-03-19
Twinview is only avaible if you have nvidia graphics card.

---

### Post by JermusDoggus on 2009-03-19
Sorry, I should have mentioned I have an nVidia 630i/GeForce 7150 motherboard with integrated graphics. And, yes, I've downloaded and activated the drivers.

---

