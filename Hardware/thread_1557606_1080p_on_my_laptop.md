---
title: "1080p on my laptop"
date: 2010-08-21
forum: Hardware
---

### Post by santiagorf on 2010-08-21
Hi all,
Since videos in 1080p are very choppy, and I can hardly play in 720p, I was wondering if there is something wrong in the configuration of my **Acer 5534**, or is it just not powerful enough?

My system is the following:
[FONT=Courier New]*Ubuntu 10.04 (32 bits)

*CPU
Name                : AMD Athlon(tm) Processor TF-20
Family, model, stepping    : 15, 124, 2 (AMD Opteron/Athlon64/FX)
Cache Size        : 512kb
Frequency        : 800.00MHz
BogoMIPS        : 1595.86
.....

*GPU
ATI RS780M/RS780MN [Radeon HD 3200 Graphics]
[/FONT]

Any idea? 
thank in advance!!
santiagorf

ps: I've used the last version of VLC as the video player.


= = = = =
Mörgæs 2013-12-05:
Using Lubuntu 13.10 and the default open source drivers everything works well.

---

### Post by luisito on 2010-08-21
In my computers I have only been able to play 1080p smoothly using the VDPAU driver from NVIDIA. I don't think such kind of driver is available for linux for ATI cards.

---

### Post by linux18 on 2010-08-21
three ways to boost decoding speed:
-limit your session to a player and an x server (and even no x server)
-mplayer and the newest (1.1.2) vlc offer speed improvements for decoding.
-use the ogg vorbis codec, which decodes much faster

---

### Post by cascade9 on 2010-08-21
A TF-20 (sinlge core Athlon, 512k cache, 1.6Gz) is probably a bit low to work well with 720p CPU video decoding. If you had an Vidia card (8000 series or higher) it would be easy, just enable VDPAU, but no nvidia card makes it more difficult.  

There is XvBA (X-video bitstream acceleration) for ATI cards. I'm not 100% sure that XvBA runs on a 3200 (it needs at least UVD2 or later, the 3200 has UVD2 'lite'), but XvBA is probably the only way to make that computer play 720p videos smoothly, and it might even let you watch 1080p videos.

---

### Post by emma123 on 2010-08-21
yeah you both are right.. firstly the singly core is (1.6) is little slow to play 1080p/i quality DVDs but if you had nvidia chipset graphics it can certainly help to accelerate, but for ATI i don't have any idea. i have Nvida fx5200 and it not only plays 1080 but also 1980 very well via VLC media player but because there is an option on vlc settings that get help from your graphic processor to boost up the video.

---

### Post by tjktyler on 2010-08-21
Is your monitor capable of displaying 1080p? If not, the video will be choppy. (This was the case in Windows and Ubuntu with reasonably powered hardware)
And yes, hardware might also be an issue. DVDs themselves (480p) require at least a 500MHz processor to decode. So I'm sure that 720 and 1080p also require more power. Exactly how much, I can't say.

---

### Post by santiagorf on 2010-08-23
Thank you for your replies. I have installed XvBA, and now I can watch 720p movies flawlessly. However, I'm still not able to watch them properly in 1080p. As you mention before, it might be that the computer is not powerful enough.

---

### Post by cascade9 on 2010-08-23
@emma123- 1080p is 1920x1080, 720p is 1280x720. 

@santiagorf- I'm glad that XvBA helped. Pity it wont quite do 1080p, but its over twice as much to decode compared to 720p.

---

### Post by roy913 on 2010-08-23
have you had a look at the site of cutting edge multimedia?

VAAPI may be your solution

[https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia]("https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia")

*****the below approach can break down your whole system, try it at your own risk****
1. add both of the 2 PPA into your software sources, then install driver for FGLRX, then reboot
2. install their vlc player or smplayer or both of them
3. follow the instructions in cutting edge multimedia to configure your player settings

i m using an old 945gse chipset and playing 720p with vlc nicely, 1080p seems unwatchable though. but yours is HD3200 so it shouldn't be a problem, i can play 1080p without a hitch in smplayer with a nostalgic nvidia 8500gt.

---

### Post by costre on 2010-10-23
How did you go about activating xvba? I am having trouble getting it to work, CPU is still under heavy load.

---

