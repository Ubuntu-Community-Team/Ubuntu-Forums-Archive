---
title: "How to install &quot;vmware&quot; on 9.4 Jaunty?"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by Ironhide on 2009-05-05
[SIZE="2"]Hello people,

Im still premature at Linux so a little help with "VMWARE" please.

So far I've install 8.10 Intrepid and just upgraded to 9.4 Jaunty and all I can say is... "This is awesome \\:D/ " But the thing is that I need to have a virtual system to install Windows just because of my ZUNE MP3 player and maybe other softwares that are not compatible with Linux. I would prefered not to work with Windows any more but I need my music :guitar: Yeah! I've heard of "wine" but I've also heard that is not 100% successful  with all Windows softwares so they told me that "vmware" is the way to make it happen. So if anybody can explain step by step on how to get "vmware" and how to install it I will appreciated so much.

Thanks!!! ;)[/SIZE]

---

### Post by veloce on 2009-05-05
Have a look on the Virtualisation forum here:

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

In particular the two sticky threads.

---

### Post by drublik on 2009-05-06
First of all, if you only want it for your Zune software, I would try Wine. Moreover, I haven't tried Zune but it's possible that you can use it with the media players that came with Ubuntu.

However, if you want to install vmware, you can do it in 2 ways:

- Install via apt-get (or synaptic). I don't remember the name of the package.

- Download vmware player from vmware website. It's easy to install, once downloaded, unzip it to some folder and execute the .sh installer. Follow the screen instructions and that's all.

But remeber, to use Windows on vmware, you need a windows license to be able to install it on vmware.

---

### Post by veloce on 2009-05-06
> **drublik said:**
> 
- Install via apt-get (or synaptic). I don't remember the name of the package.


I'm pretty sure that vmware isn't in the jaunty repositories yet.  

If you are creating a new windows vm then you'll need vmware-server rather than player.

---

### Post by dopplerdeffect on 2009-05-06
The Zune Software will not work in wine as it relies heavily on the .NET framework. Although there is an open source version of the .NET framework for Linux, called Mono, it is not enough for the Zune Software to work. From what I understand, even Virtualized support is limited. If I remember correctly, the only way to get the virtualized Zune Software (Running on a Virtual Machine in either VMware or VirtualBox) to recognize the Zune hardware is to dissable the USB 2.0 support. This means that file transfers will go extremely slow. I wish there was an alternative. The Zune Software is currently the only reason I still have a Windows partition.

---

