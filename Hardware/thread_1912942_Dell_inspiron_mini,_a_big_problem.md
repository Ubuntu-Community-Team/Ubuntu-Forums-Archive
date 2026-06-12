---
title: "Dell inspiron mini, a big problem"
date: 2012-01-21
forum: Hardware
---

### Post by ronpetit on 2012-01-21
Hello mates, this is my first post so i will try to be direct.... i got a problem with my dell inspiron mini, i got ubuntu 11.04, so, look, i got a desktop computer with the same memory and space that this mini laptop, but in my desktop pc i can see youtube videos really nice, but in my laptop not, PD: it is not a internet problem, i downloaded a video to my laptop and that video goes bad too, i search on google and someguys said that is a video card problem, so look my system summary, what drivers i need to download for my graphics card??

_[[IMG]http://img513.imageshack.us/img513/5305/pantallazosummarysystem.png[/IMG]]("http://imageshack.us/photo/my-images/513/pantallazosummarysystem.png/")_

---

### Post by snowpine on 2012-01-21
Unfortunately your netbook has Intel GMA500 Poulsbo graphics that are not well supported in Linux.

Here some reading material on the topic, good luck! :)

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

---

### Post by ahallubuntu on 2012-01-21
Yes, GMA500 (Poulsbo).  I have Ubuntu 11.04 on an Acer netbook with the same chipset and CPU.  It is possible to get Ubuntu working pretty well though fairly easily.  Video playback (Youtube, etc.) works fine.

I'm using the EMGD drivers.

My biggest problem is that suspend freezes it about 1 in 10 times and I must do a hard shut down.  Sometimes also when I resume my display is "scrambled" and unreadable, but if I suspend and resume again usually the display is fine again.

From the wiki linked to above, I did this in a terminal:

sudo add-apt-repository ppa:gma500/emgd-1.8
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms
sudo emgd-xorg-conf

and then rebooted.

---

### Post by ronpetit on 2012-01-21
Thanks mateees! now work so much better, thanks a lot

---

### Post by mörgæs on 2012-01-21
If it works, then please mark the thread 'solved' using 'thread tools'.

---

