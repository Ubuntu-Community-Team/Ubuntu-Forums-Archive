---
title: "Dual monitor -video = blank screen"
date: 2010-01-03
forum: Hardware
---

### Post by katoiam on 2010-01-03
hello y'all,
I have a question and Im sure I have seen it some where before but can find any thing on it here at the moment! I am trying to connect my laptop a flat screen tv. I can get it to work fine it detects the resolution and everything, but I have 2 gripes, 1 (minor) when I go to fullscreen youtube it moves it to the laptop!!! and 2 (main) when I play videos while I have 2 screens the video is blank even though the audio plays, on both monitors. I am running ubuntu on this one, I had a similar problem on my kubuntu laptop but at least the video worked on the laptop but not on the tv screen!! Im confused and require help!!!!
thanks in advance
ciao
katoiam

---

### Post by iltrix on 2010-01-08
Hello

I have exactly the same problems as you describe.

Problem 1: This is a known problem with flashplayer and is related to the fact that flash picks the screen with number zero to play full screen.

Problem 2: More difficult. I'm clueless about what might cause this. I have this problem on a Macbook1,1 with Intel 945GM graphics chipset. I noticed that this problem disappears when I mirror my screens. (tested this on different screens and with a beamer). 

Can anybody provide more insight in this?

Thanks a lot in advance

Kind Regards

Thomas

---

### Post by daboz1981 on 2010-04-19
This problem affect also My Dell mini 9 Ubuntu 9.10  connected to A TV lcd samsung 22" via VGA cable.

---

### Post by wfgJeru on 2010-05-16
Also occurs with my MSI Wind running Lucid, which I hooked up to a Samsung Syncmaster 20" via a VGA cord.

---

### Post by zenek89 on 2010-05-16
I have "Nvidia x" or something like this on my ubuntu 9.10 and I just simply can adjust it... but U have to switch resolution of your laptop or PC to the same as your TV and set TV as "clone". If U're using analog cable to connect to TV resolution is supposed to be 1024x(something) sorry for not being totally specific. But unfortunatelly I lost GUI on my ubuntu and I'm trying to get it back.

When I'm using them as clones, video works on both.. no matter if it's flashplayer or any other programs

---

### Post by Obfuscator on 2010-08-27
This is somewhat similar to what the driver does on windows too - if you have multiple monitors the card only renders to one of them - unless you have clone enabled. I think this is due to the fact that the output is hardware accelerated and bypasses the window manager somehow. I would expect the output to reach one monitor though.

Anyway, what works fine is to turn all all monitors but one off in the display settings.

---

### Post by miniac on 2010-08-30
hi all,

I was having a similar problem with my MSI Wind U100 Netbook running Lucid NBE until I found a site a while ago (which I've conveniently lost) which I think explained the issue. It was much more detailed than any explanation I can give but I'll try and give the gist of it. It's actually quite simple.

Apparently with certain video cards (like the Intel GMA 950 in the U100) there is a maximum allowable "desktop space" in pixels which the driver/card can handle..the number 2048 rings a bell. By running screens side by side you would exceed this horizontal limit, where if you run the screens "stacked" one on top of the other it will be within the vertical and horizontal limit.

So the solution for me was actually simple - in the display settings I merely move the positions of the two monitors from being side by side to stacked - which meant that it took a little while to get used to dragging up and down to get to my other screen, but also that I could watch video on either screen while the other one is running.

---

### Post by Obfuscator on 2010-09-08
Found this bug related to this problem: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/460616]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/460616")

---

### Post by Obfuscator on 2010-09-08
Also found [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2"). It says 'Note that the maximum supported size of the virtual desktop for the Intel 945GM series of chipset with 3D acceleration enabled, is 2048x2048. The virtual screen can be larger but DRI will be disabled.' Is that you were talking about, miniac?

---

### Post by 130s on 2011-03-01
I was experiencing exactly the same phenomenon described in this page: [http://ubuntuforums.org/archive/index.php/t-1499087.html]("http://ubuntuforums.org/archive/index.php/t-1499087.html")

This solution by miniac worked perfect on my environment. Thanks!

> **miniac said:**
> 
So the solution for me was actually simple - in the display settings I merely move the positions of the two monitors from being side by side to stacked - which meant that it took a little while to get used to dragging up and down to get to my other screen, but also that I could watch video on either screen while the other one is running.

Ubuntu 10.04 Netbook edition with VLC media player

---

