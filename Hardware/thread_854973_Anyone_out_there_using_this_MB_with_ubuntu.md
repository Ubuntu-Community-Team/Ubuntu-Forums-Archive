---
title: "Anyone out there using this MB with ubuntu?"
date: 2008-07-10
forum: Hardware
---

### Post by DJANIMATE on 2008-07-10
Hello all,

  I'm seriously considering replacing my media center which currently runs Windows Media Center with new hardware running Mythbuntu. It's one of the first generation AMD 64's and just can't handle anything above 720p HD movies (.mkv files) so I think it's time to upgrade. 
  I use my media center to play movies and some games on my 50" plasma in the Family room. I store all my movies on a server in the office and just pull from it across the network (hardwired).
   It's been a while since I used Linux, so I've been outta the loop as to it's current capabilities. The last time I used it, it was still very hard to find drivers for much of the hardware I had so I had to settle for Windows. 
   Anyway, I wanted to ask you knowledgeable folks what you think of the motherboard I picked out, specifically, if you see any problems with running Mythbuntu on it. Here are the specs:

Foxconn A7GM-S AM2+/AM2 AMD 780G HDMI Micro ATX AMD Motherboard
Found here [http://www.newegg.com/Product/Product.aspx?Item=N82E16813186141]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813186141")

CPU Socket Type  	 AM2+/AM2
CPU Type 	Phenom FX / Phenom / Athlon 64 FX / Athlon 64 X2
FSB 	2600MHz Hyper Transport (5200 MT/s)
Chipsets
North Bridge 	AMD 780G
South Bridge 	AMD SB700
Memory
Number of Memory Slots 	4×240pin
Memory Standard 	DDR2 1066
Maximum Memory Supported 	8GB
Dual Channel Supported 	Yes
Expansion Slots
PCI Express 2.0 x16 	1
PCI Express x1 	1
PCI Slots 	2
Storage Devices
PATA 	1 x ATA100 2 Dev. Max
SATA 3Gb/s 	6
SATA RAID 	0/1/0+1
Onboard Video
Onboard Video Chipset 	ATI Radeon HD 3200
Onboard Audio
Audio Chipset 	Realtek ALC888
Audio Channels 	8 Channels
Onboard LAN
LAN Chipset 	Realtek 8111B
Max LAN Speed 	10/100/1000Mbps
Rear Panel Ports
PS/2 	2
Video Ports 	D-Sub + DVI
HDMI 	1 x HDMI
USB 	4 x USB 2.0
Audio Ports 	6 Ports
Onboard USB
Onboard USB 	3 x USB 2.0 headers support additional 6 ports
Physical Spec
Form Factor 	Micro ATX
Dimensions 	9.6" x 9.6"
Power Pin 	24 Pin 

My biggest concern is the video, audio, and LAN support. Anyone know of any known issues with any of these? The things I must have in order to replace my current setup are:

1. Ability to connect to, and play movies from a Win2k server
2. Ability to play HD .mkv containers with MPEG4 video and Dolby AC3/Dolby DTS audio 
3. Ability to play AVI (xvid), and WMV files

I've not looking for controlling or recording TV, but that might be something I use in the future. 

From what my research shows, I shouldn't have any problems with this motherboard, but I wanted to run it by you guys first so I don't get stuck with windows again. 

Thanks in advance,
Adam

---

### Post by Bruuuuuce on 2008-07-10
After just having gone through a very annoying period of trying to find a decently priced motherboard for a Phenom 9850 (I'm not a big gamer and don't want huge performance out of it, just stability) all I can advise is go to AMD's website and look up recommended motherboards.

Now let me be more specific - i got a 9850 125watter (bundled with an ECS MB that said it supported quad core processors -- stupid me should have made sure) apparently some of the cheaper MB run 95watt - this means that your system will appear to be stable but it's not -- trust me, mine ran awesome until i wanted to use that stupid thing called the ethernet port.

The board i originally bought had the AMD chipset, the replacement MB (from the same maker and same series) with an NVidia chipset seems to be working perfect (knock on wood).

This is the form for compatible motherboards [http://products.amd.com/en-us/RecommendedMBFilter.aspx](http://products.amd.com/en-us/RecommendedMBFilter.aspx)

After this crap I won't ever be trusting newegg to bundle together components that are actually compatible -- i won't even be trusting motherboard manufacturers to report which processors their systems are compatible with -- because ECS says the motherboard i currently have is NOT compatible with 125watt procs, but yet AMD says it is... If i could have returned it all I probably would have and gone with Intel.

But if you go with a 95watt proc, you should, apparently, be fine.

Good luck

---

### Post by DJANIMATE on 2008-07-10
Hello Bruuuuce, 

Thanks for your reply. I was actually thinking about getting a 65w brisbane core, specifically -
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103234]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103234")

Since AMD has nothing more efficient than 65w, I can't imagine any board not having the architecture to handle it. Nevertheless, I will take your words of wisdom and check out AMD's site. 
 
The main reason I like the board I picked is due the fact it has a good graphics chip set AND an HDMI video out. I plan to run straight from the PC to the TV. Currently, I go from VGA to a converter, which converts to component, then to my TV. While this works good, an HMDI connection would give the ability for higher resolution, a "cleaner" picture, and audio built in. My plasma doesn't have a VGA in, just composite and HDMI.

If anyone else knows of a good, responsibly priced motherboard that has HDMI and at least 5 channel sounds, and has been proven to work with mythuntu, I'm all ears. Thanks in advance. 

Thanks,
Adam

---

### Post by redcharlie on 2008-09-11
I bought a gigabyte ga-ma78gpm-ds2h and a brisbane x2 2400-BE (dual 2.3GHz core, 45Watt TDP) from NewEgg in late August.  Put the Hardy Heron on it and so far so good.  Even plays BZflag with just the integrated gfx, and the box idles at only 37 Watts!

---

### Post by deamon_knight on 2008-09-11
Also remember that your soundcard is what gives you audio, and this means for you to get sound through HDMI your soundcard must be connected to your video card. This may not be a problem if you are using the onboard sound, but be aware.

---

### Post by grege on 2008-09-11
I have the same Gigabyte board as redcharlie, but with an LE-1600 45w single core cpu ( equivallent to an Altlon 64 3500+ ). I do not play HD disk content, but DVDs and divx and HD TV all play smoothly. I also have the sound from the onboard spdif to my Yamaha amplifier and do the decoding there. Music sounds great and i get 5.1 through VLC for DVD playback. I do not use MythTV, I am happy with Kaffeine for TV, Amarok for music and VLC for divx/dvd. I use Kubuntu Hardy. All this works, so there is no reason it will not work in MythTV as well. I connected though the HDMI and did not see any great benefit over VGA, but that will depend on the panel you use.

It is necessary to get the latest fglrx drivers to get proper AVIVO playback through xv. It is attached to a Samsung LCD through normal VGA connection. I also have a WD Green Power Terrabyte hard disk for storage.

So far it is rock solid. The unit is very power efficient, the biggest power hog is the amplifier and subwoofer. I can also play back stereo through the TV speakers for content where sound is unimportant.

It is not an issue for MythTV, but avoid Compiz effects on a media box, they do not mix well with ATI video chipsets.

---

### Post by mr_raider on 2008-12-15
Sorry to bump this post but I'm looking at the same mobo. I notice it doesn't have SPDIF out, so it's either analogue or audio via HDMI. Can anyone confirm that audio over HDMI out works? I'd hate to have to resort to winblows just for this issue.

---

### Post by iggykoopa on 2008-12-15
another thing you'll want to think about is the codecs for 1080p (x.264 specifically) don't support multi-core decoding very well at the moment. Also nvidia just released updates to their drivers that will allow decoding to be sent to the gpu but it could be a little while before that works its way into most of the video players. I've got a 2.2 ghz phenom and have trouble playing back most 1080p, if your willing to buy the board now and wait a little for the support to be better than go for it. Heres a good post on phoronix about the nvidia stuff [http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau_gpu&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau_gpu&num=1) . I'd probably wait until the nvidia stuff goes mainstream then upgrade.

---

### Post by mr_raider on 2008-12-15
HD playback is not an issue. I'm just looking at SD MPEG-2 and xvid stuff.

Nevertheless, which nvidia/AM2 chipset would you suggest? Support for the 8200 seems to be spotty right now.

---

### Post by markbuntu on 2008-12-15
I have a Biostar TA790GX A2+ and for the money (~$100) it is great.

Any amd A2 or A2+ cpu including phenom ( using 6000 x2 for now)
5200 MTS bus
790GX chipset
16GB ram max, 1066 with phenom cpu
6 SATA/raid
2 Pata
1 floppy
1 rs232
ATI 3300 gpu w/hdmi/dvi/vga out
On board realtec lan
HDA ALC888, no digital out on the back panel but there IS A spdif header on the mobo for external plugs. also headers for front panel mic and headphones,
6 USB, 4 plugs on the back panel.
2 PCIE x2 slots
2 PCIE x1 slots 
2 PCI slots
blah blah blah...

Worked out of the box with existing Hardy i386 and amd64. Intrepid installed with no problems at all. Mandriva One also works fine.

Easy overclocking setup with a recovery mode if you go too far with that that will just reboot you back to bios defaults when it craps out, hardware monitoring and fan control all in the bios.

I just stay away from gigabyte. I see a lot of complaints/problems in the forums about them.

---

### Post by mr_raider on 2008-12-15
> **markbuntu said:**
> I have a Biostar TA790GX A2+ and for the money (~$100) it is great.

Any amd A2 or A2+ cpu including phenom ( using 6000 x2 for now)
5200 MTS bus
790GX chipset
16GB ram max, 1066 with phenom cpu
6 SATA/raid
2 Pata
1 floppy
1 rs232
ATI 3300 gpu w/hdmi/dvi/vga out
On board realtec lan
HDA ALC888, no digital out on the back panel but there IS A spdif header on the mobo for external plugs. also headers for front panel mic and headphones,
6 USB, 4 plugs on the back panel.
2 PCIE x2 slots
2 PCIE x1 slots 
2 PCI slots
blah blah blah...

Worked out of the box with existing Hardy i386 and amd64. Intrepid installed with no problems at all. Mandriva One also works fine.

Easy overclocking setup with a recovery mode if you go too far with that that will just reboot you back to bios defaults when it craps out, hardware monitoring and fan control all in the bios.

I just stay away from gigabyte. I see a lot of complaints/problems in the forums about them.

How are you outputting audio?

---

### Post by markbuntu on 2008-12-16
I am using the on board ACL888 and a C-Media 8768 PCI and a usb headest and they all work just fine. I don't own a tv so i have not tried the HDMI but from what i have read it should just work since the newer ati drivers now have HDMI support and the 3300 is also well supported. 

I have also noticed no one asking for help with this mobo or complaining about it here or in other forums and have seen some stellar reviews by people who have them which is a big reason I bought it. 

I am very happy with this board especially now that ati has multi-gpu support and hybrid crossfire in the linux driver. I just need to get some more monitors to try all that stuff out, and maybe a tv.

---

