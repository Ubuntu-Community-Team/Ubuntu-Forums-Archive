---
title: "i need help with this tv tuner card"
date: 2015-12-20
forum: Hardware
---

### Post by braveheart-egy on 2015-12-20
Hello:
This is my first issue to your helpful forum and i'd like to be helped please. I have a TV tuner card  and i can't make it work with Ubuntu 14.0.4 i tried all available solutions posted over the internet and all didn't work can anybody help me????
my TV tuner is Philips semiconductor saa7130 video broadcast decoder (rev01)

---

### Post by deadflowr on 2015-12-20
We'll probably need more info as the Phillips semiconductor saa7130 is rather a generic description.
Perhaps dmesg can help narrow it down some.
In a terminal try something like this
```
dmesg | grep saa713
```
and post the output.

---

### Post by braveheart-egy on 2015-12-21
> **deadflowr said:**
> We'll probably need more info as the Phillips semiconductor saa7130 is rather a generic description.
Perhaps dmesg can help narrow it down some.
In a terminal try something like this
```
dmesg | grep saa713
```
and post the output.

Thank you for your answer
after i tried ```
dmesg | grep saa713
```
i have got that
```
[   13.899107] saa7130/34: v4l2 driver version 0, 2, 17 loaded
[   13.899263] saa7130[0]: found at 0000:02:01.0, rev: 1, irq: 19, latency: 64, mmio: 0xe3001000
[   13.899269] saa7134: Board is currently unknown. You might try to use the card=<nr>
[   13.899269] saa7134: insmod option to specify which board do you have, but this is
[   13.899269] saa7134: somewhat risky, as might damage your card. It is better to ask
[   13.899269] saa7134: for support at [EMAIL="linux-media@vger.kernel.org"]linux-media@vger.kernel.org[/EMAIL].
[   13.899269] saa7134: The supported cards are:
[   13.899273] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   13.899276] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   13.899279] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   13.899282] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   13.899285] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   13.899288] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   13.899290] saa7134:   card=6 -> Tevion MD 9717                          
[   13.899292] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   13.899295] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   13.899297] saa7134:   card=9 -> Medion 5044                             
[   13.899299] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   13.899301] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   13.899303] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   13.899306] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   13.899308] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   13.899310] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   13.899312] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   13.899315] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   13.899318] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   13.899320] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   13.899322] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   13.899324] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   13.899327] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   13.899329] saa7134:   card=23 -> BMK MPEX Tuner                          
[   13.899331] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   13.899333] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   13.899336] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   13.899338] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   13.899340] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   13.899342] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   13.899344] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   13.899347] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   13.899349] saa7134:   card=32 -> AVACS SmartTV                           
[   13.899351] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   13.899353] saa7134:   card=34 -> Noval Prime TV 7133                     
[   13.899355] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   13.899357] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   13.899360] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   13.899362] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   13.899364] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   13.899367] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   13.899369] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   13.899372] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   13.899374] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   13.899375] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   13.899377] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   13.899379] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   13.899382] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   13.899384] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   13.899387] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   13.899389] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   13.899391] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   13.899394] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   13.899396] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   13.899398] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   13.899402] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   13.899405] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   13.899408] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   13.899410] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   13.899414] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   13.899416] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   13.899419] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   13.899422] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   13.899423] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   13.899425] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   13.899428] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   13.899429] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   13.899431] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   13.899434] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   13.899436] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   13.899438] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   13.899441] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   13.899443] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   13.899445] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   13.899448] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   13.899450] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   13.899452] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   13.899455] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   13.899457] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   13.899459] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   13.899461] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   13.899464] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   13.899466] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   13.899469] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   13.899471] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   13.899473] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   13.899476] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   13.899479] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   13.899481] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   13.899483] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   13.899486] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   13.899489] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   13.899491] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   13.899493] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   13.899496] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   13.899499] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   13.899502] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   13.899505] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   13.899508] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   13.899510] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   13.899513] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   13.899515] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   13.899517] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   13.899519] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   13.899521] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   13.899526] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   13.899528] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   13.899532] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   13.899534] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   13.899536] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   13.899538] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   13.899540] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   13.899543] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   13.899545] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   13.899547] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   13.899550] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   13.899552] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   13.899555] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   13.899557] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   13.899559] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   13.899562] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   13.899564] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   13.899566] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   13.899569] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   13.899571] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   13.899573] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   13.899576] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   13.899578] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   13.899581] saa7134:   card=128 -> Beholder BeholdTV Columbus TV/FM         0000:5201
[   13.899584] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   13.899586] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   13.899589] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   13.899591] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   13.899593] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   13.899595] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   13.899597] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   13.899599] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   13.899602] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   13.899604] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   13.899606] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   13.899609] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   13.899611] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   13.899614] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   13.899616] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   13.899618] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   13.899620] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   13.899623] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   13.899625] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   13.899627] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   13.899630] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   13.899632] saa7134:   card=150 -> Zogis Real Angel 220                    
[   13.899634] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   13.899636] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   13.899639] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   13.899641] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   13.899643] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   13.899646] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   13.899649] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   13.899652] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   13.899654] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   13.899656] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   13.899659] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   13.899661] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   13.899664] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   13.899666] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   13.899668] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   13.899670] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   13.899673] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   13.899675] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   13.899677] saa7134:   card=169 -> Compro VideoMate S350/S300               185b:c900
[   13.899680] saa7134:   card=170 -> AverMedia AverTV Studio 505              1461:a115
[   13.899682] saa7134:   card=171 -> Beholder BeholdTV X7                     5ace:7595
[   13.899684] saa7134:   card=172 -> RoverMedia TV Link Pro FM                19d1:0138
[   13.899687] saa7134:   card=173 -> Zolid Hybrid TV Tuner PCI                1131:2004
[   13.899689] saa7134:   card=174 -> Asus Europa Hybrid OEM                   1043:4847
[   13.899691] saa7134:   card=175 -> Leadtek Winfast DTV1000S                 107d:6655
[   13.899693] saa7134:   card=176 -> Beholder BeholdTV 505 RDS                0000:5051
[   13.899696] saa7134:   card=177 -> Hawell HW-404M7                         
[   13.899697] saa7134:   card=178 -> Beholder BeholdTV H7                     5ace:7190
[   13.899700] saa7134:   card=179 -> Beholder BeholdTV A7                     5ace:7090
[   13.899702] saa7134:   card=180 -> Avermedia PCI M733A                      1461:4155 1461:4255
[   13.899705] saa7134:   card=181 -> TechoTrend TT-budget T-3000              13c2:2804
[   13.899707] saa7134:   card=182 -> Kworld PCI SBTVD/ISDB-T Full-Seg Hybrid  17de:b136
[   13.899710] saa7134:   card=183 -> Compro VideoMate Vista M1F               185b:c900
[   13.899712] saa7134:   card=184 -> Encore ENLTV-FM 3                        1a7f:2108
[   13.899714] saa7134:   card=185 -> MagicPro ProHDTV Pro2 DMB-TH/Hybrid      17de:d136
[   13.899717] saa7134:   card=186 -> Beholder BeholdTV 501                    5ace:5010
[   13.899719] saa7134:   card=187 -> Beholder BeholdTV 503 FM                 5ace:5030
[   13.899721] saa7134:   card=188 -> Sensoray 811/911                         6000:0811 6000:0911
[   13.899724] saa7134:   card=189 -> Kworld PC150-U                           17de:a134
[   13.899726] saa7134:   card=190 -> Asus My Cinema PS3-100                   1043:48cd
[   13.899729] saa7134:   card=191 -> Hawell HW-9004V1                        
[   13.899731] saa7134:   card=192 -> AverMedia AverTV Satellite Hybrid+FM A70 1461:2055
[   13.899733] saa7134:   card=193 -> WIS Voyager or compatible                1905:7007
[   13.899736] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   13.899758] saa7130[0]: board init: gpio is 804000
[   14.000303] saa7130[0]: Huh, no eeprom present (err=-5)?
[   14.000394] saa7130[0]: registered device video0 [v4l2]
[   14.000440] saa7130[0]: registered device vbi0
[   14.152582] saa7134 ALSA driver for DMA sound loaded
[   14.152587] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio
```

---

