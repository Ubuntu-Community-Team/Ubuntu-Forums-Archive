---
title: "Video Capture Device. How to set up and use?"
date: 2015-01-08
forum: Hardware
---

### Post by madbrozzer2 on 2015-01-08
Please help.
There is one video capture device in my computer: KWORLD PCI Analog TV Card II Lite.
Aim: capture video stream from VHS.

And now I have no idea how to set it up.
I've found some information in Internet, but either it too complicated or not helping for my case.
Some information:

**$ lspci -vnn**

```
05:00.0 Multimedia controller [0480]: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder [1131:7134] (rev 01)
    Subsystem: KWorld Computer Co. Ltd. Device [17de:714c]
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at f7200000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
```


**$ dmesg | grep -i saa713**

```
[    7.822444] saa7130/34: v4l2 driver version 0, 2, 17 loaded
[    7.822587] saa7134[0]: found at 0000:05:00.0, rev: 1, irq: 19, latency: 32, mmio: 0xf7200000
[    7.822592] saa7134: <rant>
[    7.822592] saa7134:  Congratulations!  Your TV card vendor saved a few
[    7.822592] saa7134:  cents for a eeprom, thus your pci board has no
[    7.822592] saa7134:  subsystem ID and I can't identify it automatically
[    7.822592] saa7134: </rant>
[    7.822592] saa7134: I feel better now.  Ok, here are the good news:
[    7.822592] saa7134: You can use the card=<nr> insmod option to specify
[    7.822592] saa7134: which board do you have.  The list:
[    7.822594] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[    7.822596] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[    7.822597] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[    7.822599] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[    7.822600] saa7134:   card=4 -> EMPRESS                                  1131:6752
[    7.822601] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[    7.822602] saa7134:   card=6 -> Tevion MD 9717                          
[    7.822603] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[    7.822604] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[    7.822605] saa7134:   card=9 -> Medion 5044                             
[    7.822606] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[    7.822607] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[    7.822608] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[    7.822609] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[    7.822610] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[    7.822611] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[    7.822612] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[    7.822614] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[    7.822615] saa7134:   card=18 -> BMK MPEX No Tuner                       
[    7.822615] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[    7.822617] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[    7.822618] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[    7.822619] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[    7.822620] saa7134:   card=23 -> BMK MPEX Tuner                          
[    7.822620] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[    7.822621] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[    7.822622] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[    7.822624] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[    7.822624] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[    7.822625] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[    7.822626] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[    7.822627] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[    7.822628] saa7134:   card=32 -> AVACS SmartTV                           
[    7.822629] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[    7.822630] saa7134:   card=34 -> Noval Prime TV 7133                     
[    7.822631] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[    7.822632] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[    7.822633] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[    7.822634] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[    7.822635] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[    7.822636] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[    7.822637] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[    7.822638] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[    7.822639] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[    7.822640] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[    7.822641] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[    7.822642] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[    7.822643] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[    7.822644] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[    7.822645] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[    7.822646] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[    7.822647] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[    7.822648] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[    7.822649] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[    7.822650] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[    7.822652] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[    7.822653] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[    7.822654] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[    7.822655] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[    7.822657] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[    7.822658] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[    7.822659] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[    7.822660] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[    7.822661] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[    7.822662] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[    7.822663] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[    7.822664] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[    7.822664] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[    7.822666] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[    7.822667] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[    7.822668] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[    7.822669] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[    7.822670] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[    7.822671] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[    7.822672] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[    7.822673] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[    7.822674] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[    7.822675] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[    7.822676] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[    7.822677] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[    7.822678] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[    7.822679] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[    7.822680] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[    7.822681] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[    7.822682] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[    7.822683] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[    7.822684] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[    7.822686] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[    7.822687] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[    7.822688] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[    7.822689] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[    7.822690] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[    7.822691] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[    7.822692] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[    7.822693] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[    7.822695] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[    7.822696] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[    7.822697] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[    7.822699] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[    7.822700] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[    7.822701] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[    7.822702] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[    7.822703] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[    7.822704] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[    7.822705] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[    7.822707] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[    7.822708] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[    7.822709] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[    7.822710] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[    7.822712] saa7134:   card=109 -> Philips Tiger - S Reference design      
[    7.822712] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[    7.822713] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[    7.822714] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[    7.822715] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[    7.822716] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[    7.822717] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[    7.822718] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[    7.822719] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[    7.822720] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[    7.822721] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[    7.822723] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[    7.822724] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[    7.822725] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[    7.822726] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[    7.822727] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[    7.822728] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[    7.822729] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[    7.822730] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[    7.822731] saa7134:   card=128 -> Beholder BeholdTV Columbus TV/FM         0000:5201
[    7.822732] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[    7.822733] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[    7.822734] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[    7.822735] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[    7.822736] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[    7.822737] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[    7.822738] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[    7.822739] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[    7.822740] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[    7.822741] saa7134:   card=138 -> Avermedia M115                           1461:a836
[    7.822742] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[    7.822743] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[    7.822744] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[    7.822745] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[    7.822746] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[    7.822747] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[    7.822748] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[    7.822749] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[    7.822750] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[    7.822751] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[    7.822752] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[    7.822753] saa7134:   card=150 -> Zogis Real Angel 220                    
[    7.822754] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[    7.822755] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[    7.822756] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[    7.822757] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[    7.822758] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[    7.822759] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[    7.822761] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[    7.822762] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[    7.822763] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[    7.822764] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[    7.822765] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[    7.822766] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[    7.822767] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[    7.822768] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[    7.822769] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[    7.822770] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[    7.822771] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[    7.822772] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[    7.822773] saa7134:   card=169 -> Compro VideoMate S350/S300               185b:c900
[    7.822774] saa7134:   card=170 -> AverMedia AverTV Studio 505              1461:a115
[    7.822775] saa7134:   card=171 -> Beholder BeholdTV X7                     5ace:7595
[    7.822776] saa7134:   card=172 -> RoverMedia TV Link Pro FM                19d1:0138
[    7.822777] saa7134:   card=173 -> Zolid Hybrid TV Tuner PCI                1131:2004
[    7.822778] saa7134:   card=174 -> Asus Europa Hybrid OEM                   1043:4847
[    7.822779] saa7134:   card=175 -> Leadtek Winfast DTV1000S                 107d:6655
[    7.822780] saa7134:   card=176 -> Beholder BeholdTV 505 RDS                0000:5051
[    7.822781] saa7134:   card=177 -> Hawell HW-404M7                         
[    7.822782] saa7134:   card=178 -> Beholder BeholdTV H7                     5ace:7190
[    7.822783] saa7134:   card=179 -> Beholder BeholdTV A7                     5ace:7090
[    7.822784] saa7134:   card=180 -> Avermedia PCI M733A                      1461:4155 1461:4255
[    7.822785] saa7134:   card=181 -> TechoTrend TT-budget T-3000              13c2:2804
[    7.822786] saa7134:   card=182 -> Kworld PCI SBTVD/ISDB-T Full-Seg Hybrid  17de:b136
[    7.822787] saa7134:   card=183 -> Compro VideoMate Vista M1F               185b:c900
[    7.822788] saa7134:   card=184 -> Encore ENLTV-FM 3                        1a7f:2108
[    7.822789] saa7134:   card=185 -> MagicPro ProHDTV Pro2 DMB-TH/Hybrid      17de:d136
[    7.822790] saa7134:   card=186 -> Beholder BeholdTV 501                    5ace:5010
[    7.822791] saa7134:   card=187 -> Beholder BeholdTV 503 FM                 5ace:5030
[    7.822792] saa7134:   card=188 -> Sensoray 811/911                         6000:0811 6000:0911
[    7.822793] saa7134:   card=189 -> Kworld PC150-U                           17de:a134
[    7.822795] saa7134:   card=190 -> Asus My Cinema PS3-100                   1043:48cd
[    7.822796] saa7134:   card=191 -> Hawell HW-9004V1                        
[    7.822796] saa7134:   card=192 -> AverMedia AverTV Satellite Hybrid+FM A70 1461:2055
[    7.822798] saa7134[0]: subsystem: 17de:714c, board: UNKNOWN/GENERIC [card=0,autodetected]
[    7.822810] saa7134[0]: board init: gpio is c00005
[    7.978073] saa7134[0]: i2c eeprom 00: de 17 4c 71 10 28 1c 00 43 43 a9 1c 55 d2 b2 92
[    7.978079] saa7134[0]: i2c eeprom 10: 00 ff e2 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[    7.978082] saa7134[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 1d ff ff ff ff
[    7.978086] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.978089] saa7134[0]: i2c eeprom 40: ff 08 00 c2 00 10 03 3a ff ff ff ff ff ff ff ff
[    7.978093] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.978096] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.978100] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.978104] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.978107] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.978111] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.978114] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.978118] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.978121] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.978125] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.978128] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.978253] saa7134[0]: registered device video0 [v4l2]
[    7.978278] saa7134[0]: registered device vbi0
[    7.979687] saa7134 ALSA driver for DMA sound loaded
[    7.979701] saa7134[0]/alsa: saa7134[0] at 0xf7200000 irq 19 registered as card -2
```

I've tried to play video via VLC: Media -> Open Capture Device... -> TV-Analog
MRL: v4l2:///dev/video0

But there was nothing to output: no picture, no sound, no errors. Just seconds count.

TV-Digital option I did not understand at all. Too much options and no clues on what to check. But in any case I've got an errors like this one:

Your input can't be opened:
VLC is unable to open the MRL 'dvb-c://frequency=0000:modulation=QAM:srate=0'. Check the log for details.

Please help and thanks in advance!

---

### Post by deadflowr on 2015-01-08
It seems your card isn't recognized.
Not unusual really, quite a few tv capture cards aren't supported on linux.
I have a kworld pci 150-u and support for it came initially with a patch around the 3.0 kernel ( I think) and it was integrated into the kernel around 3.4.
It had been on the market for a few years at that point.

I found this
[http://www.linuxtv.org/wiki/index.php/Kworld_PCI_Analog_TV_Card_Lite](http://www.linuxtv.org/wiki/index.php/Kworld_PCI_Analog_TV_Card_Lite)
but it seems to be a different card than yours.

The sad reality is that those able to write drivers/modules for these cards need to have access to them.

---

### Post by madbrozzer2 on 2015-01-11
Well... sad information is also an information...
I've already saw that article and tried to type this in termianl:
$sudo modprobe saa7134 card=63 tuner=43 
(the only thing I understood) before posting, and reboot system... but didn't understand whether it gave me something.
Device in that article looks like very similar, but with differences of course.
I wish there was another solution but dual boot...

Thank you for your reply.

---

### Post by Xelort on 2015-02-05
> **madbrozzer2 said:**
> Well... sad information is also an information...
I've already saw that article and tried to type this in termianl:
$sudo modprobe saa7134 card=63 tuner=43 
(the only thing I understood) before posting, and reboot system... but didn't understand whether it gave me something.
Device in that article looks like very similar, but with differences of course.
I wish there was another solution but dual boot...

Thank you for your reply.

Hi madbrozzer.

I'm installing this device right now (a "Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder", but from Encore, not KWORLD), and _**IT WORKS FINE**_ (ubuntu 14.04). 

Just plug in thew card, install "tvtime" for tv and "gnomeradio" for radio. 

There are some configs you gotta set up before everything works ok, but that should be all you need to install.

Things you need to know: 

1) My encore card said, even in its manuals, that in order for audio to work, you need to plu a cable from the card's audio output to the pc sound card line input. That is, a cable bridge. I'm working right now on some way of configure a loopback setup instead of this, but that should be enough for starters. Also, beware of enabling the line input, from alsamixer or ubuntu's sound controls. In alsamixer, the "m" keyboard key enables and disables a channel ;)

2) As it had no default setup files for my country (Argentina), tvtime told me to run tvtime-scanner once, in order to detect the channels frequency. Also, i had to guess (by trial and error) the country's signal format (some special form of PAL). You got to configure that according to your country's setup.

3) In this pc i had a few silly problems: speakers were not working... and i though it was a problem of the capture card :/.
Trying to solve this non-problem, i also changed modprobe configurations, that i don't know if were ultimately required or not.
What i did was this:

a) Created a "/etc/modprobe.d/saa7134.conf" file with this sole content: "options saa7134 i2c_scan=1"
b) I ran this other commands, and restarted my system:
sudo modprobe -vr saa7134_dvb
sudo modprobe -vr saa7134_alsa
sudo modprobe -vr saa7134
sudo modprobe -v saa7134 card=40


Hope it helps.

---

