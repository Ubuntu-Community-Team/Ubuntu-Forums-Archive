---
title: "Trying to find packages for ffmpeg install."
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by shmoobot on 2009-11-09
Hi,

I've found the tutorials on these forums for installing ffmpeg on Hardy, but my setup seems to be having trouble finding the expected packages. I'm running Hardy: Ubuntu 8.04.3 LTS.

 ~/ffmpeg: sudo apt-get install liblame-dev
[sudo] password for jimt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package liblame-dev
 ~/ffmpeg:

The same thing applies to x264 and others. I assume I'm just missing the right source in my sources.list... but which one(s)?

Thanks.

---

### Post by FakeOutdoorsman on 2009-11-10
That's strange.  Show the output of:
```
less /etc/apt/sources.list
```
and
```
ls /etc/apt/sources.list.d/
```
Are you refering to the Hardy guide for [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showpost.php?p=6963607&postcount=360)?

---

### Post by jerrrys on 2009-11-10
ffmpeg is located in synaptic package manager.  why not download from there and let it fill the dependencies?

---

