---
title: "Intel HDA drivers not working"
date: 2011-08-13
forum: Hardware
---

### Post by surajrajpurohit on 2011-08-13
i'm using asus mother board which is having nvidia HDA audio. I found from nvidia website that hda intel drivers will work. 
the current drivers in my ubuntu is 

cat /proc/asound/card0/codec* | grep Codec
Codec: VIA VT1708S

i've followed the instructions from [https://help.ubuntu.com/community/HdaIntelSoundHowt](https://help.ubuntu.com/community/HdaIntelSoundHowt)

In sudo nano /etc/modprobe.d/alsa-base.conf

i've added 

options snd-hda-intel model=ALC880

sudo alsa force-reload

also got the model number from the link in [https://help.ubuntu.com/community/HdaIntelSoundHowt](https://help.ubuntu.com/community/HdaIntelSoundHowt)
...
and rebooted but its not working

i've alsodownloaded alsa-drivers-10 from alsa website
i've downloaded .tar.bz2 file
den i've unziped it and complied the drivers
but this is also not working
after reboot i again got the old kernel

---

### Post by BicyclerBoy on 2011-08-13
AFAIK
this is totally wrong
options snd-hda-intel model=ALC880

The modprobe module options are used as extra switches for oddball h/w not to set the soundcard model.

Also the modprobe options do not get applied immediately, you have to rebuild the boot image.

intel-HDA is a standard, The snd-hda-intel driver supports all of h/w conforming to the std. 

You can for immediate test:
[sudo] modprobe snd-hda-intel
check the output from:
dmesg

Is your mobo a laptop or std ATX ?
Exact model number would help someone..
What ubuntu release are you running ?

---

### Post by surajrajpurohit on 2011-08-14
thank q for reply...
well i'm new to Linux so don't know much about it..

"The modprobe module options are used as extra switches for oddball h/w not to set the soundcard model.

Also the modprobe options do not get applied immediately, you have to rebuild the boot image.

intel-HDA is a standard, The snd-hda-intel driver supports all of h/w conforming to the std"
 
the above lines are a bit difficult 4 me to understand...
but anyways for test as u said i enterd the commands

---

### Post by surajrajpurohit on 2011-08-14
root@bt:~#  modprobe snd-hda-intel
root@bt:~#dmesg
[  248.064442] --> EEPROMAddressNum = 8
[  248.064445] Initialize MAC Address from E2PROM 
[  248.064481] E2PROM MAC: =f0:7d:68:11:83:97
[  248.064484] Use the MAC address what is assigned from EEPROM. 
[  248.064492] Current MAC: =f0:7d:68:11:83:97
[  248.064955] E2PROM: Version = 0, FAE release #1
[  248.065053] NICReadEEPROMParameters: RxPath = 1, TxPath = 1
[  248.065055] Chip specific bbpRegTbSize=0!
[  248.065097] E2PROM: G Tssi[-4 .. +4] = 255 255 255 255 - 255 -255 255 255 255, step=255, tuning=0
[  248.065146] E2PROM: A Tssi[-4 .. +4] = 255 255 255 255 - 255 -255 255 255 255, step=255, tuning=0
[  248.065157] E2PROM: RF FreqOffset=0x3d 
[  248.065158] RTMPSetPhyMode : PhyMode=9, channel=0 
[  248.065160] country code=129/129, RFIC=8, PHY mode=9, support 13 channels
[  248.065161] BuildChannel # 1 :: Pwr0 = 28, Pwr1 =5, 
[  248.065162]  BuildChannel # 2 :: Pwr0 = 28, Pwr1 =5, 
[  248.065163]  BuildChannel # 3 :: Pwr0 = 27, Pwr1 =5, 
[  248.065165]  BuildChannel # 4 :: Pwr0 = 27, Pwr1 =5, 
[  248.065166]  BuildChannel # 5 :: Pwr0 = 27, Pwr1 =5, 
[  248.065167]  BuildChannel # 6 :: Pwr0 = 26, Pwr1 =5, 
[  248.065168]  BuildChannel # 7 :: Pwr0 = 26, Pwr1 =5, 
[  248.065169]  BuildChannel # 8 :: Pwr0 = 25, Pwr1 =5, 
[  248.065170]  BuildChannel # 9 :: Pwr0 = 24, Pwr1 =5, 
[  248.065172]  BuildChannel # 10 :: Pwr0 = 24, Pwr1 =5, 
[  248.065173]  BuildChannel # 11 :: Pwr0 = 23, Pwr1 =5, 
[  248.065174]  BuildChannel # 12 :: Pwr0 = 22, Pwr1 =5, 
[  248.065175]  BuildChannel # 13 :: Pwr0 = 21, Pwr1 =5, 
[  248.065176]  RTMPSetPhyMode: channel is out of range, use first channel=1 
[  248.065179] RTMPSetHT : HT_mode(0), ExtOffset(3), MCS(33), BW(1), STBC(0), SHORTGI(1)
[  248.065181] RTMPSetHT : RxBAWinLimit = 64
[  248.065182] RTMPSetHT : AMsduSize = 0, MimoPs = 3, MpduDensity = 4, MaxRAmpduFactor = 3
[  248.066195] EDCA [#0]: AIFSN CWmin CWmax  TXOP(us)  ACM
[  248.066197]      AC_BE       3      4      6         0     0
[  248.066198]      AC_BK       7      4     10         0     0
[  248.066200]      AC_VI       1      3      4      3008     0
[  248.066201]      AC_VO       1      2      3      1504     0
[  248.066202] RTMPSetIndividualHT : Desired MCS = 33
[  248.066204] MlmeUpdateHtTxRates===> 
[  248.066205]  MlmeUpdateHtTxRates<---.AMsduSize = 0  
[  248.066207] TX: MCS[0] = ff (choose 7), BW = 1, ShortGI = 1, MODE = 2,  
[  248.066208] MlmeUpdateHtTxRates<=== 
[  248.066311] Txpower per Rate
[  248.066322] Gpwrdelta = 0, Apwrdelta = 0 .
[  248.066343] 20MHz BW, 2.4G band-77776666,  Adata = 77776666,  Gdata = 77776666 
[  248.066364] 20MHz BW, 2.4G band-77776677,  Adata = 77776677,  Gdata = 77776677 
[  248.066385] 20MHz BW, 2.4G band-aaaa4477,  Adata = aaaa4477,  Gdata = aaaa4477 
[  248.066406] 20MHz BW, 2.4G band-aaaa6688,  Adata = aaaa6688,  Gdata = aaaa6688 
[  248.066425] 20MHz BW, 2.4G band-ffff6688,  Adata = ffff6688,  Gdata = ffff6688 
[  248.066426] <-- NICReadEEPROMParameters
[  248.066427] 3. Phy Mode = 9
[  248.066428] --> NICInitAsicFromEEPROM
[  248.080828] RTMPFilterCalibration - CaliBW20RfR24=0x7, CaliBW40RfR24=0x27
[  248.080846] RTMPSetLED::Mode=10,HighByte=0x20,LowByte=0x0a
[  248.080962] --> AsicCheckCommanOk CID = 0xff020001, CmdStatus= 0xff012101 
[  248.082282] --> AsicCheckCommanOk CID = 0xffffff03, CmdStatus= 0xffffff01 
[  248.084316] Use Hw Radio Control Pin=0; if used Pin=0;
[  248.086517] TxPath = 1, RxPath = 1, RFIC=8, Polar+LED mode=a
[  248.086518] <-- NICInitAsicFromEEPROM
[  248.086520] RTMPSetPhyMode : PhyMode=9, channel=1 
[  248.086522] country code=129/129, RFIC=8, PHY mode=9, support 13 channels
[  248.086524] BuildChannel # 1 :: Pwr0 = 28, Pwr1 =5, 
[  248.086524]  BuildChannel # 2 :: Pwr0 = 28, Pwr1 =5, 
[  248.086525]  BuildChannel # 3 :: Pwr0 = 27, Pwr1 =5, 
[  248.086527]  BuildChannel # 4 :: Pwr0 = 27, Pwr1 =5, 
[  248.086528]  BuildChannel # 5 :: Pwr0 = 27, Pwr1 =5, 
[  248.086529]  BuildChannel # 6 :: Pwr0 = 26, Pwr1 =5, 
[  248.086530]  BuildChannel # 7 :: Pwr0 = 26, Pwr1 =5, 
[  248.086531]  BuildChannel # 8 :: Pwr0 = 25, Pwr1 =5, 
[  248.086532]  BuildChannel # 9 :: Pwr0 = 24, Pwr1 =5, 
[  248.086534]  BuildChannel # 10 :: Pwr0 = 24, Pwr1 =5, 
[  248.086535]  BuildChannel # 11 :: Pwr0 = 23, Pwr1 =5, 
[  248.086536]  BuildChannel # 12 :: Pwr0 = 22, Pwr1 =5, 
[  248.086537]  BuildChannel # 13 :: Pwr0 = 21, Pwr1 =5, 
[  248.086538]  RTMPSetHT : HT_mode(0), ExtOffset(3), MCS(33), BW(1), STBC(0), SHORTGI(1)
[  248.086541] RTMPSetHT : RxBAWinLimit = 64
[  248.086543] RTMPSetHT : AMsduSize = 0, MimoPs = 3, MpduDensity = 4, MaxRAmpduFactor = 3
[  248.087555] EDCA [#0]: AIFSN CWmin CWmax  TXOP(us)  ACM
[  248.087557]      AC_BE       3      4      6         0     0
[  248.087558]      AC_BK       7      4     10         0     0
[  248.087559]      AC_VI       1      3      4      3008     0
[  248.087561]      AC_VO       1      2      3      1504     0
[  248.087562] RTMPSetIndividualHT : Desired MCS = 33
[  248.087564] MlmeUpdateHtTxRates===> 
[  248.087565]  MlmeUpdateHtTxRates<---.AMsduSize = 0  
[  248.087567] TX: MCS[0] = ff (choose 7), BW = 1, ShortGI = 1, MODE = 2,  
[  248.087568] MlmeUpdateHtTxRates<=== 
[  248.087569] MCS Set = ff 00 00 00 01
[  248.087570] NDIS_STATUS_MEDIA_DISCONNECT Event B!
[  248.087572] <==== rt28xx_init, Status=0
[  248.087575] ==> RTMPEnableRxTx
[  248.087628] <== WRITE DMA offset 0x208 = 0x65
[  248.087632] <== RTMPEnableRxTx
[  248.087634] 0x1300 = 00064300
[  248.087635] In InitHwCoex ...
[  248.087637] Driver auto reconnect to last OID_802_11_SSID setting - Virus Detected, len - 14
[  248.087662] CntlOidSsidProc():CNTL - 0 BSS of 0 BSS match the desire (14)SSID - Virus Detected
[  248.087664] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
[  248.087731] SCANNING, suspend MSDU transmission ...
[  248.090799] SYNC - BBP R4 to 20MHz.l
[  248.092901] RT35xx: SwitchChannel#1(RF=8, Pwr0=28, Pwr1=5, 1T), N=0xF1, K=0x02, R=0x02
[  248.149236] ===>Set_NetworkType_Proc::(INFRA)
[  248.149245] Set_NetworkType_Proc::(NetworkType=1)
[  248.234154] RT35xx: SwitchChannel#2(RF=8, Pwr0=28, Pwr1=5, 1T), N=0xF1, K=0x07, R=0x02
[  248.378159] RT35xx: SwitchChannel#3(RF=8, Pwr0=27, Pwr1=5, 1T), N=0xF2, K=0x02, R=0x02
[  248.522156] RT35xx: SwitchChannel#4(RF=8, Pwr0=27, Pwr1=5, 1T), N=0xF2, K=0x07, R=0x02
[  248.666314] RT35xx: SwitchChannel#5(RF=8, Pwr0=27, Pwr1=5, 1T), N=0xF3, K=0x02, R=0x02
[  248.810157] RT35xx: SwitchChannel#6(RF=8, Pwr0=26, Pwr1=5, 1T), N=0xF3, K=0x07, R=0x02
[  248.954157] RT35xx: SwitchChannel#7(RF=8, Pwr0=26, Pwr1=5, 1T), N=0xF4, K=0x02, R=0x02
[  249.098159] RT35xx: SwitchChannel#8(RF=8, Pwr0=25, Pwr1=5, 1T), N=0xF4, K=0x07, R=0x02
[  249.242156] RT35xx: SwitchChannel#9(RF=8, Pwr0=24, Pwr1=5, 1T), N=0xF5, K=0x02, R=0x02
[  249.386347] RT35xx: SwitchChannel#10(RF=8, Pwr0=24, Pwr1=5, 1T), N=0xF5, K=0x07, R=0x02
[  249.445399] ==>rt_ioctl_giwfreq  1
[  249.445436] ===>rt_ioctl_giwencode 0
[  249.445444] MediaState is not connected, ess
[  249.445451] ==>rt_ioctl_giwmode(mode=0)
[  249.445459] ===>rt_ioctl_giwrange
[  249.445482] rt28xx_get_wireless_stats --->
[  249.445487] <--- rt28xx_get_wireless_stats
[  249.530161] RT35xx: SwitchChannel#11(RF=8, Pwr0=23, Pwr1=5, 1T), N=0xF6, K=0x02, R=0x02
[  249.674362] RT35xx: SwitchChannel#12(RF=8, Pwr0=22, Pwr1=5, 1T), N=0xF6, K=0x07, R=0x02
[  249.818155] RT35xx: SwitchChannel#13(RF=8, Pwr0=21, Pwr1=5, 1T), N=0xF7, K=0x02, R=0x02
[  249.962185] RT35xx: SwitchChannel#1(RF=8, Pwr0=28, Pwr1=5, 1T), N=0xF1, K=0x02, R=0x02
[  249.964377] SYNC - End of SCAN, restore to channel 1, Total BSS[04]
[  249.964386] SCAN done, resume MSDU transmission ...
[  250.278377] ===> rt_ioctl_siwpmksa
[  250.278385] rt_ioctl_siwpmksa - IW_PMKSA_FLUSH
[  250.278394] ===>Set_NetworkType_Proc::(INFRA)
[  250.278399] Set_NetworkType_Proc::(NetworkType=1)
[  250.278435] ===>rt_ioctl_giwrange
[  250.304112] rt_ioctl_siwauth::IW_AUTH_WPA_ENABLED - Driver supports WPA!(param->value = 1)
[  250.304131] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
[  250.304137]          WCIDAttri = 0x1 
[  250.304141] AsicRemovePairwiseKeyEntry : Wcid #1 
[  250.304145] AsicRemoveSharedKeyEntry: #0 
[  250.304151] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
[  250.304157] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8401)
[  250.304167] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
[  250.304172]          WCIDAttri = 0x1 
[  250.304175] AsicRemovePairwiseKeyEntry : Wcid #1 
[  250.304179] AsicRemoveSharedKeyEntry: #1 
[  250.304184] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
[  250.304190] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8402)
[  250.304199] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
[  250.304203]          WCIDAttri = 0x1 
[  250.304207] AsicRemovePairwiseKeyEntry : Wcid #1 
[  250.304210] AsicRemoveSharedKeyEntry: #2 
[  250.304216] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
[  250.304221] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8403)
[  250.304229] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
[  250.304234]          WCIDAttri = 0x1 
[  250.304237] AsicRemovePairwiseKeyEntry : Wcid #1 
[  250.304241] AsicRemoveSharedKeyEntry: #3 
[  250.304246] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
[  250.304252] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8404)
[  250.304291] rt_ioctl_siwauth::IW_AUTH_DROP_UNENCRYPTED - param->value = 1!
[  250.304298] ===> rt_ioctl_siwpmksa
[  250.304302] rt_ioctl_siwpmksa - IW_PMKSA_FLUSH
[  250.313512] rt28xx_get_wireless_stats --->
[  250.313520] <--- rt28xx_get_wireless_stats
[  250.313648] Set_SSID_Proc::(Len=14,Ssid=Virus Detected)
[  250.313709] CntlOidSsidProc():CNTL - 1 BSS of 4 BSS match the desire (14)SSID - Virus Detected
[  250.313719] CNTL - iterate BSS 0 of 1
[  250.313725] SYNC - MlmeJoinReqAction(BSS #0)
[  250.314741] SYNC - BBP R4 to 20MHz.l
[  250.316863] RT35xx: SwitchChannel#11(RF=8, Pwr0=23, Pwr1=5, 1T), N=0xF6, K=0x02, R=0x02
[  250.319121] SYNC - Switch to ch 11, Wait BEACON from 00:1b:57:f0:78:d7
[  250.329323] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  250.332595] MlmeRestartStateMachine 
[  250.334702] RT35xx: SwitchChannel#11(RF=8, Pwr0=23, Pwr1=5, 1T), N=0xF6, K=0x02, R=0x02
[  250.336855] SCAN done, resume MSDU transmission ...
[  250.337909] !!! MLME busy, reset MLME state machine !!!
[  250.337913] IOCTL::SIOCSIWAP 00:1b:57:f0:78:d7
[  250.365122] CNTL - joining 00:1b:57:f0:78:d7 ...
[  250.365130] SYNC - MlmeJoinReqAction(BSS #0)
[  250.366141] SYNC - BBP R4 to 20MHz.l
[  250.368264] RT35xx: SwitchChannel#11(RF=8, Pwr0=23, Pwr1=5, 1T), N=0xF6, K=0x02, R=0x02
[  250.369065] SYNC - Switch to ch 11, Wait BEACON from 00:1b:57:f0:78:d7
[  250.400891] SYNC - receive desired BEACON at JoinWaitBeacon... Channel = 11
[  250.400899] MlmeAux.ExtCapInfo=0
[  250.400902] RTMPUpdateMlmeRate ==>   MlmeTransmit = 0x0  
[  250.400904] SYNC - after JOIN, SupRateLen=8, ExtRateLen=4
[  250.404007] RT35xx: SwitchChannel#11(RF=8, Pwr0=23, Pwr1=5, 1T), N=0xF6, K=0x02, R=0x02
[  250.404862] !!! 20MHz !!! 
[  250.404862] AUTH - Send AUTH request seq#1 (Alg=0)...
[  250.404862] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 462
[  250.404862] ===>Set_NetworkType_Proc::(INFRA)
[  250.404862] Set_NetworkType_Proc::(NetworkType=1)
[  250.404862] rt_ioctl_siwauth::IW_AUTH_80211_AUTH_ALG - param->value = 1!
[  250.404862] rt_ioctl_siwauth::IW_AUTH_DROP_UNENCRYPTED - param->value = 1!
[  250.404862] ===> rt_ioctl_siwgenie

---

### Post by surajrajpurohit on 2011-08-14
[  250.404862] rt_ioctl_siwauth::IW_AUTH_WPA_VERSION - param->value = 2!
[  250.404862] rt_ioctl_siwauth::IW_AUTH_CIPHER_PAIRWISE - param->value = 4!
[  250.404862] rt_ioctl_siwauth::IW_AUTH_CIPHER_GROUP - param->value = 4!
[  250.404862] rt_ioctl_siwauth::IW_AUTH_KEY_MGMT - param->value = 2!
[  250.404862] rt_ioctl_siwauth::IW_AUTH_PRIVACY_INVOKED - param->value = 1!
[  250.404862] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  250.404862] MlmeRestartStateMachine 
[  250.412634] RT35xx: SwitchChannel#1(RF=8, Pwr0=28, Pwr1=5, 1T), N=0xF1, K=0x02, R=0x02
[  250.414758] SCAN done, resume MSDU transmission ...
[  250.415806] !!! MLME busy, reset MLME state machine !!!
[  250.415809] Set_SSID_Proc::(Len=14,Ssid=Virus Detected)
[  250.415840] CntlOidSsidProc():CNTL - 1 BSS of 4 BSS match the desire (14)SSID - Virus Detected
[  250.415844] CNTL - iterate BSS 0 of 1
[  250.415846] SYNC - MlmeJoinReqAction(BSS #0)
[  250.416864] SYNC - BBP R4 to 20MHz.l
[  250.418975] RT35xx: SwitchChannel#11(RF=8, Pwr0=23, Pwr1=5, 1T), N=0xF6, K=0x02, R=0x02
[  250.421111] SYNC - Switch to ch 11, Wait BEACON from 00:1b:57:f0:78:d7
[  250.421141] MlmeRestartStateMachine 
[  250.423236] RT35xx: SwitchChannel#1(RF=8, Pwr0=28, Pwr1=5, 1T), N=0xF1, K=0x02, R=0x02
[  250.425369] SCAN done, resume MSDU transmission ...
[  250.426417] !!! MLME busy, reset MLME state machine !!!
[  250.426420] IOCTL::SIOCSIWAP 00:1b:57:f0:78:d7
[  250.659131] CNTL - joining 00:1b:57:f0:78:d7 ...
[  250.659141] SYNC - MlmeJoinReqAction(BSS #0)
[  250.660177] SYNC - BBP R4 to 20MHz.l
[  250.662290] RT35xx: SwitchChannel#11(RF=8, Pwr0=23, Pwr1=5, 1T), N=0xF6, K=0x02, R=0x02
[  250.664458] SYNC - Switch to ch 11, Wait BEACON from 00:1b:57:f0:78:d7
[  250.708096] SYNC - receive desired BEACON at JoinWaitBeacon... Channel = 11
[  250.708104] MlmeAux.ExtCapInfo=0
[  250.708107] RTMPUpdateMlmeRate ==>   MlmeTransmit = 0x0  
[  250.708110] SYNC - after JOIN, SupRateLen=8, ExtRateLen=4
[  250.711212] RT35xx: SwitchChannel#11(RF=8, Pwr0=23, Pwr1=5, 1T), N=0xF6, K=0x02, R=0x02
[  250.712067] !!! 20MHz !!! 
[  250.712067] AUTH - Send AUTH request seq#1 (Alg=0)...
[  250.718991] AUTH - Receive AUTH_RSP seq#2 to me (Alg=0, Status=0)
[  250.718997] CNTL - AUTH OK
[  250.719001] ASSOC - Send ASSOC request...
[  250.723199] PeerAssocRspAction():ASSOC - receive ASSOC_RSP to me (status=0)
[  250.723208] PeerAssocRspAction():MacTable [255].AMsduSize = 0. ClientStatusFlags = 0x0 
[  250.723218] AssocPostProc===>  AP.AMsduSize = 0. ClientStatusFlags = 0x0 
[  250.723223] AssocPostProc===>    (Mmps=0, AmsduSize=0, )
[  250.723228] AssocPostProc===> Store RSN_IE for WPA SM negotiation 
[  250.723235] RSN_IE: f937942b, len = 26
[  250.723239] 0x0000 : dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 
[  250.723257] 0x0010 : f2 02 01 00 00 50 f2 02 00 00 
[  250.723294] !!!Infra LINK UP !!! 
[  250.723300] !!! LINK UP !!! (BssType=1, AID=1, ssid=Virus Detected, Channel=11, CentralChannel = 11)
[  250.723306] !!! LINK UP !!! (Density =0, )
[  250.723312] ==============> AsicSetBssid 0:1b:57:f0:78:d7
[  250.723320] AsicSetEdcaParm
[  250.723342] RTMPWPARemoveAllKeys(AuthMode=4, WepStatus=4)
[  250.723349] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
[  250.723354]          WCIDAttri = 0x1 
[  250.723357] AsicRemovePairwiseKeyEntry : Wcid #1 
[  250.723361] remove none key #0
[  250.723365] AsicRemoveSharedKeyEntry: #0 
[  250.723371] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
[  250.723376] remove none key #1
[  250.723379] AsicRemoveSharedKeyEntry: #1 
[  250.723384] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
[  250.723389] remove none key #2
[  250.723393] AsicRemoveSharedKeyEntry: #2 
[  250.723398] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
[  250.723403] remove none key #3
[  250.723406] AsicRemoveSharedKeyEntry: #3 
[  250.723412] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
[  250.723417] --->AsicEnableBssSync(INFRA mode)
[  250.723431] !!! LINK UP !!!  ClientStatusFlags=0)
[  250.723440] MlmeUpdateTxRates[MaxSupport = 54] = MaxDesire 54 Mbps
[  250.723446]  MlmeUpdateTxRates (MaxDesire=54, MaxSupport=54, MaxTxRate=54, MinRate=1, Rate Switching =1)
[  250.723452]  MlmeUpdateTxRates (TxRate=11, RtsRate=24, BasicRateBitmap=0x015f)
[  250.723458] MlmeUpdateTxRates (MlmeTransmit=0x0, MinHTPhyMode=0, MaxHTPhyMode=0x3, HTPhyMode=0x3)
[  250.723463] MlmeUpdateHtTxRates===> 
[  250.723467] !!! LINK UP !! (StaActive.bHtEnable =0, )
[  250.723472] NDIS_STATUS_MEDIA_CONNECT Event B!.BACapability = 3234040. ClientStatusFlags = 0
[  250.723482] RTMPSetLED::Mode=10,HighByte=0x60,LowByte=0x0a
[  250.724506] Txburst 2
[  250.724509] !!!pAd->bNextDisableRxBA= 0 
[  250.724513] not supports 20/40 BSS COEX !!! 
[  250.724517] pAd->CommonCfg.bBssCoexEnable 1 !!! 
[  250.724520] pAd->CommonCfg.Channel 11 !!! 
[  250.724524] pAd->StaActive.SupportedHtPhy.bHtEnable 0 !!! 
[  250.724528] pAd->MlmeAux.ExtCapInfo.BssCoexstSup 0 !!! 
[  250.724532] pAd->CommonCfg.CentralChannel 11 !!! 
[  250.724536] pAd->CommonCfg.PhyMode 9 !!! 
[  250.724539] CNTL - Association successful on BSS #0
[  250.727688] Receive EAPOL-Key frame, TYPE = 3, Length = 95
[  250.727820] MediaState is connected
[  250.736979] Receive EAPOL-Key frame, TYPE = 3, Length = 121
[  250.737133] rt_ioctl_siwencodeext::DefaultKeyId = 0
[  250.737139] rt_ioctl_siwencodeext::IW_ENCODE_ALG_TKIP - keyIdx = 0, ext->key_len = 32
[  250.737146] AsicAddSharedKeyEntry BssIndex=0, KeyIdx=0
[  250.737150] AsicAddSharedKeyEntry: TKIP key #0
[  250.737158]          Key = ce:3d:35:70:ae:35:d1:d5:e5:6c:15:d4:a7:5d:c2:ee
[  250.737164]          Rx MIC Key = 7f:d7:8a:34:9b:89:a5:99
[  250.737170]          Tx MIC Key = ec:f8:20:2c:8a:04:46:7e
[  250.737212] Read: SHARED_KEY_MODE_BASE at this Bss[0] KeyIdx[0]= 0x0 
[  250.737217] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x3 
[  250.737226] AsicUpdateWCIDIVEIV: wcid(1) 0x20000001, 0x00000000 
[  250.737233] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=TKIP
[  250.737237]          WCIDAttri = 0x6 
[  250.745221] Receive EAPOL-Key frame, TYPE = 3, Length = 127
[  250.745335] rt_ioctl_siwencodeext::IW_ENCODE_ALG_TKIP - keyIdx = 1, ext->key_len = 32
[  250.745342] AsicAddSharedKeyEntry BssIndex=0, KeyIdx=1
[  250.745346] AsicAddSharedKeyEntry: TKIP key #1
[  250.745354]          Key = f2:2e:76:cb:23:a1:11:70:4e:70:66:c5:00:30:94:71
[  250.745360]          Rx MIC Key = ce:55:9a:1e:96:78:69:a9
[  250.745366]          Tx MIC Key = 6d:8b:db:9a:a8:9b:65:72
[  250.745408] Read: SHARED_KEY_MODE_BASE at this Bss[0] KeyIdx[1]= 0x3 
[  250.745413] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x33 
[  251.943215] ==>rt_ioctl_giwfreq  11
[  251.943253] ===>rt_ioctl_giwencode 0
[  251.943260] MediaState is connected
[  251.943268] ==>rt_ioctl_giwmode(mode=2)
[  251.943283] ===>rt_ioctl_giwrange
[  251.943306] rt28xx_get_wireless_stats --->
[  251.943310] <--- rt28xx_get_wireless_stats
[  254.322133] ==>rt_ioctl_giwfreq  11
[  254.322172] ===>rt_ioctl_giwencode 0
[  254.322180] MediaState is connected
[  254.322187] ==>rt_ioctl_giwmode(mode=2)
[  254.322195] ===>rt_ioctl_giwrange
[  254.322218] rt28xx_get_wireless_stats --->
[  254.322222] <--- rt28xx_get_wireless_stats
[  256.333719] ==>rt_ioctl_giwfreq  11
[  256.333757] ===>rt_ioctl_giwencode 0
[  256.333765] MediaState is connected
[  256.333772] ==>rt_ioctl_giwmode(mode=2)
[  256.333780] ===>rt_ioctl_giwrange
[  256.333803] rt28xx_get_wireless_stats --->
[  256.333807] <--- rt28xx_get_wireless_stats
[  258.608046] ra0: no IPv6 routers present
[  259.332709] ==>rt_ioctl_giwfreq  11
[  259.332748] ===>rt_ioctl_giwencode 0
[  259.332756] MediaState is connected
[  259.332762] ==>rt_ioctl_giwmode(mode=2)
[  259.332770] ===>rt_ioctl_giwrange
[  259.332793] rt28xx_get_wireless_stats --->
[  259.332797] <--- rt28xx_get_wireless_stats
[  262.333995] ==>rt_ioctl_giwfreq  11
[  262.334034] ===>rt_ioctl_giwencode 0
[  262.334042] MediaState is connected
[  262.334049] ==>rt_ioctl_giwmode(mode=2)
[  262.334057] ===>rt_ioctl_giwrange
[  262.334080] rt28xx_get_wireless_stats --->
[  262.334085] <--- rt28xx_get_wireless_stats
[  265.327809] ==>rt_ioctl_giwfreq  11
[  265.327848] ===>rt_ioctl_giwencode 0
[  265.327856] MediaState is connected
[  265.327864] ==>rt_ioctl_giwmode(mode=2)
[  265.327872] ===>rt_ioctl_giwrange
[  265.327896] rt28xx_get_wireless_stats --->
[  265.327900] <--- rt28xx_get_wireless_stats
[  270.538320] ==>rt_ioctl_giwfreq  11
[  270.538362] ===>rt_ioctl_giwencode 0
[  270.538370] MediaState is connected
[  270.538377] ==>rt_ioctl_giwmode(mode=2)
[  270.538385] ===>rt_ioctl_giwrange
[  270.538409] rt28xx_get_wireless_stats --->
[  270.538413] <--- rt28xx_get_wireless_stats
[  275.538274] ==>rt_ioctl_giwfreq  11
[  275.538313] ===>rt_ioctl_giwencode 0
[  275.538321] MediaState is connected
[  275.538328] ==>rt_ioctl_giwmode(mode=2)
[  275.538336] ===>rt_ioctl_giwrange
[  275.538359] rt28xx_get_wireless_stats --->
[  275.538364] <--- rt28xx_get_wireless_stats
[  280.544120] ==>rt_ioctl_giwfreq  11
[  280.544160] ===>rt_ioctl_giwencode 0
[  280.544168] MediaState is connected
[  280.544175] ==>rt_ioctl_giwmode(mode=2)
[  280.544183] ===>rt_ioctl_giwrange
[  280.544206] rt28xx_get_wireless_stats --->
[  280.544211] <--- rt28xx_get_wireless_stats
[  285.316032] QuickDRS: TxTotalCnt <= 15, train back to original rate 
[  285.537748] ==>rt_ioctl_giwfreq  11
[  285.537785] ===>rt_ioctl_giwencode 0
[  285.537792] MediaState is connected
[  285.537799] ==>rt_ioctl_giwmode(mode=2)
[  285.537807] ===>rt_ioctl_giwrange
[  285.537831] rt28xx_get_wireless_stats --->
[  285.537835] <--- rt28xx_get_wireless_stats
[  285.816025] QuickDRS: TxTotalCnt <= 15, train back to original rate 
[  290.543846] ==>rt_ioctl_giwfreq  11
[  290.543885] ===>rt_ioctl_giwencode 0
[  290.543893] MediaState is connected
[  290.543900] ==>rt_ioctl_giwmode(mode=2)
[  290.543908] ===>rt_ioctl_giwrange
[  290.543931] rt28xx_get_wireless_stats --->
[  290.543935] <--- rt28xx_get_wireless_stats
[  295.536629] ==>rt_ioctl_giwfreq  11
[  295.536641] ===>rt_ioctl_giwencode 0
[  295.536644] MediaState is connected
[  295.536646] ==>rt_ioctl_giwmode(mode=2)
[  295.536648] ===>rt_ioctl_giwrange
[  295.536656] rt28xx_get_wireless_stats --->
[  295.536657] <--- rt28xx_get_wireless_stats
[  299.336065] QuickDRS: TxTotalCnt <= 15, train back to original rate 
[  300.534510] ==>rt_ioctl_giwfreq  11
[  300.534554] ===>rt_ioctl_giwencode 0
[  300.534563] MediaState is connected
[  300.534570] ==>rt_ioctl_giwmode(mode=2)
[  300.534579] ===>rt_ioctl_giwrange
[  300.534604] rt28xx_get_wireless_stats --->
[  300.534609] <--- rt28xx_get_wireless_stats
[  300.836050] QuickDRS: TxTotalCnt <= 15, train back to original rate 
[  304.848023] QuickDRS: TxTotalCnt <= 15, train back to original rate 
[  305.528102] ==>rt_ioctl_giwfreq  11
[  305.528119] ===>rt_ioctl_giwencode 0
[  305.528122] MediaState is connected
[  305.528125] ==>rt_ioctl_giwmode(mode=2)
[  305.528129] ===>rt_ioctl_giwrange
[  305.528138] rt28xx_get_wireless_stats --->
[  305.528141] <--- rt28xx_get_wireless_stats
[  310.550847] ==>rt_ioctl_giwfreq  11
[  310.550889] ===>rt_ioctl_giwencode 0
[  310.550897] MediaState is connected
[  310.550904] ==>rt_ioctl_giwmode(mode=2)
[  310.550913] ===>rt_ioctl_giwrange
[  310.550939] rt28xx_get_wireless_stats --->
[  310.550943] <--- rt28xx_get_wireless_stats
[  315.536335] ==>rt_ioctl_giwfreq  11
[  315.536380] ===>rt_ioctl_giwencode 0
[  315.536389] MediaState is connected
[  315.536397] ==>rt_ioctl_giwmode(mode=2)
[  315.536406] ===>rt_ioctl_giwrange
[  315.536433] rt28xx_get_wireless_stats --->
[  315.536438] <--- rt28xx_get_wireless_stats
[  320.535251] ==>rt_ioctl_giwfreq  11
[  320.535272] ===>rt_ioctl_giwencode 0
[  320.535277] MediaState is connected
[  320.535281] ==>rt_ioctl_giwmode(mode=2)
[  320.535286] ===>rt_ioctl_giwrange
[  320.535299] rt28xx_get_wireless_stats --->
[  320.535302] <--- rt28xx_get_wireless_stats
[  325.534081] ==>rt_ioctl_giwfreq  11
[  325.534100] ===>rt_ioctl_giwencode 0
[  325.534104] MediaState is connected
[  325.534107] ==>rt_ioctl_giwmode(mode=2)
[  325.534114] ===>rt_ioctl_giwrange
[  325.534125] rt28xx_get_wireless_stats --->
[  325.534127] <--- rt28xx_get_wireless_stats
[  330.543842] ==>rt_ioctl_giwfreq  11
[  330.543856] ===>rt_ioctl_giwencode 0
[  330.543858] MediaState is connected
[  330.543860] ==>rt_ioctl_giwmode(mode=2)
[  330.543863] ===>rt_ioctl_giwrange
[  330.543870] rt28xx_get_wireless_stats --->
[  330.543872] <--- rt28xx_get_wireless_stats
[  332.896032] QuickDRS: TxTotalCnt <= 15, train back to original rate 
[  335.542817] ==>rt_ioctl_giwfreq  11
[  335.542859] ===>rt_ioctl_giwencode 0
[  335.542868] MediaState is connected
[  335.542875] ==>rt_ioctl_giwmode(mode=2)
[  335.542883] ===>rt_ioctl_giwrange
[  335.542908] rt28xx_get_wireless_stats --->
[  335.542913] <--- rt28xx_get_wireless_stats
[  340.544376] ==>rt_ioctl_giwfreq  11
[  340.544422] ===>rt_ioctl_giwencode 0
[  340.544431] MediaState is connected
[  340.544439] ==>rt_ioctl_giwmode(mode=2)
[  340.544448] ===>rt_ioctl_giwrange
[  340.544475] rt28xx_get_wireless_stats --->
[  340.544480] <--- rt28xx_get_wireless_stats
[  345.544799] ==>rt_ioctl_giwfreq  11
[  345.544837] ===>rt_ioctl_giwencode 0
[  345.544845] MediaState is connected
[  345.544852] ==>rt_ioctl_giwmode(mode=2)
[  345.544860] ===>rt_ioctl_giwrange
[  345.544883] rt28xx_get_wireless_stats --->
[  345.544888] <--- rt28xx_get_wireless_stats
[  350.539402] ==>rt_ioctl_giwfreq  11
[  350.539441] ===>rt_ioctl_giwencode 0
[  350.539448] MediaState is connected
[  350.539455] ==>rt_ioctl_giwmode(mode=2)
[  350.539463] ===>rt_ioctl_giwrange
[  350.539486] rt28xx_get_wireless_stats --->
[  350.539491] <--- rt28xx_get_wireless_stats
[  355.543509] ==>rt_ioctl_giwfreq  11
[  355.543548] ===>rt_ioctl_giwencode 0
[  355.543556] MediaState is connected
[  355.543563] ==>rt_ioctl_giwmode(mode=2)
[  355.543571] ===>rt_ioctl_giwrange
[  355.543594] rt28xx_get_wireless_stats --->
[  355.543598] <--- rt28xx_get_wireless_stats
[  360.539414] ==>rt_ioctl_giwfreq  11
[  360.539453] ===>rt_ioctl_giwencode 0
[  360.539461] MediaState is connected
[  360.539468] ==>rt_ioctl_giwmode(mode=2)
[  360.539477] ===>rt_ioctl_giwrange
[  360.539501] rt28xx_get_wireless_stats --->
[  360.539505] <--- rt28xx_get_wireless_stats
[  365.538882] ==>rt_ioctl_giwfreq  11
[  365.538927] ===>rt_ioctl_giwencode 0
[  365.538935] MediaState is connected
[  365.538943] ==>rt_ioctl_giwmode(mode=2)
[  365.538951] ===>rt_ioctl_giwrange
[  365.538976] rt28xx_get_wireless_stats --->
[  365.538981] <--- rt28xx_get_wireless_stats
[  370.537268] ==>rt_ioctl_giwfreq  11
[  370.537308] ===>rt_ioctl_giwencode 0
[  370.537316] MediaState is connected
[  370.537323] ==>rt_ioctl_giwmode(mode=2)
[  370.537331] ===>rt_ioctl_giwrange
[  370.537354] rt28xx_get_wireless_stats --->
[  370.537359] <--- rt28xx_get_wireless_stats
[  375.541412] ==>rt_ioctl_giwfreq  11
[  375.541428] ===>rt_ioctl_giwencode 0
[  375.541431] MediaState is connected
[  375.541433] ==>rt_ioctl_giwmode(mode=2)
[  375.541436] ===>rt_ioctl_giwrange
[  375.541445] rt28xx_get_wireless_stats --->
[  375.541447] <--- rt28xx_get_wireless_stats
[  380.543186] ==>rt_ioctl_giwfreq  11
[  380.543199] ===>rt_ioctl_giwencode 0
[  380.543201] MediaState is connected
[  380.543203] ==>rt_ioctl_giwmode(mode=2)
[  380.543205] ===>rt_ioctl_giwrange
[  380.543212] rt28xx_get_wireless_stats --->
[  380.543214] <--- rt28xx_get_wireless_stats
[  385.542027] ==>rt_ioctl_giwfreq  11
[  385.542066] ===>rt_ioctl_giwencode 0
[  385.542074] MediaState is connected
[  385.542081] ==>rt_ioctl_giwmode(mode=2)
[  385.542089] ===>rt_ioctl_giwrange
[  385.542112] rt28xx_get_wireless_stats --->
[  385.542116] <--- rt28xx_get_wireless_stats
[  390.545352] ==>rt_ioctl_giwfreq  11
[  390.545392] ===>rt_ioctl_giwencode 0
[  390.545401] MediaState is connected
[  390.545408] ==>rt_ioctl_giwmode(mode=2)
[  390.545416] ===>rt_ioctl_giwrange
[  390.545440] rt28xx_get_wireless_stats --->
[  390.545444] <--- rt28xx_get_wireless_stats
[  395.542774] ==>rt_ioctl_giwfreq  11
[  395.542817] ===>rt_ioctl_giwencode 0
[  395.542825] MediaState is connected
[  395.542834] ==>rt_ioctl_giwmode(mode=2)
[  395.542843] ===>rt_ioctl_giwrange
[  395.542868] rt28xx_get_wireless_stats --->
[  395.542873] <--- rt28xx_get_wireless_stats
[  400.553567] ==>rt_ioctl_giwfreq  11
[  400.553606] ===>rt_ioctl_giwencode 0
[  400.553614] MediaState is connected
[  400.553621] ==>rt_ioctl_giwmode(mode=2)
[  400.553630] ===>rt_ioctl_giwrange
[  400.553653] rt28xx_get_wireless_stats --->
[  400.553658] <--- rt28xx_get_wireless_stats
[  405.548506] ==>rt_ioctl_giwfreq  11
[  405.548545] ===>rt_ioctl_giwencode 0
[  405.548552] MediaState is connected
[  405.548559] ==>rt_ioctl_giwmode(mode=2)
[  405.548567] ===>rt_ioctl_giwrange
[  405.548590] rt28xx_get_wireless_stats --->
[  405.548594] <--- rt28xx_get_wireless_stats
[  410.543391] ==>rt_ioctl_giwfreq  11
[  410.543430] ===>rt_ioctl_giwencode 0
[  410.543438] MediaState is connected
[  410.543445] ==>rt_ioctl_giwmode(mode=2)
[  410.543453] ===>rt_ioctl_giwrange
[  410.543475] rt28xx_get_wireless_stats --->
[  410.543480] <--- rt28xx_get_wireless_stats
[  415.539392] ==>rt_ioctl_giwfreq  11
[  415.539406] ===>rt_ioctl_giwencode 0
[  415.539409] MediaState is connected
[  415.539411] ==>rt_ioctl_giwmode(mode=2)
[  415.539416] ===>rt_ioctl_giwrange
[  415.539424] rt28xx_get_wireless_stats --->
[  415.539425] <--- rt28xx_get_wireless_stats
[  420.540198] ==>rt_ioctl_giwfreq  11
[  420.540217] ===>rt_ioctl_giwencode 0
[  420.540221] MediaState is connected
[  420.540224] ==>rt_ioctl_giwmode(mode=2)
[  420.540228] ===>rt_ioctl_giwrange
[  420.540239] rt28xx_get_wireless_stats --->
[  420.540241] <--- rt28xx_get_wireless_stats
[  425.543106] ==>rt_ioctl_giwfreq  11
[  425.543145] ===>rt_ioctl_giwencode 0
[  425.543153] MediaState is connected
[  425.543160] ==>rt_ioctl_giwmode(mode=2)
[  425.543168] ===>rt_ioctl_giwrange
[  425.543191] rt28xx_get_wireless_stats --->
[  425.543196] <--- rt28xx_get_wireless_stats
[  430.549519] ==>rt_ioctl_giwfreq  11
[  430.549563] ===>rt_ioctl_giwencode 0
[  430.549572] MediaState is connected
[  430.549580] ==>rt_ioctl_giwmode(mode=2)
[  430.549589] ===>rt_ioctl_giwrange
[  430.549616] rt28xx_get_wireless_stats --->
[  430.549621] <--- rt28xx_get_wireless_stats
[  435.542121] ==>rt_ioctl_giwfreq  11
[  435.542166] ===>rt_ioctl_giwencode 0
[  435.542175] MediaState is connected
[  435.542182] ==>rt_ioctl_giwmode(mode=2)
[  435.542191] ===>rt_ioctl_giwrange
[  435.542217] rt28xx_get_wireless_stats --->
[  435.542223] <--- rt28xx_get_wireless_stats
[  440.529739] ==>rt_ioctl_giwfreq  11
[  440.529760] ===>rt_ioctl_giwencode 0
[  440.529764] MediaState is connected
[  440.529766] ==>rt_ioctl_giwmode(mode=2)
[  440.529769] ===>rt_ioctl_giwrange
[  440.529779] rt28xx_get_wireless_stats --->
[  440.529781] <--- rt28xx_get_wireless_stats
[  445.542080] ==>rt_ioctl_giwfreq  11
[  445.542119] ===>rt_ioctl_giwencode 0
[  445.542127] MediaState is connected
[  445.542134] ==>rt_ioctl_giwmode(mode=2)
[  445.542142] ===>rt_ioctl_giwrange
[  445.542165] rt28xx_get_wireless_stats --->
[  445.542169] <--- rt28xx_get_wireless_stats
[  450.536298] ==>rt_ioctl_giwfreq  11
[  450.536337] ===>rt_ioctl_giwencode 0
[  450.536345] MediaState is connected
[  450.536352] ==>rt_ioctl_giwmode(mode=2)
[  450.536359] ===>rt_ioctl_giwrange
[  450.536382] rt28xx_get_wireless_stats --->
[  450.536387] <--- rt28xx_get_wireless_stats
[  455.534365] ==>rt_ioctl_giwfreq  11
[  455.534383] ===>rt_ioctl_giwencode 0
[  455.534387] MediaState is connected
[  455.534390] ==>rt_ioctl_giwmode(mode=2)
[  455.534397] ===>rt_ioctl_giwrange
[  455.534421] rt28xx_get_wireless_stats --->
[  455.534423] <--- rt28xx_get_wireless_stats
[  460.536919] ==>rt_ioctl_giwfreq  11
[  460.536960] ===>rt_ioctl_giwencode 0
[  460.536969] MediaState is connected
[  460.536977] ==>rt_ioctl_giwmode(mode=2)
[  460.536986] ===>rt_ioctl_giwrange
[  460.537010] rt28xx_get_wireless_stats --->
[  460.537015] <--- rt28xx_get_wireless_stats
[  465.542980] ==>rt_ioctl_giwfreq  11
[  465.542993] ===>rt_ioctl_giwencode 0
[  465.542995] MediaState is connected
[  465.542997] ==>rt_ioctl_giwmode(mode=2)
[  465.543000] ===>rt_ioctl_giwrange
[  465.543006] rt28xx_get_wireless_stats --->
[  465.543008] <--- rt28xx_get_wireless_stats
[  470.541574] ==>rt_ioctl_giwfreq  11
[  470.541618] ===>rt_ioctl_giwencode 0
[  470.541628] MediaState is connected
[  470.541636] ==>rt_ioctl_giwmode(mode=2)
[  470.541652] ===>rt_ioctl_giwrange
[  470.541680] rt28xx_get_wireless_stats --->
[  470.541686] <--- rt28xx_get_wireless_stats
[  475.540385] ==>rt_ioctl_giwfreq  11
[  475.540424] ===>rt_ioctl_giwencode 0
[  475.540432] MediaState is connected
[  475.540439] ==>rt_ioctl_giwmode(mode=2)
[  475.540447] ===>rt_ioctl_giwrange
[  475.540471] rt28xx_get_wireless_stats --->
[  475.540475] <--- rt28xx_get_wireless_stats
[  480.546479] ==>rt_ioctl_giwfreq  11
[  480.546519] ===>rt_ioctl_giwencode 0
[  480.546527] MediaState is connected
[  480.546534] ==>rt_ioctl_giwmode(mode=2)
[  480.546542] ===>rt_ioctl_giwrange
[  480.546566] rt28xx_get_wireless_stats --->
[  480.546570] <--- rt28xx_get_wireless_stats
[  485.531743] ==>rt_ioctl_giwfreq  11
[  485.531766] ===>rt_ioctl_giwencode 0
[  485.531772] MediaState is connected
[  485.531775] ==>rt_ioctl_giwmode(mode=2)
[  485.531779] ===>rt_ioctl_giwrange
[  485.531791] rt28xx_get_wireless_stats --->
[  485.531795] <--- rt28xx_get_wireless_stats
[  490.543314] ==>rt_ioctl_giwfreq  11
[  490.543353] ===>rt_ioctl_giwencode 0
[  490.543362] MediaState is connected
[  490.543369] ==>rt_ioctl_giwmode(mode=2)
[  490.543376] ===>rt_ioctl_giwrange
[  490.543400] rt28xx_get_wireless_stats --->
[  490.543405] <--- rt28xx_get_wireless_stats
[  495.533893] ==>rt_ioctl_giwfreq  11
[  495.533910] ===>rt_ioctl_giwencode 0
[  495.533912] MediaState is connected
[  495.533914] ==>rt_ioctl_giwmode(mode=2)
[  495.533919] ===>rt_ioctl_giwrange
[  495.533927] rt28xx_get_wireless_stats --->
[  495.533929] <--- rt28xx_get_wireless_stats
[  500.547320] ==>rt_ioctl_giwfreq  11
[  500.547335] ===>rt_ioctl_giwencode 0
[  500.547338] MediaState is connected
[  500.547340] ==>rt_ioctl_giwmode(mode=2)
[  500.547343] ===>rt_ioctl_giwrange
[  500.547350] rt28xx_get_wireless_stats --->
[  500.547351] <--- rt28xx_get_wireless_stats
[  505.539538] ==>rt_ioctl_giwfreq  11
[  505.539577] ===>rt_ioctl_giwencode 0
[  505.539585] MediaState is connected
[  505.539592] ==>rt_ioctl_giwmode(mode=2)
[  505.539600] ===>rt_ioctl_giwrange
[  505.539641] rt28xx_get_wireless_stats --->
[  505.539646] <--- rt28xx_get_wireless_stats
[  510.533836] ==>rt_ioctl_giwfreq  11
[  510.533879] ===>rt_ioctl_giwencode 0
[  510.533888] MediaState is connected
[  510.533895] ==>rt_ioctl_giwmode(mode=2)
[  510.533904] ===>rt_ioctl_giwrange
[  510.533931] rt28xx_get_wireless_stats --->
[  510.533935] <--- rt28xx_get_wireless_stats
[  515.539641] ==>rt_ioctl_giwfreq  11
[  515.539679] ===>rt_ioctl_giwencode 0
[  515.539687] MediaState is connected
[  515.539693] ==>rt_ioctl_giwmode(mode=2)
[  515.539701] ===>rt_ioctl_giwrange
[  515.539725] rt28xx_get_wireless_stats --->
[  515.539729] <--- rt28xx_get_wireless_stats
[  520.543510] ==>rt_ioctl_giwfreq  11
[  520.543549] ===>rt_ioctl_giwencode 0
[  520.543557] MediaState is connected
[  520.543564] ==>rt_ioctl_giwmode(mode=2)
[  520.543572] ===>rt_ioctl_giwrange
[  520.543595] rt28xx_get_wireless_stats --->
[  520.543600] <--- rt28xx_get_wireless_stats
[  525.541231] ==>rt_ioctl_giwfreq  11
[  525.541270] ===>rt_ioctl_giwencode 0
[  525.541278] MediaState is connected
[  525.541285] ==>rt_ioctl_giwmode(mode=2)
[  525.541293] ===>rt_ioctl_giwrange
[  525.541316] rt28xx_get_wireless_stats --->
[  525.541320] <--- rt28xx_get_wireless_stats
[  530.535947] ==>rt_ioctl_giwfreq  11
[  530.535964] ===>rt_ioctl_giwencode 0
[  530.535968] MediaState is connected
[  530.535971] ==>rt_ioctl_giwmode(mode=2)
[  530.535975] ===>rt_ioctl_giwrange
[  530.535984] rt28xx_get_wireless_stats --->
[  530.535987] <--- rt28xx_get_wireless_stats
[  535.523525] ==>rt_ioctl_giwfreq  11
[  535.523542] ===>rt_ioctl_giwencode 0
[  535.523545] MediaState is connected
[  535.523548] ==>rt_ioctl_giwmode(mode=2)
[  535.523551] ===>rt_ioctl_giwrange
[  535.523562] rt28xx_get_wireless_stats --->
[  535.523564] <--- rt28xx_get_wireless_stats
[  537.196046] QuickDRS: TxTotalCnt <= 15, train back to original rate 
[  540.542455] ==>rt_ioctl_giwfreq  11
[  540.542493] ===>rt_ioctl_giwencode 0
[  540.542501] MediaState is connected
[  540.542508] ==>rt_ioctl_giwmode(mode=2)
[  540.542524] ===>rt_ioctl_giwrange
[  540.542547] rt28xx_get_wireless_stats --->
[  540.542552] <--- rt28xx_get_wireless_stats
[  545.543048] ==>rt_ioctl_giwfreq  11
[  545.543085] ===>rt_ioctl_giwencode 0
[  545.543093] MediaState is connected
[  545.543100] ==>rt_ioctl_giwmode(mode=2)
[  545.543108] ===>rt_ioctl_giwrange
[  545.543131] rt28xx_get_wireless_stats --->
[  545.543135] <--- rt28xx_get_wireless_stats
[  550.541127] ==>rt_ioctl_giwfreq  11
[  550.541165] ===>rt_ioctl_giwencode 0
[  550.541173] MediaState is connected
[  550.541180] ==>rt_ioctl_giwmode(mode=2)
[  550.541188] ===>rt_ioctl_giwrange
[  550.541211] rt28xx_get_wireless_stats --->
[  550.541215] <--- rt28xx_get_wireless_stats
[  555.541287] ==>rt_ioctl_giwfreq  11
[  555.541326] ===>rt_ioctl_giwencode 0
[  555.541334] MediaState is connected
[  555.541341] ==>rt_ioctl_giwmode(mode=2)
[  555.541349] ===>rt_ioctl_giwrange
[  555.541372] rt28xx_get_wireless_stats --->
[  555.541376] <--- rt28xx_get_wireless_stats
[  560.539300] ==>rt_ioctl_giwfreq  11
[  560.539339] ===>rt_ioctl_giwencode 0
[  560.539347] MediaState is connected
[  560.539354] ==>rt_ioctl_giwmode(mode=2)
[  560.539361] ===>rt_ioctl_giwrange
[  560.539384] rt28xx_get_wireless_stats --->
[  560.539389] <--- rt28xx_get_wireless_stats
[  565.541394] ==>rt_ioctl_giwfreq  11
[  565.541432] ===>rt_ioctl_giwencode 0
[  565.541440] MediaState is connected
[  565.541447] ==>rt_ioctl_giwmode(mode=2)
[  565.541463] ===>rt_ioctl_giwrange
[  565.541487] rt28xx_get_wireless_stats --->
[  565.541492] <--- rt28xx_get_wireless_stats
[  570.532786] ==>rt_ioctl_giwfreq  11
[  570.532825] ===>rt_ioctl_giwencode 0
[  570.532833] MediaState is connected
[  570.532840] ==>rt_ioctl_giwmode(mode=2)
[  570.532848] ===>rt_ioctl_giwrange
[  570.532872] rt28xx_get_wireless_stats --->
[  570.532876] <--- rt28xx_get_wireless_stats
[  575.543202] ==>rt_ioctl_giwfreq  11
[  575.543240] ===>rt_ioctl_giwencode 0
[  575.543248] MediaState is connected
[  575.543255] ==>rt_ioctl_giwmode(mode=2)
[  575.543270] ===>rt_ioctl_giwrange
[  575.543293] rt28xx_get_wireless_stats --->
[  575.543298] <--- rt28xx_get_wireless_stats
[  580.544669] ==>rt_ioctl_giwfreq  11
[  580.544707] ===>rt_ioctl_giwencode 0
[  580.544715] MediaState is connected
[  580.544722] ==>rt_ioctl_giwmode(mode=2)
[  580.544730] ===>rt_ioctl_giwrange
[  580.544753] rt28xx_get_wireless_stats --->
[  580.544757] <--- rt28xx_get_wireless_stats
[  585.541706] ==>rt_ioctl_giwfreq  11
[  585.541724] ===>rt_ioctl_giwencode 0
[  585.541728] MediaState is connected
[  585.541731] ==>rt_ioctl_giwmode(mode=2)
[  585.541735] ===>rt_ioctl_giwrange
[  585.541745] rt28xx_get_wireless_stats --->
[  585.541748] <--- rt28xx_get_wireless_stats
[  590.541733] ==>rt_ioctl_giwfreq  11
[  590.541772] ===>rt_ioctl_giwencode 0
[  590.541780] MediaState is connected
[  590.541787] ==>rt_ioctl_giwmode(mode=2)
[  590.541794] ===>rt_ioctl_giwrange
[  590.541817] rt28xx_get_wireless_stats --->
[  590.541821] <--- rt28xx_get_wireless_stats
[  595.540620] ==>rt_ioctl_giwfreq  11
[  595.540659] ===>rt_ioctl_giwencode 0
[  595.540667] MediaState is connected
[  595.540674] ==>rt_ioctl_giwmode(mode=2)
[  595.540689] ===>rt_ioctl_giwrange
[  595.540713] rt28xx_get_wireless_stats --->
[  595.540717] <--- rt28xx_get_wireless_stats
[  600.541844] ==>rt_ioctl_giwfreq  11
[  600.541883] ===>rt_ioctl_giwencode 0
[  600.541890] MediaState is connected
[  600.541897] ==>rt_ioctl_giwmode(mode=2)
[  600.541905] ===>rt_ioctl_giwrange
[  600.541928] rt28xx_get_wireless_stats --->
[  600.541933] <--- rt28xx_get_wireless_stats
[  605.543551] ==>rt_ioctl_giwfreq  11
[  605.543590] ===>rt_ioctl_giwencode 0
[  605.543598] MediaState is connected
[  605.543606] ==>rt_ioctl_giwmode(mode=2)
[  605.543614] ===>rt_ioctl_giwrange
[  605.543637] rt28xx_get_wireless_stats --->
[  605.543641] <--- rt28xx_get_wireless_stats
[  610.532449] ==>rt_ioctl_giwfreq  11
[  610.532468] ===>rt_ioctl_giwencode 0
[  610.532471] MediaState is connected
[  610.532475] ==>rt_ioctl_giwmode(mode=2)
[  610.532478] ===>rt_ioctl_giwrange
[  610.532489] rt28xx_get_wireless_stats --->
[  610.532491] <--- rt28xx_get_wireless_stats
[  615.541534] ==>rt_ioctl_giwfreq  11
[  615.541572] ===>rt_ioctl_giwencode 0
[  615.541580] MediaState is connected
[  615.541587] ==>rt_ioctl_giwmode(mode=2)
[  615.541595] ===>rt_ioctl_giwrange
[  615.541619] rt28xx_get_wireless_stats --->
[  615.541623] <--- rt28xx_get_wireless_stats
[  620.545249] ==>rt_ioctl_giwfreq  11
[  620.545288] ===>rt_ioctl_giwencode 0
[  620.545296] MediaState is connected
[  620.545303] ==>rt_ioctl_giwmode(mode=2)
[  620.545310] ===>rt_ioctl_giwrange
[  620.545333] rt28xx_get_wireless_stats --->
[  620.545338] <--- rt28xx_get_wireless_stats
[  625.543743] ==>rt_ioctl_giwfreq  11
[  625.543781] ===>rt_ioctl_giwencode 0
[  625.543789] MediaState is connected
[  625.543796] ==>rt_ioctl_giwmode(mode=2)
[  625.543804] ===>rt_ioctl_giwrange
[  625.543826] rt28xx_get_wireless_stats --->
[  625.543831] <--- rt28xx_get_wireless_stats
[  630.543880] ==>rt_ioctl_giwfreq  11
[  630.543925] ===>rt_ioctl_giwencode 0
[  630.543935] MediaState is connected
[  630.543942] ==>rt_ioctl_giwmode(mode=2)
[  630.543958] ===>rt_ioctl_giwrange
[  630.543984] rt28xx_get_wireless_stats --->
[  630.543988] <--- rt28xx_get_wireless_stats
[  635.537248] ==>rt_ioctl_giwfreq  11
[  635.537286] ===>rt_ioctl_giwencode 0
[  635.537294] MediaState is connected
[  635.537301] ==>rt_ioctl_giwmode(mode=2)
[  635.537309] ===>rt_ioctl_giwrange
[  635.537333] rt28xx_get_wireless_stats --->
[  635.537338] <--- rt28xx_get_wireless_stats
[  640.539159] ==>rt_ioctl_giwfreq  11
[  640.539205] ===>rt_ioctl_giwencode 0
[  640.539213] MediaState is connected
[  640.539220] ==>rt_ioctl_giwmode(mode=2)
[  640.539228] ===>rt_ioctl_giwrange
[  640.539252] rt28xx_get_wireless_stats --->
[  640.539257] <--- rt28xx_get_wireless_stats
[  645.539074] ==>rt_ioctl_giwfreq  11
[  645.539112] ===>rt_ioctl_giwencode 0
[  645.539121] MediaState is connected
[  645.539127] ==>rt_ioctl_giwmode(mode=2)
[  645.539135] ===>rt_ioctl_giwrange
[  645.539159] rt28xx_get_wireless_stats --->
[  645.539163] <--- rt28xx_get_wireless_stats
[  650.543159] ==>rt_ioctl_giwfreq  11
[  650.543171] ===>rt_ioctl_giwencode 0
[  650.543174] MediaState is connected
[  650.543176] ==>rt_ioctl_giwmode(mode=2)
[  650.543179] ===>rt_ioctl_giwrange
[  650.543186] rt28xx_get_wireless_stats --->
[  650.543187] <--- rt28xx_get_wireless_stats
[  655.544218] ==>rt_ioctl_giwfreq  11
[  655.544257] ===>rt_ioctl_giwencode 0
[  655.544266] MediaState is connected
[  655.544273] ==>rt_ioctl_giwmode(mode=2)
[  655.544288] ===>rt_ioctl_giwrange
[  655.544311] rt28xx_get_wireless_stats --->
[  655.544316] <--- rt28xx_get_wireless_stats
[  660.544429] ==>rt_ioctl_giwfreq  11
[  660.544468] ===>rt_ioctl_giwencode 0
[  660.544476] MediaState is connected
[  660.544483] ==>rt_ioctl_giwmode(mode=2)
[  660.544490] ===>rt_ioctl_giwrange
[  660.544514] rt28xx_get_wireless_stats --->
[  660.544518] <--- rt28xx_get_wireless_stats
[  665.537495] ==>rt_ioctl_giwfreq  11
[  665.537534] ===>rt_ioctl_giwencode 0
[  665.537542] MediaState is connected
[  665.537548] ==>rt_ioctl_giwmode(mode=2)
[  665.537564] ===>rt_ioctl_giwrange
[  665.537587] rt28xx_get_wireless_stats --->
[  665.537592] <--- rt28xx_get_wireless_stats
[  670.541207] ==>rt_ioctl_giwfreq  11
[  670.541247] ===>rt_ioctl_giwencode 0
[  670.541255] MediaState is connected
[  670.541262] ==>rt_ioctl_giwmode(mode=2)
[  670.541270] ===>rt_ioctl_giwrange
[  670.541293] rt28xx_get_wireless_stats --->
[  670.541297] <--- rt28xx_get_wireless_stats
[  675.534854] ==>rt_ioctl_giwfreq  11
[  675.534875] ===>rt_ioctl_giwencode 0
[  675.534880] MediaState is connected
[  675.534883] ==>rt_ioctl_giwmode(mode=2)
[  675.534888] ===>rt_ioctl_giwrange
[  675.534901] rt28xx_get_wireless_stats --->
[  675.534904] <--- rt28xx_get_wireless_stats
[  680.539242] ==>rt_ioctl_giwfreq  11
[  680.539280] ===>rt_ioctl_giwencode 0
[  680.539288] MediaState is connected
[  680.539295] ==>rt_ioctl_giwmode(mode=2)
[  680.539303] ===>rt_ioctl_giwrange
[  680.539327] rt28xx_get_wireless_stats --->
[  680.539331] <--- rt28xx_get_wireless_stats
[  685.541240] ==>rt_ioctl_giwfreq  11
[  685.541278] ===>rt_ioctl_giwencode 0
[  685.541287] MediaState is connected
[  685.541293] ==>rt_ioctl_giwmode(mode=2)
[  685.541301] ===>rt_ioctl_giwrange
[  685.541324] rt28xx_get_wireless_stats --->
[  685.541329] <--- rt28xx_get_wireless_stats
[  690.541243] ==>rt_ioctl_giwfreq  11
[  690.541281] ===>rt_ioctl_giwencode 0
[  690.541289] MediaState is connected
[  690.541296] ==>rt_ioctl_giwmode(mode=2)
[  690.541304] ===>rt_ioctl_giwrange
[  690.541327] rt28xx_get_wireless_stats --->
[  690.541332] <--- rt28xx_get_wireless_stats
[  695.540959] ==>rt_ioctl_giwfreq  11
[  695.540971] ===>rt_ioctl_giwencode 0
[  695.540974] MediaState is connected
[  695.540976] ==>rt_ioctl_giwmode(mode=2)
[  695.540978] ===>rt_ioctl_giwrange
[  695.540985] rt28xx_get_wireless_stats --->
[  695.540986] <--- rt28xx_get_wireless_stats
[  700.529937] ==>rt_ioctl_giwfreq  11
[  700.529975] ===>rt_ioctl_giwencode 0
[  700.529982] MediaState is connected
[  700.529987] ==>rt_ioctl_giwmode(mode=2)
[  700.529996] ===>rt_ioctl_giwrange
[  700.530019] rt28xx_get_wireless_stats --->
[  700.530023] <--- rt28xx_get_wireless_stats
[  705.544735] ==>rt_ioctl_giwfreq  11
[  705.544773] ===>rt_ioctl_giwencode 0
[  705.544781] MediaState is connected
[  705.544788] ==>rt_ioctl_giwmode(mode=2)
[  705.544796] ===>rt_ioctl_giwrange
[  705.544819] rt28xx_get_wireless_stats --->
[  705.544823] <--- rt28xx_get_wireless_stats
[  710.541104] ==>rt_ioctl_giwfreq  11
[  710.541143] ===>rt_ioctl_giwencode 0
[  710.541150] MediaState is connected
[  710.541157] ==>rt_ioctl_giwmode(mode=2)
[  710.541165] ===>rt_ioctl_giwrange
[  710.541188] rt28xx_get_wireless_stats --->
[  710.541193] <--- rt28xx_get_wireless_stats
[  715.539480] ==>rt_ioctl_giwfreq  11
[  715.539518] ===>rt_ioctl_giwencode 0
[  715.539526] MediaState is connected
[  715.539533] ==>rt_ioctl_giwmode(mode=2)
[  715.539541] ===>rt_ioctl_giwrange
[  715.539564] rt28xx_get_wireless_stats --->
[  715.539568] <--- rt28xx_get_wireless_stats
[  720.545099] ==>rt_ioctl_giwfreq  11
[  720.545137] ===>rt_ioctl_giwencode 0
[  720.545145] MediaState is connected
[  720.545152] ==>rt_ioctl_giwmode(mode=2)
[  720.545160] ===>rt_ioctl_giwrange
[  720.545183] rt28xx_get_wireless_stats --->
[  720.545187] <--- rt28xx_get_wireless_stats
[  725.539782] ==>rt_ioctl_giwfreq  11
[  725.539821] ===>rt_ioctl_giwencode 0
[  725.539829] MediaState is connected
[  725.539836] ==>rt_ioctl_giwmode(mode=2)
[  725.539851] ===>rt_ioctl_giwrange
[  725.539875] rt28xx_get_wireless_stats --->
[  725.539879] <--- rt28xx_get_wireless_stats
[  730.543774] ==>rt_ioctl_giwfreq  11
[  730.543813] ===>rt_ioctl_giwencode 0
[  730.543821] MediaState is connected
[  730.543829] ==>rt_ioctl_giwmode(mode=2)
[  730.543844] ===>rt_ioctl_giwrange
[  730.543868] rt28xx_get_wireless_stats --->
[  730.543872] <--- rt28xx_get_wireless_stats
[  735.541376] ==>rt_ioctl_giwfreq  11
[  735.541415] ===>rt_ioctl_giwencode 0
[  735.541423] MediaState is connected
[  735.541430] ==>rt_ioctl_giwmode(mode=2)
[  735.541438] ===>rt_ioctl_giwrange
[  735.541461] rt28xx_get_wireless_stats --->
[  735.541465] <--- rt28xx_get_wireless_stats
[  740.526257] ==>rt_ioctl_giwfreq  11
[  740.526270] ===>rt_ioctl_giwencode 0
[  740.526272] MediaState is connected
[  740.526274] ==>rt_ioctl_giwmode(mode=2)
[  740.526279] ===>rt_ioctl_giwrange
[  740.526286] rt28xx_get_wireless_stats --->
[  740.526287] <--- rt28xx_get_wireless_stats
[  745.544223] ==>rt_ioctl_giwfreq  11
[  745.544268] ===>rt_ioctl_giwencode 0
[  745.544276] MediaState is connected
[  745.544283] ==>rt_ioctl_giwmode(mode=2)
[  745.544291] ===>rt_ioctl_giwrange
[  745.544315] rt28xx_get_wireless_stats --->
[  745.544319] <--- rt28xx_get_wireless_stats
[  750.540863] ==>rt_ioctl_giwfreq  11
[  750.540903] ===>rt_ioctl_giwencode 0
[  750.540911] MediaState is connected
[  750.540918] ==>rt_ioctl_giwmode(mode=2)
[  750.540933] ===>rt_ioctl_giwrange
[  750.540956] rt28xx_get_wireless_stats --->
[  750.540961] <--- rt28xx_get_wireless_stats
 
i'm using a desktop with motherboard ASUS M4N68T-M series (NVIDIA geforce 7025/nforce 630a chipset)
i'm using ubuntu LUCID with kernel 2.6.38 with KDE
and i more thing i thought of saying u...every time i boot my pc i get the notification 
The audio playback device Ensoniq Audio PCI ENS1371(ES1371 DAC/ADC) does not work. 
falling back to HDA NVIDIA (VT17085 Analog)

plz help....thanks

---

### Post by BicyclerBoy on 2011-08-15
Install/run pavucontrol
Check your device mixer is not muted/ try changing the ouput device type & setup.

Your modprobe needed to be preceded by a rmmod *driver_module_name*
And only the last few lines of dmesg will be useful.
dmesg | tail

But as you're using lucid it could pay to add a launchpad ppa to update the alsa drivers..
Updating by compiling is a bad idea.
[https://launchpad.net/~team-iquik/+archive/alsa]("https://launchpad.net/%7Eteam-iquik/+archive/alsa")

Did you fix the 
options snd-hda-intel model=ALC880
problem ?

After editing any files in /etc/modprode.d/ you must rebuild the boot image
[sudo] update-initramfs -u

---

### Post by .... on 2011-08-15
ALC880 is a codec (and not the one you have). You have a VIA VT1708 codec and there is only one model option for that:
```
VIA VT17xx/VT18xx/VT20xx
========================
  auto        BIOS setup (default)
```

If you're using Lucid, I would use this script to update all of your ALSA stuff: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by surajrajpurohit on 2011-08-15
thanks 4 reply BicyclerBoy

i've fixed snd-hda-intel model=ALC880 by removing 

this lines in nano /etc/modprobe.d/alsa-base.conf,

and i've also rebuildted boot image...

but im sound card still not playing....

same proble....

---

### Post by surajrajpurohit on 2011-08-15
thanks 4 reply  ....

i've used script to update ALSA as mentioned in the threat 

[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

still the no solutions for problem....

sound is not coming.....

---

### Post by surajrajpurohit on 2011-08-15
hey i got my problem solved.....

i speakers are rocking......

i just followed the instructions from
 
[http://ubuntuforums.org/showthread.php?t=205449&highlight=nvidia+hda+sound+card](http://ubuntuforums.org/showthread.php?t=205449&highlight=nvidia+hda+sound+card)

and it got solved

thank q every body 4 helping....

---

### Post by .... on 2011-08-15
glad to be useful....

---

