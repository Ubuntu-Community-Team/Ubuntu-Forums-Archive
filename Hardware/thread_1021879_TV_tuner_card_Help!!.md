---
title: "TV tuner card Help!!"
date: 2008-12-26
forum: Hardware
---

### Post by sanjayd on 2008-12-26
i am using mercury ez view tv tuner card and i am using ubuntu 8.10. kindly help me with the software and also with the drivers!!
[click here for card details]("http://www.mercury-pc.com/product-detail.php?link=p-addcards&subtitle=Add-On%20Cards&productid=653")

---

### Post by cariboo on 2008-12-26
Just to be sure what chiset your Tv tuner card uses, could run in a Applications-->Accessories-->Terminal:

```
sudo lshw -C multimedia
```

and past the output in your next post, hopefully the output will be something like this:

```
sudo lshw -C multimedia
[sudo] password for jim: 
  *-multimedia            
       description: Multimedia controller
       product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 7
       bus info: pci@0000:04:07.0
       version: d0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=64 maxlatency=40 mingnt=16 module=saa7134
```

Jim

---

### Post by hnprashanth on 2008-12-26
Hey,
I have the same problem.
Here is the output when I run the command you have given

```
  *-multimedia            
       description: Multimedia controller
       product: SAA7130 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=64 maxlatency=38 mingnt=15 module=saa7134
  *-multimedia
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

```

Please help me configuring it. I have installed TV Time application & is blank now.

---

### Post by sanjayd on 2008-12-26
[HTML] *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: 5
       bus info: pci@0000:06:05.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20 module=cx8800
[/HTML]

---

### Post by sanjayd on 2008-12-26
[HTML] *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: 5
       bus info: pci@0000:06:05.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20 module=cx8800
[/HTML]

---

### Post by hnprashanth on 2008-12-26
Finally I got my TV Tuner card (Philips SAA 7130) working :)
I referred to a guide over here [http://mann-linuxproject.blogspot.com/2007/06/problem3.html]("http://mann-linuxproject.blogspot.com/2007/06/problem3.html")

Though it's basically for Fedora, but still works for Ubuntu. One thing which is changed in new version (8.10) of Ubuntu is path of modprobe.conf from /etc/modprobe.conf to /etc/modprobe.d/options. Open it using 
```
sudo gedit /etc/modprobe.d/options
```
and append appropriate card & tuner numbers, in my case it is:
```
options saa7134 card=3 tuner=37
```
Restart coputer for changes to take effect. Now use any TV Tuner application like TV Time, Xaw Tv or Myth TV & scan all the channels.

---

### Post by sanjayd on 2008-12-28
where to find tuner number!!

---

### Post by hnprashanth on 2008-12-28
I am not sure on how to find the correct numbers. If your card uses Philips SAA713x chipset (find that out using command dmesg), you can refer to following list. 
>  0 -> UNKNOWN/GENERIC
 1 -> Proteus Pro [philips reference design]   [1131:2001,1131:2001]
 2 -> LifeView FlyVIDEO3000                    [5168:0138,4e42:0138]
 3 -> LifeView/Typhoon FlyVIDEO2000            [5168:0138,4e42:0138]
 4 -> EMPRESS                                  [1131:6752]
 5 -> SKNet Monster TV                         [1131:4e85]
 6 -> Tevion MD 9717
 7 -> KNC One TV-Station RDS / Typhoon TV Tuner RDS [1131:fe01,1894:fe01]
 8 -> Terratec Cinergy 400 TV                  [153b:1142]
 9 -> Medion 5044
10 -> Kworld/KuroutoShikou SAA7130-TVPCI
11 -> Terratec Cinergy 600 TV                  [153b:1143]
12 -> Medion 7134                              [16be:0003]
13 -> Typhoon TV+Radio 90031
14 -> ELSA EX-VISION 300TV                     [1048:226b]
15 -> ELSA EX-VISION 500TV                     [1048:226a]
16 -> ASUS TV-FM 7134                          [1043:4842,1043:4830,1043:4840]
17 -> AOPEN VA1000 POWER                       [1131:7133]
18 -> BMK MPEX No Tuner
19 -> Compro VideoMate TV                      [185b:c100]
20 -> Matrox CronosPlus                        [102B:48d0]
21 -> 10MOONS PCI TV CAPTURE CARD              [1131:2001]
22 -> AverMedia M156 / Medion 2819             [1461:a70b]
23 -> BMK MPEX Tuner
24 -> KNC One TV-Station DVR                   [1894:a006]
25 -> ASUS TV-FM 7133                          [1043:4843]
26 -> Pinnacle PCTV Stereo (saa7134)           [11bd:002b]
27 -> Manli MuchTV M-TV002/Behold TV 403 FM
28 -> Manli MuchTV M-TV001/Behold TV 401
29 -> Nagase Sangyo TransGear 3000TV           [1461:050c]
30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card(PAL-BG,FM)  [1019:4cb4]
31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card (NTSC,FM) [1019:4cb5]
32 -> AVACS SmartTV
33 -> AVerMedia DVD EZMaker                    [1461:10ff]
34 -> Noval Prime TV 7133
35 -> AverMedia AverTV Studio 305              [1461:2115]
36 -> UPMOST PURPLE TV                         [12ab:0800]
37 -> Items MuchTV Plus / IT-005
38 -> Terratec Cinergy 200 TV                  [153b:1152]
39 -> LifeView FlyTV Platinum Mini             [5168:0212,4e42:0212]
40 -> Compro VideoMate TV PVR/FM               [185b:c100]
41 -> Compro VideoMate TV Gold+                [185b:c100]
42 -> Sabrent SBT-TVFM (saa7130)               [1131:7130 Subsystem 1131:0000]
43 -> :Zolid Xpert TV7134
44 -> Empire PCI TV-Radio LE
45 -> Avermedia AVerTV Studio 307              [1461:9715]
46 -> AVerMedia Cardbus TV/Radio (E500)        [1461:d6ee]
47 -> Terratec Cinergy 400 mobile              [153b:1162]
48 -> Terratec Cinergy 600 TV MK3              [153b:1158]
49 -> Compro VideoMate Gold+ Pal               [185b:c200]
50 -> Pinnacle PCTV 300i DVB-T + PAL           [11bd:002d]
51 -> ProVideo PV952                           [1540:9524]
52 -> AverMedia AverTV/305                     [1461:2108]
53 -> ASUS TV-FM 7135                          [1043:4845]
54 -> LifeView FlyTV Platinum FM / Gold        [5168:0214,1489:0214,5168:0304]
55 -> LifeView FlyDVB-T DUO                    [5168:0306]
56 -> Avermedia AVerTV 307                     [1461:a70a]
57 -> Avermedia AVerTV GO 007 FM               [1461:f31f]
58 -> ADS Tech Instant TV (saa7135)            [1421:0350,1421:0351,1421:0370,1421:1370]
59 -> Kworld/Tevion V-Stream Xpert TV PVR7134
60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Cardbus [5168:0502,4e42:0502,1489:0502]
61 -> Philips TOUGH DVB-T reference design     [1131:2004]
62 -> Compro VideoMate TV Gold+II
63 -> Kworld Xpert TV PVR7134
64 -> FlyTV mini Asus Digimatrix               [1043:0210]
65 -> V-Stream Studio TV Terminator
66 -> Yuan TUN-900 (saa7135)
67 -> Beholder BeholdTV 409 FM                 [0000:4091]
68 -> GoTView 7135 PCI                         [5456:7135]
69 -> Philips EUROPA V3 reference design       [1131:2004]
70 -> Compro Videomate DVB-T300                [185b:c900]
71 -> Compro Videomate DVB-T200                [185b:c901]
72 -> RTD Embedded Technologies VFG7350        [1435:7350]
73 -> RTD Embedded Technologies VFG7330        [1435:7330]
74 -> LifeView FlyTV Platinum Mini2            [14c0:1212]
75 -> AVerMedia AVerTVHD MCE A180              [1461:1044]
76 -> SKNet MonsterTV Mobile                   [1131:4ee9]
77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     [11bd:002e]
78 -> ASUSTeK P7131 Dual                       [1043:4862,1043:4876]
79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO25 Rev:2B)
80 -> ASUS Digimatrix TV                       [1043:0210]
81 -> Philips Tiger reference design           [1131:2018]
82 -> MSI TV@Anywhere plus                     [1462:6231]
83 -> Terratec Cinergy 250 PCI TV              [153b:1160]
84 -> LifeView FlyDVB Trio                     [5168:0319]
85 -> AverTV DVB-T 777                         [1461:2c05,1461:2c05]
86 -> LifeView FlyDVB-T / Genius VideoWonder DVB-T [5168:0301,1489:0301]
87 -> ADS Instant TV Duo Cardbus PTV331        [0331:1421]
88 -> Tevion/KWorld DVB-T 220RF                [17de:7201]
89 -> ELSA EX-VISION 700TV                     [1048:226c]
90 -> Kworld ATSC110                           [17de:7350]
91 -> AVerMedia A169 B                         [1461:7360]
92 -> AVerMedia A169 B1                        [1461:6360]
93 -> Medion 7134 Bridge #2                    [16be:0005]
94 -> LifeView FlyDVB-T Hybrid Cardbus         [5168:3306,5168:3502]
95 -> LifeView FlyVIDEO3000 (NTSC)             [5169:0138]
96 -> Medion Md8800 Quadro                     [16be:0007,16be:0008]
97 -> LifeView FlyDVB-S /Acorp TV134DS         [5168:0300,4e42:0300]
98 -> Proteus Pro 2309                         [0919:2003]
99 -> AVerMedia TV Hybrid A16AR                [1461:2c00]
100 -> Asus Europa2 OEM                         [1043:4860]
101 -> Pinnacle PCTV 310i                       [11bd:002f]
102 -> Avermedia AVerTV Studio 507              [1461:9715]
103 -> Compro Videomate DVB-T200A
104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     [0070:6701]
105 -> Terratec Cinergy HT PCMCIA               [153b:1172]
106 -> Encore ENLTV                             [1131:2342,1131:2341,3016:2344]
107 -> Encore ENLTV-FM                          [1131:230f]
108 -> Terratec Cinergy HT PCI                  [153b:1175]
109 -> Philips Tiger - S Reference design
110 -> Avermedia M102                           [1461:f31e]
111 -> ASUS P7131 4871                          [1043:4871]
112 -> ASUSTeK P7131 Hybrid                     [1043:4876]
113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card (PAL,FM) [1019:4cb6]
114 -> KWorld DVB-T 210                         [17de:7250]
115 -> Sabrent PCMCIA TV-PCB05                  [0919:2003]
116 -> 10MOONS TM300 TV Card                    [1131:2304]
117 -> Avermedia Super 007                      [1461:f01d]
118 -> Beholder BeholdTV 401                    [0000:4016]
119 -> Beholder BeholdTV 403                    [0000:4036]
120 -> Beholder BeholdTV 403 FM                 [0000:4037]
121 -> Beholder BeholdTV 405                    [0000:4050]
122 -> Beholder BeholdTV 405 FM                 [0000:4051]
123 -> Beholder BeholdTV 407                    [0000:4070]
124 -> Beholder BeholdTV 407 FM                 [0000:4071]
125 -> Beholder BeholdTV 409                    [0000:4090]
126 -> Beholder BeholdTV 505 FM/RDS             [0000:5051,0000:505B,5ace:5050]
127 -> Beholder BeholdTV 507 FM/RDS / BeholdTV 509 FM [0000:5071,0000:507B,5ace:5070,5ace:5090]
128 -> Beholder BeholdTV Columbus TVFM          [0000:5201]
129 -> Beholder BeholdTV 607 / BeholdTV 609     [5ace:6070,5ace:6071,5ace:6072,5ace:6073,5ace:6090,5ace:6091,5ace:6092,5ace:6093]
130 -> Beholder BeholdTV M6 / BeholdTV M6 Extra [5ace:6190,5ace:6193,5ace:6191]
131 -> Twinhan Hybrid DTV-DVB 3056 PCI          [1822:0022]
132 -> Genius TVGO AM11MCE
133 -> NXP Snake DVB-S reference design
134 -> Medion/Creatix CTX953 Hybrid             [16be:0010]
135 -> MSI TV@nywhere A/D v1.1                  [1462:8625]
136 -> AVerMedia Cardbus TV/Radio (E506R)       [1461:f436]
137 -> AVerMedia Hybrid TV/Radio (A16D)         [1461:f936]
138 -> Avermedia M115                           [1461:a836]
139 -> Compro VideoMate T750                    [185b:c900]
140 -> Avermedia DVB-S Pro A700                 [1461:a7a1]
141 -> Avermedia DVB-S Hybrid+FM A700           [1461:a7a2]
142 -> Beholder BeholdTV H6                     [5ace:6290]

---

### Post by aditeman on 2009-02-20
Hi,
I am a newbie and have been trying to set up my AverTV Super 007 for about two days.
I have tried numerous things on numerous threads, though I don't actually understand what I'm doing...

Running  "sudo lshw -C multimedia" gave me:

 *-multimedia
       description: Multimedia controller
       product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 0
       bus info: pci@0000:04:00.0
       version: d1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=84 module=saa7134

I have tried many things - downloading the firmware, cloning from mercurial, changing /etc/modules
when i run dmesg, i don't have anything about AverMedia or Phillips. The relevant line (from what I understand) is:

[    8.784321] saa7133[0]: subsystem: 1461:f11d, board: UNKNOWN/GENERIC [card=0,autodetected]
[    8.784329] saa7133[0]: board init: gpio is 40000

Can anyone help me solve my problem?
Another few details:
1. I am hooked up to a satellite box in Israel (YES broadcast).
2. I would like to use MythTV or another PVR program.

Thanks
aditeman

---

### Post by roach33 on 2009-04-04
This thread seems to point me in the right direction, yet I am lost on the modprobe command (I'm new to linux, and limited in IT knowledge generally...)

can someone please help me through this process with more detailed command lines? 

output from lshw -C multimedia:

*-multimedia            
       description: Multimedia controller
       product: SAA7130 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=32 maxlatency=40 mingnt=16 module=saa7134

and from lspci -v:

02:02.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
	Subsystem: Animation Technologies Inc. LifeView FlyVIDEO2000
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at ff1efc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

Where to from here?

---

### Post by sikander3786 on 2009-04-07
Try these simple steps.

go to terminal and type

sudo modprobe -vr saa7134_dvb
sudo modprobe -vr saa7134_alsa
sudo modprobe -vr saa7134
sudo modprobe -v saa7134 card=21

this is how i got many of my cards working. Might be this helps you.
Sorry if you have already tried this.

---

### Post by skotos on 2009-05-14
Bumping to understand the current state of art after the Jaunty upgrade.
Here below, my fresh info. Any idea on where to go?

*uname -a*```
Linux mypcname 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
```*lshw -C multimedia*[php]  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Multimedia controller
       product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 4
       bus info: pci@0000:09:04.0
       version: d1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=64 module=saa7134
[/php]*lsmod | grep -i saa*[php]saa7134_alsa           22176  0 
snd_pcm                99336  3 saa7134_alsa,snd_hda_intel,snd_pcm_oss
saa7134               176732  1 saa7134_alsa
ir_common              56068  1 saa7134
snd                    78792  16 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
compat_ioctl32         18304  2 saa7134,uvcvideo
v4l2_common            23296  2 tuner,saa7134
videobuf_dma_sg        22660  2 saa7134_alsa,saa7134
videobuf_core          29828  2 saa7134,videobuf_dma_sg
videodev               45184  4 tuner,saa7134,uvcvideo,compat_ioctl32
tveeprom               23428  1 saa7134
[/php]*lsmod | grep -i tuner*[php]tuner_xc2028           30000  1 
tuner                  36036  0 
v4l2_common            23296  2 tuner,saa7134
videodev               45184  4 tuner,saa7134,uvcvideo,compat_ioctl32
[/php]*sudo modinfo saa7134*[php]filename:       /lib/modules/2.6.28-11-generic/kernel/drivers/media/video/saa7134/saa7134.ko
license:        GPL
author:         Gerd Knorr <kraxel@bytesex.org> [SuSE Labs]
description:    v4l2 driver module for saa7130/34 based TV cards
srcversion:     B761198587B8BEDD5203AB8
alias:          pci:v00001131d00007135sv*sd*bc*sc*i*
alias:          pci:v00001131d00007134sv*sd*bc*sc*i*
alias:          pci:v00001131d00007133sv*sd*bc*sc*i*
alias:          pci:v00001131d00007130sv*sd*bc*sc*i*
alias:          pci:v00001131d00007130sv00001131sd00000000bc*sc*i*
alias:          pci:v00001131d00007134sv00001131sd00000000bc*sc*i*
alias:          pci:v00001131d00007133sv00001043sd00004878bc*sc*i*
alias:          pci:v00001131d00007133sv00001461sd0000F636bc*sc*i*
alias:          pci:v00001131d00007133sv00005ACEsd00006290bc*sc*i*
alias:          pci:v00001131d00007133sv00005169sd00001502bc*sc*i*
alias:          pci:v00001131d00007133sv00001421sd00000380bc*sc*i*
alias:          pci:v00001131d00007133sv0000185Bsd0000C900bc*sc*i*
alias:          pci:v00001131d00007133sv00001461sd0000A836bc*sc*i*
alias:          pci:v00001131d00007133sv00001461sd0000F936bc*sc*i*
alias:          pci:v00001131d00007133sv00001461sd0000F436bc*sc*i*
alias:          pci:v00001131d00007133sv00001462sd00008625bc*sc*i*
alias:          pci:v00001131d00007133sv000016BEsd00000010bc*sc*i*
alias:          pci:v00001131d00007133sv00001822sd00000022bc*sc*i*
alias:          pci:v00001131d00007133sv00004E42sd00003502bc*sc*i*
alias:          pci:v00001131d00007133sv00005ACEsd00006191bc*sc*i*
alias:          pci:v00001131d00007133sv00005ACEsd00006193bc*sc*i*
alias:          pci:v00001131d00007133sv00005ACEsd00006190bc*sc*i*
alias:          pci:v00001131d00007133sv00005ACEsd00006093bc*sc*i*
alias:          pci:v00001131d00007133sv00005ACEsd00006092bc*sc*i*
alias:          pci:v00001131d00007133sv00005ACEsd00006091bc*sc*i*
alias:          pci:v00001131d00007133sv00005ACEsd00006090bc*sc*i*
alias:          pci:v00001131d00007134sv00005ACEsd00006073bc*sc*i*
alias:          pci:v00001131d00007134sv00005ACEsd00006072bc*sc*i*
alias:          pci:v00001131d00007134sv00005ACEsd00006071bc*sc*i*
alias:          pci:v00001131d00007134sv00005ACEsd00006070bc*sc*i*
alias:          pci:v00001131d00007133sv00000000sd00005201bc*sc*i*
alias:          pci:v00001131d00007133sv00005ACEsd00005090bc*sc*i*
alias:          pci:v00001131d00007134sv00005ACEsd00005070bc*sc*i*
alias:          pci:v00001131d00007133sv00000000sd0000507Bbc*sc*i*
alias:          pci:v00001131d00007133sv00000000sd00005071bc*sc*i*
alias:          pci:v00001131d00007130sv00005ACEsd00005050bc*sc*i*
alias:          pci:v00001131d00007130sv00000000sd0000505Bbc*sc*i*
alias:          pci:v00001131d00007130sv00000000sd00005051bc*sc*i*
alias:          pci:v00001131d00007133sv00000000sd00004090bc*sc*i*
alias:          pci:v00001131d00007134sv00000000sd00004071bc*sc*i*
alias:          pci:v00001131d00007134sv00000000sd00004070bc*sc*i*
alias:          pci:v00001131d00007130sv00000000sd00004051bc*sc*i*
alias:          pci:v00001131d00007130sv00000000sd00004050bc*sc*i*
alias:          pci:v00001131d00007134sv00000000sd00004037bc*sc*i*
alias:          pci:v00001131d00007134sv00000000sd00004036bc*sc*i*
alias:          pci:v00001131d00007130sv00000000sd00004016bc*sc*i*
alias:          pci:v00001131d00007133sv00001461sd0000F01Dbc*sc*i*
alias:          pci:v00001131d00007130sv00001131sd00002304bc*sc*i*
alias:          pci:v00001131d00007134sv00000919sd00002003bc*sc*i*
alias:          pci:v00001131d00007133sv00001043sd00004857bc*sc*i*
alias:          pci:v00001131d00007133sv00001043sd00004871bc*sc*i*
alias:          pci:v00001131d00007133sv00004E42sd00000306bc*sc*i*
alias:          pci:v00001131d00007133sv00001461sd0000F31Ebc*sc*i*
alias:          pci:v00001131d00007133sv0000153Bsd00001175bc*sc*i*
alias:          pci:v00001131d00007130sv00001A7Fsd00002008bc*sc*i*
alias:          pci:v00001131d00007130sv00001131sd0000230Fbc*sc*i*
alias:          pci:v00001131d00007130sv00003016sd00002344bc*sc*i*
alias:          pci:v00001131d00007130sv00001131sd00002341bc*sc*i*
alias:          pci:v00001131d00007130sv00001131sd00002342bc*sc*i*
alias:          pci:v00001131d00007133sv0000153Bsd00001172bc*sc*i*
alias:          pci:v00001131d00007133sv00000070sd00006705bc*sc*i*
alias:          pci:v00001131d00007133sv00000070sd00006704bc*sc*i*
alias:          pci:v00001131d00007133sv00000070sd00006703bc*sc*i*
alias:          pci:v00001131d00007133sv00000070sd00006702bc*sc*i*
alias:          pci:v00001131d00007133sv00000070sd00006701bc*sc*i*
alias:          pci:v00001131d00007133sv00000070sd00006700bc*sc*i*
alias:          pci:v00001131d00007133sv00001043sd00004876bc*sc*i*
alias:          pci:v00001131d00007133sv00001461sd00009715bc*sc*i*
alias:          pci:v00001131d00007133sv000011BDsd0000002Fbc*sc*i*
alias:          pci:v00001131d00007134sv00001043sd00004860bc*sc*i*
alias:          pci:v00001131d00007134sv00001461sd00002C00bc*sc*i*
alias:          pci:v00001131d00007130sv00000919sd00002003bc*sc*i*
alias:          pci:v00001131d00007133sv00001489sd00000502bc*sc*i*
alias:          pci:v00001131d00007133sv00001461sd00002C05bc*sc*i*
alias:          pci:v00001131d00007133sv000016BEsd0000000Dbc*sc*i*
alias:          pci:v00001131d00007133sv000016BEsd00000008bc*sc*i*
alias:          pci:v00001131d00007133sv000016BEsd00000007bc*sc*i*
alias:          pci:v00001131d00007133sv00005168sd00003307bc*sc*i*
alias:          pci:v00001131d00007133sv00005168sd00003502bc*sc*i*
alias:          pci:v00001131d00007133sv00005168sd00003306bc*sc*i*
alias:          pci:v00001131d00007133sv00005168sd00000304bc*sc*i*
alias:          pci:v00001131d00007134sv00001489sd00000301bc*sc*i*
alias:          pci:v00001131d00007134sv00004E42sd00000300bc*sc*i*
alias:          pci:v00001131d00007134sv00005168sd00000300bc*sc*i*
alias:          pci:v00001131d00007134sv000016BEsd00000005bc*sc*i*
alias:          pci:v00001131d00007134sv00001461sd00006360bc*sc*i*
alias:          pci:v00001131d00007134sv00001461sd00007360bc*sc*i*
alias:          pci:v00001131d00007133sv000017DEsd00007352bc*sc*i*
alias:          pci:v00001131d00007133sv000017DEsd00007350bc*sc*i*
alias:          pci:v00001131d00007133sv000017DEsd00007250bc*sc*i*
alias:          pci:v00001131d00007133sv000017DEsd00007201bc*sc*i*
alias:          pci:v00001131d00007133sv00000331sd00001421bc*sc*i*
alias:          pci:v00001131d00007134sv00005168sd00000301bc*sc*i*
alias:          pci:v00001131d00007134sv00001461sd00002C05bc*sc*i*
alias:          pci:v00001131d00007133sv00005168sd00000319bc*sc*i*
alias:          pci:v00001131d00007133sv0000153Bsd00001160bc*sc*i*
alias:          pci:v00001131d00007133sv00001462sd00008624bc*sc*i*
alias:          pci:v00001131d00007133sv00001462sd00006231bc*sc*i*
alias:          pci:v00001131d00007133sv00001131sd00002018bc*sc*i*
alias:          pci:v00001131d00007133sv00001043sd00004862bc*sc*i*
alias:          pci:v00001131d00007133sv000011BDsd0000002Ebc*sc*i*
alias:          pci:v00001131d00007133sv00001131sd00004EE9bc*sc*i*
alias:          pci:v00001131d00007133sv00001461sd00001044bc*sc*i*
alias:          pci:v00001131d00007133sv00001435sd00007330bc*sc*i*
alias:          pci:v00001131d00007133sv00001435sd00007350bc*sc*i*
alias:          pci:v00001131d00007130sv0000185Bsd0000C901bc*sc*i*
alias:          pci:v00001131d00007134sv0000185Bsd0000C900bc*sc*i*
alias:          pci:v00001131d00007134sv00001131sd00002004bc*sc*i*
alias:          pci:v00001131d00007133sv00005456sd00007135bc*sc*i*
alias:          pci:v00001131d00007133sv00000000sd00004091bc*sc*i*
alias:          pci:v00001131d00007134sv00001043sd00000210bc*sc*i*
alias:          pci:v00001131d00007133sv00001043sd00000210bc*sc*i*
alias:          pci:v00001131d00007133sv00004E42sd00000502bc*sc*i*
alias:          pci:v00001131d00007133sv00001421sd00001370bc*sc*i*
alias:          pci:v00001131d00007133sv00001421sd00000370bc*sc*i*
alias:          pci:v00001131d00007133sv00001421sd00000351bc*sc*i*
alias:          pci:v00001131d00007133sv00001421sd00000350bc*sc*i*
alias:          pci:v00001131d00007130sv00001131sd00002004bc*sc*i*
alias:          pci:v00001131d00007133sv00001461sd0000F11Dbc*sc*i*
alias:          pci:v00001131d00007133sv00001461sd0000F31Fbc*sc*i*
alias:          pci:v00001131d00007133sv00005168sd00000306bc*sc*i*
alias:          pci:v00001131d00007133sv00005168sd00000502bc*sc*i*
alias:          pci:v00001131d00007134sv00001540sd00009524bc*sc*i*
alias:          pci:v00001131d00007134sv0000185Bsd0000C200bc*sc*i*
alias:          pci:v00001131d00007134sv00001461sd0000A70Abc*sc*i*
alias:          pci:v00001131d00007134sv00001461sd00009715bc*sc*i*
alias:          pci:v00001131d00007130sv0000185Bsd0000C100bc*sc*i*
alias:          pci:v00001131d00007130sv0000153Bsd00001152bc*sc*i*
alias:          pci:v00001131d00007133sv000012ABsd00000800bc*sc*i*
alias:          pci:v00001131d00007134sv00001019sd00004CB6bc*sc*i*
alias:          pci:v00001131d00007133sv00001019sd00004CB5bc*sc*i*
alias:          pci:v00001131d00007134sv00001019sd00004CB4bc*sc*i*
alias:          pci:v00001131d00007134sv000011BDsd0000002Dbc*sc*i*
alias:          pci:v00001131d00007134sv000011BDsd0000002Bbc*sc*i*
alias:          pci:v00001131d00007130sv00001461sd0000050Cbc*sc*i*
alias:          pci:v00001131d00007134sv00001461sd0000D6EEbc*sc*i*
alias:          pci:v00001131d00007130sv00001461sd000010FFbc*sc*i*
alias:          pci:v00001131d00007130sv00001461sd00002108bc*sc*i*
alias:          pci:v00001131d00007130sv00001461sd00002115bc*sc*i*
alias:          pci:v00001131d00007133sv00001461sd0000A7A2bc*sc*i*
alias:          pci:v00001131d00007133sv00001461sd0000A7A1bc*sc*i*
alias:          pci:v00001131d00007134sv00001461sd0000A70Bbc*sc*i*
alias:          pci:v00001131d00007130sv0000102Bsd000048D0bc*sc*i*
alias:          pci:v00001131d00007133sv0000185Bsd0000C100bc*sc*i*
alias:          pci:v00001131d00007133sv0000185Bsd0000C100bc*sc*i*
alias:          pci:v00001131d00007130sv00001131sd00002001bc*sc*i*
alias:          pci:v00001131d00007134sv00001131sd00007133bc*sc*i*
alias:          pci:v00001131d00007134sv00001894sd0000A006bc*sc*i*
alias:          pci:v00001131d00007134sv00001894sd0000FE01bc*sc*i*
alias:          pci:v00001131d00007134sv00001131sd0000FE01bc*sc*i*
alias:          pci:v00001131d00007134sv00001043sd00004840bc*sc*i*
alias:          pci:v00001131d00007133sv00001043sd00004843bc*sc*i*
alias:          pci:v00001131d00007134sv00001043sd00004830bc*sc*i*
alias:          pci:v00001131d00007133sv00001043sd00004845bc*sc*i*
alias:          pci:v00001131d00007134sv00001043sd00004842bc*sc*i*
alias:          pci:v00001131d00007130sv00001048sd0000226Cbc*sc*i*
alias:          pci:v00001131d00007130sv00001048sd0000226Abc*sc*i*
alias:          pci:v00001131d00007130sv00001048sd0000226Bbc*sc*i*
alias:          pci:v00001131d00007134sv000016BEsd00000003bc*sc*i*
alias:          pci:v00001131d00007133sv00001489sd00000214bc*sc*i*
alias:          pci:v00001131d00007133sv00005168sd00005214bc*sc*i*
alias:          pci:v00001131d00007133sv00005168sd00000214bc*sc*i*
alias:          pci:v00001131d00007133sv00004E42sd00000212bc*sc*i*
alias:          pci:v00001131d00007133sv000014C0sd00001212bc*sc*i*
alias:          pci:v00001131d00007133sv00005168sd00000212bc*sc*i*
alias:          pci:v00001131d00007130sv00004E42sd00000138bc*sc*i*
alias:          pci:v00001131d00007130sv00005168sd00000138bc*sc*i*
alias:          pci:v00001131d00007134sv00004E42sd00000138bc*sc*i*
alias:          pci:v00001131d00007134sv00005168sd00000138bc*sc*i*
alias:          pci:v00001131d00007134sv00005169sd00000138bc*sc*i*
alias:          pci:v00001131d00007133sv0000153Bsd00001162bc*sc*i*
alias:          pci:v00001131d00007134sv0000153Bsd00001158bc*sc*i*
alias:          pci:v00001131d00007134sv0000153Bsd00001143bc*sc*i*
alias:          pci:v00001131d00007134sv0000153Bsd00001142bc*sc*i*
alias:          pci:v00001131d00007134sv00001131sd00004E85bc*sc*i*
alias:          pci:v00001131d00007134sv00001131sd00006752bc*sc*i*
alias:          pci:v00001131d00007133sv00001131sd00002001bc*sc*i*
alias:          pci:v00001131d00007134sv00001131sd00002001bc*sc*i*
depends:        videobuf-core,videobuf-dma-sg,ir-common,videodev,tveeprom,v4l2-common,compat_ioctl32
vermagic:       2.6.28-11-generic SMP mod_unload modversions 
parm:           disable_ir:disable infrared remote support (int)
parm:           ir_debug:enable debug messages [IR] (int)
parm:           pinnacle_remote:Specify Pinnacle PCTV remote: 0=coloured, 1=grey (defaults to 0) (int)
parm:           ir_rc5_remote_gap:int
parm:           ir_rc5_key_timeout:int
parm:           repeat_delay:delay before key repeat started (int)
parm:           repeat_period:repeat period between keypresses when key is down (int)
parm:           disable_other_ir:disable full codes of alternative remotes from other manufacturers (int)
parm:           video_debug:enable debug messages [video] (int)
parm:           gbuffers:number of capture buffers, range 2-32 (int)
parm:           noninterlaced:capture non interlaced video (int)
parm:           secam:force SECAM variant, either DK,L or Lc (string)
parm:           vbi_debug:enable debug messages [vbi] (int)
parm:           vbibufs:number of vbi buffers, range 2-32 (int)
parm:           audio_debug:enable debug messages [tv audio] (int)
parm:           audio_ddep:audio ddep overwrite (int)
parm:           audio_clock_override:int
parm:           audio_clock_tweak:Audio clock tick fine tuning for cards with audio crystal that's slightly off (range [-1024 .. 1024]) (int)
parm:           ts_debug:enable debug messages [ts] (int)
parm:           tsbufs:number of ts buffers, range 2-32 (int)
parm:           ts_nr_packets:size of a ts buffers (in ts packets) (int)
parm:           i2c_debug:enable debug messages [i2c] (int)
parm:           i2c_scan:scan i2c bus at insmod time (int)
parm:           irq_debug:enable debug messages [IRQ handler] (int)
parm:           core_debug:enable debug messages [core] (int)
parm:           gpio_tracking:enable debug messages [gpio] (int)
parm:           alsa:enable ALSA DMA sound [dmasound] (int)
parm:           oss:enable OSS DMA sound [dmasound] (int)
parm:           latency:pci latency timer (int)
parm:           no_overlay:allow override overlay default (0 disables, 1 enables) [some VIA/SIS chipsets are known to have problem with overlay] (int)
parm:           video_nr:video device number (array of int)
parm:           vbi_nr:vbi device number (array of int)
parm:           radio_nr:radio device number (array of int)
parm:           tuner:tuner type (array of int)
parm:           card:card type (array of int)
[/php]*sudo modinfo tuner_xc2028*[php]filename:       /lib/modules/2.6.28-11-generic/kernel/drivers/media/common/tuners/tuner-xc2028.ko
license:        GPL
author:         Mauro Carvalho Chehab <mchehab@infradead.org>
author:         Michel Ludwig <michel.ludwig@gmail.com>
description:    Xceive xc2028/xc3028 tuner driver
srcversion:     8A712231913D7536A9238B2
depends:        
vermagic:       2.6.28-11-generic SMP mod_unload modversions 
parm:           debug:enable verbose debug messages (int)
parm:           audio_std:Audio standard. XC3028 audio decoder explicitly needs to know what audio
standard is needed for some video standards with audio A2 or NICAM.
The valid values are:
A2
A2/A
A2/B
NICAM
NICAM/A
NICAM/B
 (string)
parm:           firmware_name:Firmware file name. Allows overriding the default firmware name
 (string)
[/php]*lsmod | grep -i lirc* (the following refers to a certainly wrong configuration)[php]lirc_mceusb            18080  0 
lirc_mceusb2           21636  0 
lirc_dev               22088  2 lirc_mceusb,lirc_mceusb2[/php]FYI
- for further info there is also [this old thread]("http://ubuntuforums.org/showthread.php?t=397164")
- my laptop is an Acer Aspire 9815WKMi

PS
To check [a further but elder and detailed info page]("http://samuel.benoit.online.fr/en/kubuntu-hardy-heron-8-04-lts-linux-acer-aspire-9814-wkmi-9800-series-edgy-feisty-gutsy")

---

### Post by emal011 on 2009-06-22
and in my case?

Where find the codes?

```
*-multimedia:0 UNCLAIMED
       description: Multimedia controller
       product: Royal TS Function 1
       vendor: Pinnacle Systems Inc.
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=128 maxlatency=16 mingnt=2
  *-multimedia:1 UNCLAIMED
       description: Multimedia controller
       product: Royal TS Function 3
       vendor: Pinnacle Systems Inc.
       physical id: a.2
       bus info: pci@0000:01:0a.2
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=128 maxlatency=16 mingnt=2
```

I use the Pinnacle Sat Pro Pci, and i can't makeit work. No driver, no soft...

---

### Post by niyaz_ on 2010-03-06
*-multimedia            
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20
       resources: irq:22 memory:fd000000-fdffffff
  *-multimedia
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:17 memory:febff800-febff9ff memory:febff400-febff4ff


these r my configurations,,,,hw cn i run ma tv on ubuntu...plz help

---

