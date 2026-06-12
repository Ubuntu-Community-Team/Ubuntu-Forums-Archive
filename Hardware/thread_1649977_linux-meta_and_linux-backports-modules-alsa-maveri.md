---
title: "linux-meta and linux-backports-modules-alsa-maverick-generic question"
date: 2010-12-20
forum: Hardware
---

### Post by xandey on 2010-12-20
I am trying to get my microphone working with Maverick.

I've found on some other forums that I need to upgrade my alsa version to 1.0.23 or so. 

I have the same audio chip as these guys, and it seems like the problem is the same (no microphone found)
[http://wiki.ubuntuforums.org/showthread.php?p=9811380](http://wiki.ubuntuforums.org/showthread.php?p=9811380)

They suggest that I instal 
linux-backports-modules-alsa-lucid-generic 

( figured that this was worth a shot, and since no maverick version was available in synapitic, I tried it... but then my machine wouldn't boot.

So, my question: how do I get linux-backports-modules-alsa-maverick-generic ? I can find it referenced places:

[https://launchpad.net/ubuntu/maverick/+source/linux-meta](https://launchpad.net/ubuntu/maverick/+source/linux-meta)

Thanks
Sandy

---

### Post by IcarusR on 2010-12-21
[https://launchpad.net/ubuntu/maverick/i386/linux-backports-modules-alsa-maverick-generic/2.6.35.23.25]("https://launchpad.net/ubuntu/maverick/i386/linux-backports-modules-alsa-maverick-generic/2.6.35.23.25")

---

### Post by xandey on 2010-12-21
So I found this page. But I couldn't find it through apt-get or synaptic. My question was how do I get the repo that it is in? or is it waiting to be reviewed to be included?

Is there a way to have it update when ubuntu updates the kernel?

Sandy

---

### Post by xandey on 2010-12-21
Oh wait, nevermind. It seems i've screwed up some stuff... This machine has Lucid on it, and that's why the maverick package isn't showing up.

Thanks for your help.

---

### Post by IcarusR on 2010-12-21
Please mark the thread as 'solved' if it is.

---

