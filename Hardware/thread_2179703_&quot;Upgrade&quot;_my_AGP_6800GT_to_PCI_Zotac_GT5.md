---
title: "&quot;Upgrade&quot; my AGP 6800GT to PCI Zotac GT520?"
date: 2013-10-09
forum: Hardware
---

### Post by Jaguarandine on 2013-10-09
Hi,

I'm currently running Ubuntu 12.04 on a computer with these specs:

Asus TUV4X motherboard
1.4 GHz Tualatin P3 w/ 512k L2 cache (I know! Ancient!! :) )
BFG Nvidia GeForce 6800 GT (256 DDR2 RAM), AGP version
1.5GB PC133 SDRAM
PC Power & Cooling 370W power supply

Aside from some driver troubles, this system has worked like a champ. I could play the occasional game (circa 2004 ;) ), web browse, etc. The last couple years though, I've neglected my desktop for my laptop, tablet, and smartphone. 

What I would like to be able to do is run Netflix, Hulu, HBO Go, Youtube, and some 1080p videos using the x264 codec. Right now, the desktop can play 720p videos encoded to mpeg4 just fine, but chugs on everything else. 

I've heard a lot about vdpau and how it allows GPU-assisted video acceleration, and that it should be a cinch with a PCI card, even on a desktop as old as mine (correct me if I'm wrong). However, I would not want the DE environment to suffer as a result. I like Unity, and would rather not have to switch to something like Lubuntu, if possible.

So my question is, Could I replace my 6800 GT with a PCI (not PCI-E) GT520, and have a similiar experience while adding the features I want? Thanks for your help!

---

### Post by grahammechanical on 2013-10-09
You are going from AGP to PCI and that must be an improvement. Now you need to compare the specifications of both cards. Which has the more powerful GPU? Which has the more memory?

---

### Post by Yellow Pasque on 2013-10-09
> **grahammechanical said:**
> You are going from AGP to PCI and that must be an improvement.

False. [https://en.wikipedia.org/wiki/Agp#Advantages_over_PCI](https://en.wikipedia.org/wiki/Agp#Advantages_over_PCI)

> Which has the more powerful GPU? 
The 6800GT was a top of the line card, so even though it's older, it will probably still run circles around a lowly 520GT when it comes to 3D power.

> Which has the more memory?
That's not really a good measurement for GPU's. The marketers figured out that they could gain an advantage over competing cards by loading up a card with cheap memory even if the GPU wasn't fast enough to take advantage of it.

---

### Post by Jaguarandine on 2013-10-10
> **grahammechanical said:**
> You are going from AGP to PCI and that must be an improvement. Now you need to compare the specifications of both cards. Which has the more powerful GPU? Which has the more memory?

That would be a great option if I had it, but unfortunately, my mobo has no PCI-E slot, only regular old PCI. Of course when dealing with regular PCI, any card would have to share the bandwidth with the other cards on the bus, and that bandwidth isn't that great to begin with. So, any PCI-based video card is going to be handicapped. The 9-year old 6800 GT AGP card may be better than any new PCI video cards for that reason. However, I'm not sure about this. It's too bad that only series 8 cards can accelerate video, otherwise I think the 6800GT (series 6) would be up to the task. I just want to use vdpau, run Unity, and play a little Doom 3 ;)

---

### Post by Jaguarandine on 2013-10-10
On another thought, what's the state of ATI Linux support? I remember it not being too good a few years ago. But if things have improved, and I could somehow fit an AGP HD4670 in there, I think that would be the ideal situation. As the 6800GT still fetches a good price on ebay, I could sell it and upgrade to the ATI for little cost.

---

### Post by Yellow Pasque on 2013-10-10
^It's a good idea on paper, but AMD/ATI support for AGP cards is terrible.

> play a little Doom 3
Expecting a PCI 520GT to play Doom3 is a bit much...

---

### Post by Jaguarandine on 2013-10-10
Lol, your probably right about the Doom 3.

I had an interesting idea.

Worst case is that I buy the GT520, bite the bullet, and replace my 6800GT for vdpau. I could switch out the cards based on demand. This is incredibly inconvenient and something I want to avoid, obviously. 

Or, I could install both at the same. Of course I'm not talking about some silly SLI type setup (which would be ideal really, but impossible). But this way:

Ubuntu supports adding a second video card for dual monitors. But instead of using a second monitor, I use only one monitor that has a two video inputs. I could plug one graphics card into VGA and the other into DVI, for example, and switch between the two on demand. Using this, I might go for any series 8 PCI card, because all of them can do vdpau.

What do you think? So crazy it might work?

---

### Post by Yellow Pasque on 2013-10-10
I don't have a lot of experience with multi-monitor, so I don't know, but my gut feeling is that it won't work the way you think.

> I might go for any series 8 PCI card, because all of them can do vdpau
A G98-based 8400GS is probably best in that regard, because it has VP3: [https://en.wikipedia.org/wiki/Purevideo](https://en.wikipedia.org/wiki/Purevideo)
I'm using one of those right now (PCI-E), but OpenArena is probably the most challenging 3D task I've thrown at it.

---

### Post by Jaguarandine on 2013-10-22
A few things have happened since I last posted here. Firstly, I was able to overclock my Tualatin CPU to 1.63 GHz, with a FSB of 155 MHz. It's been very stable, and it's made Ubuntu a lot faster. The second thing is that I've been trying out Lubuntu, and so far it's extremely snappy. Thirdly, I've been using SMPlayer with the Youtube plugin. Other than straight mplayer, this is the most lightweight video player I have ever used. I've been able to get 1680 x 700 videos to play great in Lubuntu. Also, with flash eliminated, SMPlayer can play 480p fullscreen videos with ease, including the ability to download 720p videos (and re-encode.. pesky x264 stuff prevents straight playback). So the situation has greatly improved without the new graphics card.

I still do wish for vdpau, so i see myself as having 2 options here: 

1) Build another computer. This is obviously the most logical choice, but I can't see myself spending the $300 or so I would need to make another desktop right now. In the future, sure. 
2) Modify the vdpau source so it can use the 2nd graphics card. I've looked a little into this option, and it seems at least plausible. If I could make vdpau look for a second graphics card, instead of just stopping the search at my 6800 GT, I think that would allow me to use both cards; the 6800 GT for the DE and games, and the 8-series for video. The only reason I think it does not work now is that my situation is pretty unusual. It will be a while before I attempt and research this though, maybe a few months. But I will make sure to report back here with any findings.

Thanks again for your help with this issue **Temüjin**!

---

