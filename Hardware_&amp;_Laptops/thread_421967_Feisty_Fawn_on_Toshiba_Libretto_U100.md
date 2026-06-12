---
title: "Feisty Fawn on Toshiba Libretto U100"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by lingenfr on 2007-04-24
I tried Xubuntu 7.04 on my U100, but no joy. With a normal install, I had no mouse pointer and no taskbar. When I tried to resize my windows partition it puked. I am going to use Partition Magic to resize the partition and then try again. With a VGA install, I got a normal desktop. Has anyone gotten Feisty on a U100? Any pointers? Thanks.

---

### Post by Syke on 2007-04-24
Same problem with the taskbar and cursor here.

I'll play with it some more see if I can get it to work any better.

---

### Post by Syke on 2007-04-25
Ubuntu 7.04 with the vesa video driver works very well. Not perfect since it uses 1024x768 instead of the native 1280x768, but it's very close.

---

### Post by lingenfr on 2007-05-23
Likewise, I just went with Kubuntu which is what I normally use. I runs plenty fast, so it is not worth the hassle of getting used to XFCE.

---

### Post by Syke on 2007-05-24
I found the magic solution. Switch to the Intel video driver! Now, the resolution is correct and even 3D desktop effects work great.

---

### Post by lingenfr on 2007-05-25
I tried using dpkg-reconfigure xserver-xorg and selected the i810 driver. The config I got was completely hosed. So I edited my xorg.conf and just changed vesa to i810. X started, but I had crap at the top of the screen, the taskbar was barely visible and my mouse pointer was not visible. I was trying to use 1280x768 as I had been with vesa. As you said, when I keyboarded around, direct rendering was working and glxgears was giving me 2700+ frames. Holy crap. I would appreciate if you would post your xorg.conf or at least the relevant parts. Thanks.

---

### Post by Syke on 2007-05-27
No, not the i810 driver. "intel".

sudo apt-get install xserver-xorg-video-intel

Then switch to the "intel" driver.

---

### Post by lingenfr on 2007-05-27
That worked great. DRI is working and glxgears gives about 445fps. Your advice was most helpful, if you are willing, I started a wiki page for the U100. Please help out if you can.

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaLibrettoU100](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaLibrettoU100)

---

### Post by jsenner on 2007-06-09
I have a Libretto U100 and had been running Dapper on it with great results except for I never could get it to work right with Verizon's V620 Aircard in EV-DO. It would work perfectly with 1x RTT just would hang with the highspeed.

Anyhow so I heard that Feisty works perfect with EV-DO and decided to try it. So far so good but with Feisty I cannot play any videos or DVDs while using the Intel video driver mentioned in this thread. With a vesa video driver I can play videos but in general graphics are very slow. 

Is there a workaround that will change things so I can get picture as well as sound in Totem, MPlayer, Kaffeine, etc? Right now it's either a black or a blue screen. Unless I change to the vesa driver, which is awful slow and jerky.

Thanks,
Jeremiah

---

### Post by lingenfr on 2007-06-10
Rats. I hadn't noticed that I couldn't play DVD's with the intel driver. I am thinking about downloading the source and compiling my own to see if I get different results. If you have the time, please document your success with your EVDO here:

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaLibrettoU100](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaLibrettoU100)

---

### Post by jsenner on 2007-06-10
If you get it all working that would be awesome! I'm a beginner and depend on experts to help me out.

EVDO was totally straightforward. Just follow the directions on this site.

Jeremiah

---

### Post by lingenfr on 2007-06-28
We all depend on each other to get things working. Again, go to the wiki and post your results. I'm not too motivated to help folks who won't pitch in.

---

### Post by jsenner on 2007-07-19
I discovered a solution that works; replace the video driver with this; [http://ubuntuforums.org/attachment.php?attachmentid=37549&d=1183829057](http://ubuntuforums.org/attachment.php?attachmentid=37549&d=1183829057)

It is awesome to have a fully functional Libretto now!

Jeremiah

---

### Post by brownrc on 2007-08-05
Where did this deb come from and is it available via apt? Am I correct to assume that dvd/video playback works with this new driver?

RCB

---

### Post by jsenner on 2007-08-05
I found this somewhere on this forum.... and I don't know if it's available via apt. Dvd/video playback does work really well using this!

Jeremiah

> **brownrc said:**
> Where did this deb come from and is it available via apt? Am I correct to assume that dvd/video playback works with this new driver?

RCB

---

