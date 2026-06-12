---
title: "FullHD 1080p runs slowly on intel GMA 4500MHD"
date: 2010-04-25
forum: Hardware
---

### Post by baleks on 2010-04-25
I have acer 1410 laptop with 2-core intel celeron su2300 processor@1.2Ghz and intel GMA 4500MHD

This GPU capable to play 1080p video but when i try this only audio plays well, but video plays slower that the audio. mplayer -framedrop is not the solution - it drops too many frames.

When i start 1080p video in mplayer, sudo intel_gpu_top shows me only 15-20% gpu load !

How to fully use resourses of my gpu ? Or it's better to try installing coreAVC decoder ?

---

### Post by dino99 on 2010-04-25
i've no experience with this chip but it have to share ram and its certaintly and issue, what say system monitor about ram and swap ? The other question is bus width

---

### Post by baleks on 2010-04-25
> **dino99 said:**
> i've no experience with this chip but it have to share ram and its certaintly and issue, what say system monitor about ram and swap ? The other question is bus width

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          2956       2843        112          0        124       2003
-/+ buffers/cache:        716       2240
Swap:         4094          0       4094

```

I have 2 DDR2 banks installed in this laptop: 2Gb 666mhz + 1Gb 800mhz (originally was 2x1gb 800mhz but i need more ram). 
If it is the issue, how can i get round it ?

---

### Post by baleks on 2010-04-25
I tried to install mplayer that supports VA-API (wondering why it is not in ubuntu repositories yet?)

According that manual: [http://www.drupal4hu.com/node/244](http://www.drupal4hu.com/node/244)
+ [http://ubuntuforums.org/showthread.php?t=1234502&page=3](http://ubuntuforums.org/showthread.php?t=1234502&page=3) - this thread was helpful for me to use -vo xv instead of -vo vaapi (or disable compiz, but -vo xv is better even in this case)

best options for mplayer-vaapi that now works for me is: (-vf scale -vo vaapi OR -vo xv) -va vaapi -framedrop
But framedropping is still very hard especially on dynamic scenes. 
intel_gpu_top also showing not more 30% usage of gpu.

---

### Post by baleks on 2010-04-25
> **dino99 said:**
> i've no experience with this chip but it have to share ram and its certaintly and issue, what say system monitor about ram and swap ? The other question is bus width
I tried to restore original configuration (2x1gb 800mhz ram), and did not feel any significant difference in playing video, nor in memtest86+ program: [http://yfrog.com/hqdsc01838njx](http://yfrog.com/hqdsc01838njx)

---

### Post by dino99 on 2010-04-25
can try the hard way:

sudo dpkg --configure -a  and delete .pulse

---

### Post by baleks on 2010-04-25
> **dino99 said:**
> can try the hard way:

sudo dpkg --configure -a  and delete .pulse

How can removing .pulse directory helps in playing a video ?
It feels like you reacting to my post in another thread ;)

---

### Post by baleks on 2010-04-25
I tried mplayer, vlc, totem
But now i tried to watch 1080p in xine - it's definitely best!
Althought it says to me that my system is slow to play this file, and drops frames - but it does it SO NICE, that video becomes real viewable!

Of course, using xine to watch full-hd videos is not the solution to problem, but temporarily fix

UPD: I found that i can view movies that are about 9Gb and less ;) 12Gb - too slooooooooowwwwwllllyyy... :(

---

### Post by DLGandalf on 2010-05-19
the gma4500mhd has no support for vaapi (yet), strangely enough they are implementing this for the i3 cpu's with integrated gpu, I think the gma4500mhd has a bigger user base and laptop users need this a lot more. I can only speculate that there are some legal issues at play for the gma4500mhd decode unit. I have asked multiple times on a status update on the mailinglists, but I only get evasive answers and roadmaps with dates already due.

---

### Post by baleks on 2010-05-19
DLGandalf, thanks for information!

Now i partly solved this problem using [CoreAVC decoder on linux]("https://launchpad.net/~ripps818/+archive/coreavc") that use about 90% of my 2-core CPU (su2300) on any up to 17Gb movie and it plays smoothly. 20Gb-videos are not always plays smoothly, but it's not big problem ;)

Also i find that if i just use mplayer option "-lavdopts threads=2" (for 2-core cpu) it really gets better, maybe almost like with coreavc codec!

---

### Post by nhooey on 2010-10-13
Does anyone have any updates on the Intel GMA 4500MHD and 1080p playback in Linux?

---

### Post by PaulReaver on 2010-10-13
really impressed with Maverick....
I was surprised today to find out that my little atom n270 netbook with a gma950 running ubuntu 10.10 can play 1080 hd DivX videos... :D   high cpu usage, but it manages to play fullscreen without stuttering.

mind you I don't really see the point as my screen is only 600 high.. lolz

just goes to show never trust a hardware vendor...

---

