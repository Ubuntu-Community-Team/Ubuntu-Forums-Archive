---
title: "VNC Problem"
date: 2009-07-23
forum: Hardware
---

### Post by low_mat on 2009-07-23
The problem is with my graphics card and I can't figure it out. I have a Gforce GTX 285 SC edition ([http://www.newegg.com/Product/Product.aspx?Item=N82E16814130446](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130446)). When I disable the drivers for the card itdoesn't happen. So I'm fairly certain it's in the configuration of the device drivers. I installed the ones recommended by Ubuntu.

[IMG]http://img364.imageshack.us/img364/8937/screenshothardwaredrive.png[/IMG]

So here's the issue: when I VNC, over the internet or on my local network, the vnc viewer shows the desktop but when I click around nothing happens on the vnc viewer side, but the clicks are going through because using a Laptop I can watch them go through on my desktop, which I'm connecting to. I've also tried tightVNC and even connecting from another Ubuntu machine. Same thing happens.

I'm running Ubuntu 9.04, 64-bit on Wubi. But it also happens on a stand alone drive with 8.10 32 or 64 so it doesn't matter. Like I said if I remove the drivers There's no problem at all.

I've messed around with the Nvida control panel using (nvidia-settings) with no luck. Any help would be great.

---

### Post by low_mat on 2009-07-24
I wanted to test my Iphone camera so here's a quick video of the problem.

[http://www.youtube.com/watch?v=RtPEeb2n5p0](http://www.youtube.com/watch?v=RtPEeb2n5p0)

I also tried a different Nvida card. Not sure what kind but it gave me more options for drivers. I tried all three and none of them worked. (Check below)

[IMG]http://img193.imageshack.us/img193/9043/screenshothardwaredrivev.png[/IMG]

---

### Post by cariboo on 2009-07-24
I don't think your problem is related to your graphics drivers. If you connect with sftp can you manipulate files?

---

### Post by low_mat on 2009-07-24
> **cariboo907 said:**
> I don't think your problem is related to your graphics drivers. If you connect with sftp can you manipulate files?


SFTP works great. If it's not the card how come when I remove the device drivers , VNC works without a problem? Any suggestions would help a lot.

---

### Post by cariboo on 2009-07-24
So are you saying that when you use the open source nv or vesa drivers vnc works?

---

### Post by low_mat on 2009-07-24
> **cariboo907 said:**
> So are you saying that when you use the open source nv or vesa drivers vnc works?

I'm going to say yes. Basically whatever drivers ubuntu is using right after it installs. I guess the generic video drivers is the correct term. That's when VNC works. I can't change my resolution though. Once I install the accelerated drivers, the problem with VNC starts to happen but I now can change my resolution and use desktop effects.

---

