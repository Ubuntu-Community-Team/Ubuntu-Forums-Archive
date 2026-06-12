---
title: "Sintonizadora TV Magician Station en Ubuntu 8.10, como hacerla funcionar?"
date: 2009-03-09
forum: Hardware
---

### Post by atari130xe on 2009-03-09
Hola gente, cuando compré las partes de mi nueva PC me regalaron una placa sintonizadora de TV Genérica que según el manual se llama TV MAGICIAN STATION, no logro configurarala para que funcione con Ubuntu 8.10, alguno que conozca o entienda bién si es posible hacerla funcionar podria darme una mano?

PD: en la lista de abajo no ubíco el nombre de esta placa, por ahí funciona con alguna similar, no lo sé

```
jose@josh:~$ dmesg | grep saa713
[   11.068087] saa7130/34: v4l2 driver version 0.2.14 loaded
[   11.068403] saa7134 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   11.068409] saa7130[0]: found at 0000:01:06.0, rev: 1, irq: 16, latency: 32, mmio: 0xfdffe000
[   11.068416] saa7134: <rant>
[   11.068417] saa7134:  Congratulations!  Your TV card vendor saved a few
[   11.068418] saa7134:  cents for a eeprom, thus your pci board has no
[   11.068419] saa7134:  subsystem ID and I can't identify it automatically
[   11.068420] saa7134: </rant>
[   11.068421] saa7134: I feel better now.  Ok, here are the good news:
[   11.068422] saa7134: You can use the card=<nr> insmod option to specify
[   11.068423] saa7134: which board do you have.  The list:
[   11.068427] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   11.068430] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   11.068435] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   11.068439] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   11.068443] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   11.068447] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   11.068450] saa7134:   card=6 -> Tevion MD 9717                          
[   11.068453] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   11.068458] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   11.068461] saa7134:   card=9 -> Medion 5044                             
[   11.068464] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   11.068467] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   11.068470] saa7134:   card=12 -> Medion 7134                              16be:0003
[   11.068474] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   11.068477] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   11.068480] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   11.068484] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   11.068489] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   11.068492] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   11.068495] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   11.068499] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   11.068502] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   11.068506] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   11.068509] saa7134:   card=23 -> BMK MPEX Tuner                          
[   11.068512] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   11.068516] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   11.068519] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   11.068523] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   11.068526] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   11.068529] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   11.068532] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   11.068536] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   11.068539] saa7134:   card=32 -> AVACS SmartTV                           
[   11.068542] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   11.068546] saa7134:   card=34 -> Noval Prime TV 7133                     
[   11.068548] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   11.068552] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   11.068555] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   11.068558] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   11.068562] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   11.068567] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   11.068570] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   11.068574] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   11.068577] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   11.068580] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   11.068582] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   11.068586] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   11.068589] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   11.068593] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   11.068596] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   11.068600] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   11.068604] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   11.068607] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   11.068610] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   11.068614] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   11.068619] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   11.068623] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   11.068627] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   11.068630] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   11.068636] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   11.068639] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   11.068643] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   11.068647] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   11.068650] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   11.068653] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   11.068656] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   11.068659] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   11.068662] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   11.068665] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   11.068669] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   11.068672] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   11.068676] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   11.068679] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   11.068683] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   11.068686] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   11.068690] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   11.068694] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   11.068697] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   11.068700] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862 1043:4857
[   11.068705] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   11.068708] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   11.068711] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   11.068715] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   11.068719] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   11.068722] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   11.068726] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   11.068730] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   11.068734] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   11.068738] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   11.068741] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   11.068745] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   11.068749] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   11.068752] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   11.068756] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   11.068759] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   11.068765] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   11.068768] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   11.068773] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   11.068777] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   11.068780] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   11.068784] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   11.068787] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   11.068791] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   11.068795] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   11.068797] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   11.068804] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   11.068807] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   11.068812] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   11.068816] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   11.068819] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   11.068829] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   11.068832] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   11.068836] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   11.068839] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   11.068843] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   11.068846] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   11.068850] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   11.068854] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   11.068857] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   11.068861] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   11.068864] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   11.068868] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   11.068871] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   11.068875] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   11.068878] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   11.068882] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   11.068885] saa7134:   card=126 -> Beholder BeholdTV 505 FM/RDS             0000:5051 0000:505b 5ace:5050
[   11.068890] saa7134:   card=127 -> Beholder BeholdTV 507 FM/RDS / BeholdTV  0000:5071 0000:507b 5ace:5070 5ace:5090
[   11.068896] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[   11.068899] saa7134:   card=129 -> Beholder BeholdTV 607 / BeholdTV 609     5ace:6070 5ace:6071 5ace:6072 5ace:6073 5ace:6090 5ace:6091 5ace:6092 5ace:6093
[   11.068907] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   11.068910] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   11.068914] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   11.068917] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   11.068920] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   11.068923] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   11.068927] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   11.068931] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   11.068934] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   11.068938] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   11.068941] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   11.068945] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   11.068948] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   11.068952] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   11.068955] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   11.068959] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636
[   11.068962] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   11.068966] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   11.068974] saa7130[0]: board init: gpio is 39100
[   11.172194] saa7130[0]: Huh, no eeprom present (err=-5)?
[   11.172321] saa7130[0]: registered device video0 [v4l2]
[   11.172361] saa7130[0]: registered device vbi0
[   11.804878] saa7134 ALSA driver for DMA sound loaded
[   11.804910] saa7130[0]/alsa: saa7130[0] at 0xfdffe000 irq 16 registered as card -2
jose@josh:~$ 


```

```
jose@josh:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
01:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
jose@josh:~$ 

```

```
jose@josh:~$ lsmod | grep saa
saa7134_alsa           20000  0 
snd_pcm                83204  3 saa7134_alsa,snd_usb_audio,snd_pcm_oss
snd                    63268  18 saa7134_alsa,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
saa7134               147284  1 saa7134_alsa
ir_common              48132  1 saa7134
videodev               41344  2 gspca_main,saa7134
compat_ioctl32          9344  1 saa7134
v4l2_common            19840  1 saa7134
videobuf_dma_sg        20612  2 saa7134_alsa,saa7134
videobuf_core          26628  2 saa7134,videobuf_dma_sg
tveeprom               20228  1 saa7134
i2c_core               31892  5 nvidia,saa7134,v4l2_common,tveeprom,i2c_nforce2
jose@josh:~$ 

```

```
ose@josh:~$ modprobe -l saa* 
/lib/modules/2.6.27-7-generic/kernel/drivers/media/common/saa7146_vv.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/common/saa7146.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa7111.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa717x.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa7185.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa6588.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa5249.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa7115.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa7127.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa7134/saa7134-empress.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa7134/saa6752hs.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa7134/saa7134.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa7134/saa7134-alsa.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa7134/saa7134-dvb.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa5246a.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa7110.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/saa7114.ko
jose@josh:~$ 

```

---

### Post by Hei Ku on 2009-03-09
Me parece que es esta:

Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

---

### Post by atari130xe on 2009-03-09
> **Hei Ku said:**
> Me parece que es esta:

Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

Gracias Hei Ku eso lo sé el tema es que no se bajo que nro de placa cargarla, o sea de la lista de arriba, aparecen muchas pero no la mía, por ahí como es generica podria andar alguna de esa lista.

---

### Post by Hei Ku on 2009-03-09
Creo que este caso es similar al tuyo:

[https://answers.launchpad.net/ubuntu/+question/48158](https://answers.launchpad.net/ubuntu/+question/48158)

---

### Post by faktorqm on 2009-03-09
No se la solucion, pero esto me hizo caer de la silla de la risa

```

[   11.068416] saa7134: <rant>
[   11.068417] saa7134:  Congratulations!  Your TV card vendor saved a few
[   11.068418] saa7134:  cents for a eeprom, thus your pci board has no
[   11.068419] saa7134:  subsystem ID and I can't identify it automatically
[   11.068420] saa7134: </rant>

```

jajajajajaj 

Como este es un foro en castellano, dejo la traduccion:

rant significa algo asi como hablar vulgarmente, o hablar en tono violento, la traduccion correcta creo yo seria bardeada.

```

<bardeada>
Felicitaciones! El fabricante de tu placa de TV ahorro unos pocos centavos en no poner una eeprom, entonces tu placa pci no tiene el identificador de subsistema y yo no la puedo identificar automaticamente.
</bardeada>

```

Salu2!

---

### Post by josecuervo86 on 2009-03-09
Jajaja, de una, bardeo mal.

---

### Post by atari130xe on 2009-03-09
Jejeje si ya me había reido del humor fino del flaco :p, vamos bién, al menos colocando card=42 ya tengo "nieve" en la ventana de TVtime, pero no puedo pegarla con el Tuner para Argentina, pruebo con diferentes y siempre me sale:

```
jose@josh:~$ tvtime-scanner
Leyendo la configuración de /etc/tvtime/tvtime.xml
Leyendo la configuración de /home/jose/.tvtime/tvtime.xml
Escaneando usando la norma de TV PAL-N.
videoinput: Driver refuses to set norm: Argumento inválido
videoinput: Driver refuses to set norm: Argumento inválido

    Sintonizador no encontrado en entrada 0.  Si dispones de
    alguno, selecciona otro diferente usando --input=<num>.

jose@josh:~$ 

```

Lo que encuentro en Google se refiere a España, Chile (NTSC) o USA... :confused:

---

### Post by faktorqm on 2009-03-09
leiste esto? [http://linux.die.net/man/1/tvtime-scanner](http://linux.die.net/man/1/tvtime-scanner)

yo le pondria algo asi:

```
tvtime-scanner --device=/dev/video0 --norm=PAL-N --input=0 
```

A ver que onda. El input por ejemplo (segun lo que dice la pagina man que te pase) si es 0 es la sintonizadora, si es 1 es la entrada de super video, si es 2 en la entrada de banda base (RCA), y asi es distinto en cada placa, asi que proba todas las combinaciones posibles hasta saber que onda. Tambien no te olvides de especificarle que dispositivo es, por ejemplo yo en casa tengo webcam y esa es /dev/video0, y la capturadora es /dev/video1.

Contame como te fue saludos.

---

