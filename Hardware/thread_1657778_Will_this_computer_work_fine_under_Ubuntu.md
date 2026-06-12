---
title: "Will this computer work fine under Ubuntu?"
date: 2011-01-01
forum: Hardware
---

### Post by mrover on 2011-01-01
Hi,
I'm going to buy new computer. I really would like parts to be compatible with Linux especially Ubuntu.

```

AMD Phenom II X6 1100T
ASROCK 890GX EXTREME 4 / Integrated AMD Radeon HD 4290
Radeon HD 5770
```Did anybody have any problems with them?

I'm not sure when will I buy this computer so if you read it like 6 months after I posted, please answer.

Best regards,
mrover.


*Sorry for my english.*

---

### Post by elliotbeken on 2011-01-01
It should be ok

i have the 5770 with ubuntu and its fine using the ATI drivers

---

### Post by Giraffemonster on 2011-01-01
Ubuntu should be compatible with most computer components, including the ones you've listed. Performance-wise, these parts should be more than enough to run Ubuntu with enough resources left over for other applications.

I've heard that nVidia is more Linux friendly than AMD, but it should all work out. No problems with the hardware.

---

### Post by cascade9 on 2011-01-02
Should work fine, but I'd drop the Asrock 890GX motherboard and get a 890FX motherboard, probably from gigabyte (you dont need 890GX with onboard video if you are getting a video card)

---

### Post by mrover on 2011-01-02
Thanks for advise.
I'm not getting this video card soon.
It's a card I'm interested if I would decide to upgrade. I'm not into games or 3D graphic, just possibility to watch 720p would be OK.

Is it only reason you advised to change motherboard?

---

### Post by cascade9 on 2011-01-02
If its just for video (720p) and you dotn want to play games, etc, dont get 5770, get an nVidia GT210/220/240. 

nVidia VDPAU (hardware video decoding on the video card) works well, ATI has XvBA (x-video bitstream acceleration) as well, which doe the same thing but its buggy.  

Not quite the only reason why though.....890GX chipsets are overpriced IMO. You can get an 870 + video card for less. Also, I'm not at all impressed with any of the asrock motherboards I've seen lately.

---

### Post by mrover on 2011-01-04
Thank you very much!

After releasing Sandy Bridge I decided to hold on.
So, thank you for your answers. I think topic can be closed.

---

### Post by cascade9 on 2011-01-04
You'll pay a lot more for an intel CPU with similar perfromance to the X6 1100T, just in case you dont know ;)

---

### Post by njsharp on 2011-01-04
I am in the process of working towards a new PRV based on ASRock 890GX Extreme4.  At present:

Athlon 2 core 3.2GHz
2x2G 1333 RAM
Samsung BD reader (+DVD/CD/RW of coruse)
2x Kaiser Baas KBA01008 DVB-T tuner sticks
And preloved:
Optical fibre from onboard 5.1 to a Yamaha amp
Case with good side fan aimed at the cpu
2x 250G Sata 3Gbps WD HDs
450W PS
CRT 1280x1024 VGA
DFP 1920x1080p HDMI

Ubuntu 10.10 AMD 64
MythTV 0.23
VLC 1.1.4

I chose the MB because it seems to have quite a future, allowing up to 16G RAM, Phenom 6 core, 5x SATA 6Gbs and offering both USB 3 and e-SATA 6Gbs as well as built in optical fibre audio out.  The twin USB 3 mount that exactly fits the front floppy bay is cute!

I reckoned the Athlon 2 core would be enough for now, and would not strain the reused PS.  Also, I hoped the on-board GPU Radeon 4290 (VGA and either DVI or HDMI out) would keep the budget down whilst delivering enough grunt for PVR, even though you wouldn't use it for serious gaming:

[http://www.phoronix.com/scan.php?page=article&item=amd_hd4290&num=3](http://www.phoronix.com/scan.php?page=article&item=amd_hd4290&num=3)

I'd agree with cascade9 about getting 890FX not GX if you want gaming, plus your choice of grunty GPU.

I have not been disappointed with my choice of 890GX for PVR use...

Initially, on top of U10.10 I loaded the proprietary flgrx ATI Catalyst code for the GPU, but found it was not a great approach.  In particular, I could not for the life of me find the MythTV setting where I could point the TV playback to screen 1 (DFP) whilst using the CRT for the desktop.  I've seen remarks about flgrx not being the best for dualhead.


Working up a PVR on two screens is nice as you can run eg:

mythfrontend --verbose "<your choice>"

on a terminal window on the small screen and watch for trouble, and see resolution changes as you switch to HD channels, plus run System Monitor or htop to check performance.

(Alternative to second screen is to ssh in from another PC on the LAN.  I might go there if I later get a decent flat screen TV as monitor.)

So I tried to chuck out flgrx and rely on xserver-xorg-video-radeon and xserver-xorg-video-ati instead.  Failure, but ...

... after a complete U10.10 reload, the xserver code worked just fine.  I then tried setting VDPAU in MythTV, which I think was quite ignorant of me, since I suspect VDPAU is solely NVidia at this time, but I noticed on HIGH QUALITY the TV appearance looked better than on my older but almost as powerful Dell 9150 PVR which uses VDPAU to GeForce 9500.  So I replaced the Dell's VDPAU setting by HIGH QUALITY and it improved (no tearing on movement).  I'm really very puzzled by the whole issue of getting the GPU to do some of the MPEG>pixels work, not to mention trying to monitor the GPU to see how much work it is doing and how hot it is getting.

The Kaiser Baas sticks (now AU$50) seem very good.  They are immediately recognised (cold state) by U10.10 and given the correct firmware (see dmesg|grep "dvb\|DVB") to become warm state..  They are so sensitive that with a good aerial sitting just out of line of sight (hill in between) to the Sydney Gore Hill/Artarmon/Willoughby collection of transmitters, they also catch channel 9 on UHF from the Kings Cross or North Head repeater, which is actually a minor problem doing the channel scan, as they conflict with 9 VHF from Willoughby.  (I ditched 9's UHF scan results).

I used 2x these single sticks (plus an aerial twin splitter) on a suggestion from KB Sydney, but perhaps their more recent twin tuner stick would be good, simpler, and cheaper.  Two tuners of course allows simultaneous receiving channels from two different frequencies.

I have turned on ASRock's BIOS OC tweaker at "30%" performance increase (which looks more like 20% to me since the CPU clock goes up from 200 to 240) which seemed good, but trying to squeeze more by manual adjustment caused reboots.  Scary!  I'm not much into over clocking.

Perhaps the best measure of success is that after OC"30%", VLC playing a bluray file gave excellent viewing and listening with about 40-60% average usage on both cores, varying with video complexity.  At the time, mythbackend was also running, sometimes using about 10%.  I doubt if anything MythTV would ask for would come close to 60% even on a 1920 x 1080i HD channel.

Sorry if some of the above is a bit shorthand and not very rigorous, but it might help someone.

---

### Post by cascade9 on 2011-01-05
> **njsharp said:**
> I'd agree with cascade9 about getting 890FX not GX if you want gaming, plus your choice of grunty GPU.


... after a complete U10.10 reload, the xserver code worked just fine.  I then tried setting VDPAU in MythTV, which I think was quite ignorant of me, since I suspect VDPAU is solely NVidia at this time, but I noticed on HIGH QUALITY the TV appearance looked better than on my older but almost as powerful Dell 9150 PVR which uses VDPAU to GeForce 9500.  So I replaced the Dell's VDPAU setting by HIGH QUALITY and it improved (no tearing on movement).  I'm really very puzzled by the whole issue of getting the GPU to do some of the MPEG>pixels work, not to mention trying to monitor the GPU to see how much work it is doing and how hot it is getting.

I probably should have qualified my 890FX comment more. They are good boards, but if you arent overclocking then a 870 is just as good (even if you are overclocking the 870 is still great). 

VDPAU is nVidia only. I havent noticed any major difference between VDPAU output and normal output, but I probably wasnt lookign for it. My main media box is to old for VDPAU anyway (6600GT) so I dont use VDPAU that much. 

There is XvBA for ATI cards, but its, well, buggy.

---

