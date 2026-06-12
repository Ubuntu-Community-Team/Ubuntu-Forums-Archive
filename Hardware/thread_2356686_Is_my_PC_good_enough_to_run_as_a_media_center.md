---
title: "Is my PC good enough to run as a media center?"
date: 2017-03-25
forum: Hardware
---

### Post by greenlivingtim on 2017-03-25
Hi all, new to the forum, and whilst I've dabbled with linux in the past I still consider myself a beginner as I have to relearn everything each time I come back to it! I'm currently investigating the prospect of setting up an old PC I have inherited as a simple browser and movie watching machine in the lounge, just wanted your thoughts on whether it's up to the job, if it needs upgrading or if I should just trash the thing!

Basic specs are as follows:

Dual core Pentium E5400 2.7Ghz
4Gb ram
Radeon HD 2400 Pro
500gb HDD

I recovered the gpu from another machine as it's capable of outputting sound through the dvi, so with an adapter I can plug it straight into the tv and get video and audio. Currently running elementary OS 0.4 Loki (based on Ubuntu 16.04 LTS) as I liked the look and layout of it for a media based pc, however I'm open to other suggestions. At present performance is average, video is just about watchable but a bit choppy, tho this may be a software issue.

All advice is welcome and at this stage more than necessary!

Ozz

---

### Post by cariboo on 2017-03-25
If you can run [Kodi]("https://kodi.tv/") on a Raspberry Pi, your system specifications are more than enough.

---

### Post by SeijiSensei on 2017-03-26
The only problem I see might be the video card.  AMD does not offer a proprietary driver for the Radeon 2400 so you're left using the open-source driver that comes with Ubuntu.  

For a player, I use smplayer as the GUI interface to the mpv player software.  Try
```
sudo apt-get install smplayer mpv
```
then go to Options > Preferences > General in smplayer and choose "mpv" from the engine drop-down box.

---

### Post by Perfect Storm on 2017-03-26
A better video card could do the trick.
Your current card is supported through ubuntu/elementary: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by greenlivingtim on 2017-03-26
Thanks for the replies, all good advice. So far I can put up with the performance apart from the choppy video playback. I'll give smplayer a go to see if it improves but the playback wasn't good when streaming either, could this be a codec issue? I read somewhere about altering the config file to change the tear setting but this went over my head a bit!

Also if I decide to replace the graphics card, could you suggest an affordable replacement? Would need to be something with in-built sound so that I can run the hdmi easily through my home cinema.

---

### Post by mörgæs on 2017-03-26
Before buying more stuff I suggest that you try the performance in a fresh install of Lubuntu.

---

### Post by Autodave on 2017-03-26
Nvidia card is the way to go. A one gig w/DVI will probably be $50 or less, new on Amazon, Newegg, etc.

---

### Post by RobGoss on 2017-03-26
It's always best to try different distributions before you buy and start replacing your hardware it can be costly and in some cases not needed, you'll be surprise what will work when given a chance. As suggested try a** lighter distro** and see how that works

---

### Post by Yellow Pasque on 2017-03-26
I don't think a lighter distro will help in this case. My advice would be to make sure you have video decode acceleration enabled and use VDPAU for your video output in whatever video player you're trying to use:
```
sudo apt-get install mesa-vdpau-drivers vdpauinfo
vdpauinfo
```

[QUOTE=SeijiSensei]AMD does not offer a proprietary driver for the Radeon 2400 so you're left using the open-source driver that comes with Ubuntu.[/QUOTE]

You make it sound like a bad thing. For video playback, the open source radeon driver works better than fglrx/Catalyst ever did.

---

### Post by SeijiSensei on 2017-03-26
> **Temüjin said:**
> You make it sound like a bad thing. For video playback, the open source radeon driver works better than fglrx/Catalyst ever did.
I only ever buy NVIDIA cards.  I have an HP laptop with a built-in ATI adapter on which I run fglrx.  It has no problem playing HD H.264 video.  Otherwise I avoid AMD/ATI video because NVIDIA has much better support for Linux.

I bought a [GTX 750 from MSI]("https://www.newegg.com/Product/Product.aspx?Item=N82E16814127870") which cost about $100 because I occasionally play Windows games.  You can get [decent NVIDIA cards for $50-75](https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=50001441&IsNodeId=1&Manufactory=1441&bop=And&SpeTabStoreType=0&Order=PRICE&PageSize=60).

---

### Post by greenlivingtim on 2017-03-26
Thanks guys, will try the vdpau drivers first as I would like to stick to this distribution if I can, it fits the kind of use I want for this machine. If that doesn't work I'll try out a lighter one, and in the worst case I'll replace the gpu. This machine is cobbled together from a few old pc's so there's a chance the card might be faulty, I don't know what kind of a life it's had! Next step will be replacing fans with quieter units as it's a bit noisy at the moment for a movie machine! Thanks for all the good advice!

---

### Post by RobGoss on 2017-03-26
Good luck let us know how the installation goes

---

### Post by SeijiSensei on 2017-03-27
If you get vdpau running, you can select it in smplayer from the "output driver" drop-down box under Options > Preferences > General > Video.  You'll likely lose the ability to take screenshots with vdpau as the driver if that matters.  (With vdpau the graphics card decodes the H.264 stream straight to the video device so the player software doesn't have access to the video output.)

---

### Post by sp40140 on 2017-03-27
We are on edge of 4K. So, If you get a graphics card, I suggest you go with the one which supports 4k. Otherwise, you can run 1080p in GeForce 210 as well (an old and cheap card). I have that in my old core2Duo machine which I use with my home theatre. It renders 1080p @60Hz on 125" screen. No issues. I run into problem only when I use VLC and try to skip forward or go back. I only use SMPlayer. Don't have issues at all.
Your hardware specs look good enough to me for HD playback. the playback performance could be related to drivers and the application you use for playback.

---

### Post by greenlivingtim on 2017-03-27
Top marks for the vdpau drivers, they sorted out the streaming playback but not the video file playback. Switched to smplayer and perfect image quality, so all in all very pleased!

its a good point about the 4K, I think I'll hold off upgrading the card and then get a 4K one when we upgrade our tv!

Next step is going to be replacing fans with silent units and an ssd to run the os, maybe a bit more ram if I can salvage some and I think it'll be a decent little media center! I'm considering running kodi to organize my film collection, I couldn't get on with it as the main interface but just as a file organizer it could look quite neat!

---

### Post by sp40140 on 2017-03-27
Good news!
I understand the temptation to upgrade. However, I advise against throwing any money at this machine. I would just let it run for as long as it does. And that's why I mentioned 4k support for gpu as you can just take it out and put it in the new machine you get. 
You can get Amazon fire TV with 4k support for $90 (sometimes $65-70 on sale). so, for the price of upgrades, you can get powerful media streamer. You can keep the old machine as file server (out of sight).
Lot of these depends on your circumstances though.
Also, if your issues are sorted, you can mark the thread closed.

Cheers

---

