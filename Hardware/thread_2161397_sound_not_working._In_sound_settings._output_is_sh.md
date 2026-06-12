---
title: "sound not working. In sound settings. output is showing : Dummy Output. Tried few thi"
date: 2013-07-10
forum: Hardware
---

### Post by itspallab on 2013-07-10
Hi I have intalled ubuntu 13.04 recently. But sound not working. In  sound settings. output is showing : Dummy Output. Tried few things but  no result. aplay shows - no sound card.
sudo aplay -l
aplay: device_list:252: no soundcards found...

 lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:11.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RC410 [Radeon Xpress 200/1100]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



Additional Info

DistroRelease: Ubuntu 13.04
Package: alsa-base 1.0.25+
dfsg-0ubuntu4
ProcVersionSignature: Ubuntu 3.8.0-19.29-generic 3.8.8
Uname: Linux 3.8.0-19-generic i686
ApportVersion: 2.9.2-0ubuntu8
Architecture: i386
AudioDevicesInUse: Error: command ['fuser', '-v', '/dev/snd/seq', '/dev/snd/timer'] failed with exit code 1:
Date: Mon Jul  8 00:07:54 2013
InstallationDate: Installed on 2013-07-07 (0 days ago)
InstallationMedia: Ubuntu 13.04 "Raring Ringtail" - Release i386 (20130424)
MarkForUpload: True
PackageArchitecture: all
SourcePackage: alsa-driver
Symptom: audio
Title: PCI/internal sound card not detected
UpgradeStatus: No upgrade log present (probably fresh install)
dmi.bios.date: 09/15/2006
dmi.bios.vendor: Award BIOS for Intel
dmi.bios.version: GC11010N.86A.0313.2006.0915.1840
dmi.board.name: D101GGC
dmi.board.vendor: Intel Corporation
dmi.chassis.type: 3
dmi.modalias: dmi:bvnAwardBIOSforIntel:bvrGC11010N.86A.0313.2006.0915.1840:bd09/15/2006:svn:pn:pvr:rvnIntelCorporation:rnD101GGC:rvr:cvn:ct3:cvr:

---

### Post by BreezyBrooke on 2013-07-10
What is you computer model, or motherboard model number? I can research the sound chip and see if it has issues in linux and to possible fixes.

---

### Post by itspallab on 2013-07-11
I have already provided that info. Please find below again. if you require any other info please reply.
SourcePackage: alsa-driver
Symptom: audio
Title: PCI/internal sound card not detected
UpgradeStatus: No upgrade log present (probably fresh install)
dmi.bios.date: 09/15/2006
dmi.bios.vendor: Award BIOS for Intel
dmi.bios.version: GC11010N.86A.0313.2006.0915.1840
dmi.board.name: D101GGC
dmi.board.vendor: Intel Corporation

---

### Post by Ranko Kohime on 2013-07-11
Check to make sure that your user is a member of the **audio** and **pulse** groups.  Open a terminal, type **groups** and hit enter.  If you don't see them listed, add them, and then logout or reboot.

command to add user to group:
```
usermod -a -G *group* *user*
```

---

### Post by Yellow Pasque on 2013-07-11
```
Uname: Linux 3.8.0-19-generic i686
```
Update your kernel (3.8.0-25 should be available). You may be hitting this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984)

If that doesn't work after rebooting, give your alsa info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> Check to make sure that your user is a member of the audio ... groups
Bad idea... [http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

---

### Post by itspallab on 2013-07-14
kernel update not worked. Now My kernel version is 3.8.0.26. After update rebooting also done. but not worked. I think ubuntu 13.04 can't recognize my desktop board's internal sound card. because I have used ubuntu 10.XX before. Then all are fine. But this new 13.04 sound is not working. Anyway find below the alsa-info. Thanks in advance.


upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.62
!!################################

!!Script ran on: Sun Jul 14 12:42:36 UTC 2013


!!Linux Distribution
!!------------------

Ubuntu 13.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 13.04" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 13.04" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:              
Product Name:              
Product Version:           
Firmware Version:  GC11010N.86A.0313.2006.0915.1840


!!Kernel Information
!!------------------

Kernel release:    3.8.0-26-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.8.0-26-generic
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:14.2 0403: 1002:437b (rev 01)
    Subsystem: 8086:d600


!!Modprobe options (Sound related)
!!--------------------------------

snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw---T+ 1 root audio 116,  1 Jul 14 18:00 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Jul 14 18:00 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:252: no soundcards found...

ARECORD

arecord: device_list:252: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
xt_TCPMSS
xt_tcpmss
xt_tcpudp
iptable_mangle
ip_tables
x_tables
pppoe
pppox
bnep
rfcomm
bluetooth
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
radeon
snd_page_alloc
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
snd_seq
snd_seq_device
snd_timer
ttm
drm_kms_helper
joydev
snd
drm
ppdev
microcode
psmouse
soundcore
i2c_algo_bit
serio_raw
mac_hid
i2c_piix4
shpchp
parport_pc
ati_agp
lp
parport
hid_generic
usbhid
hid
usb_storage
8139too
8139cp
pata_acpi
floppy
pata_atiixp
sata_sil


!!ALSA/HDA dmesg
!!--------------

[   10.283435] hda-codec: out of range cmd 3:0:393a:f00:5
[   10.283439] hda-codec: out of range cmd 3:0:393b:f00:5
[   10.283443] hda-codec: out of range cmd 3:0:393c:f00:5
[   10.283446] hda-codec: out of range cmd 3:0:393d:f00:5
[   10.283448] hda-codec: out of range cmd 3:0:393e:f00:5
[   10.283451] hda-codec: out of range cmd 3:0:393f:f00:5
[   10.283454] hda-codec: out of range cmd 3:0:3940:f00:5
[   10.283457] hda-codec: out of range cmd 3:0:3941:f00:5
[   10.283460] hda-codec: out of range cmd 3:0:3942:f00:5
[   10.283462] hda-codec: out of range cmd 3:0:3943:f00:5
[   10.283464] hda-codec: out of range cmd 3:0:3944:f00:5
[   10.283467] hda-codec: out of range cmd 3:0:3945:f00:5
[   10.283471] hda-codec: out of range cmd 3:0:3946:f00:5
[   10.283474] hda-codec: out of range cmd 3:0:3947:f00:5
[   10.283477] hda-codec: out of range cmd 3:0:3948:f00:5
[   10.283479] hda-codec: out of range cmd 3:0:3949:f00:5
[   10.283483] hda-codec: out of range cmd 3:0:394a:f00:5
[   10.283486] hda-codec: out of range cmd 3:0:394b:f00:5
[   10.283489] hda-codec: out of range cmd 3:0:394c:f00:5
[   10.283492] hda-codec: out of range cmd 3:0:394d:f00:5
[   10.283494] hda-codec: out of range cmd 3:0:394e:f00:5
[   10.283498] hda-codec: out of range cmd 3:0:394f:f00:5
[   10.283502] hda-codec: out of range cmd 3:0:3950:f00:5
[   10.283506] hda-codec: out of range cmd 3:0:3951:f00:5
[   10.283508] hda-codec: out of range cmd 3:0:3952:f00:5
[   10.283511] hda-codec: out of range cmd 3:0:3953:f00:5
[   10.283513] hda-codec: out of range cmd 3:0:3954:f00:5
[   10.283517] hda-codec: out of range cmd 3:0:3955:f00:5
[   10.283521] hda-codec: out of range cmd 3:0:3956:f00:5
[   10.283523] hda-codec: out of range cmd 3:0:3957:f00:5
[   10.283527] hda-codec: out of range cmd 3:0:3958:f00:5
[   10.283531] hda-codec: out of range cmd 3:0:3959:f00:5
[   10.283535] hda-codec: out of range cmd 3:0:395a:f00:5
[   10.283539] hda-codec: out of range cmd 3:0:395b:f00:5
[   10.283541] hda-codec: out of range cmd 3:0:395c:f00:5
[   10.283544] hda-codec: out of range cmd 3:0:395d:f00:5
[   10.283546] hda-codec: out of range cmd 3:0:395e:f00:5
[   10.283548] hda-codec: out of range cmd 3:0:395f:f00:5
[   10.283550] hda-codec: out of range cmd 3:0:3960:f00:5
[   10.283553] hda-codec: out of range cmd 3:0:3961:f00:5
[   10.283557] hda-codec: out of range cmd 3:0:3962:f00:5
[   10.283560] hda-codec: out of range cmd 3:0:3963:f00:5
[   10.283563] hda-codec: out of range cmd 3:0:3964:f00:5
[   10.283566] hda-codec: out of range cmd 3:0:3965:f00:5
[   10.283568] hda-codec: out of range cmd 3:0:3966:f00:5
[   10.283571] hda-codec: out of range cmd 3:0:3967:f00:5
[   10.283577] hda-codec: out of range cmd 3:0:3968:f00:5
[   10.283579] hda-codec: out of range cmd 3:0:3969:f00:5
[   10.283582] hda-codec: out of range cmd 3:0:396a:f00:5
[   10.283584] hda-codec: out of range cmd 3:0:396b:f00:5
[   10.283587] hda-codec: out of range cmd 3:0:396c:f00:5
[   10.283591] hda-codec: out of range cmd 3:0:396d:f00:5
[   10.283594] hda-codec: out of range cmd 3:0:396e:f00:5
[   10.283597] hda-codec: out of range cmd 3:0:396f:f00:5
[   10.283599] hda-codec: out of range cmd 3:0:3970:f00:5
[   10.283602] hda-codec: out of range cmd 3:0:3971:f00:5
[   10.283605] hda-codec: out of range cmd 3:0:3972:f00:5
[   10.283607] hda-codec: out of range cmd 3:0:3973:f00:5
[   10.283610] hda-codec: out of range cmd 3:0:3974:f00:5
[   10.283612] hda-codec: out of range cmd 3:0:3975:f00:5
[   10.283614] hda-codec: out of range cmd 3:0:3976:f00:5
[   10.283617] hda-codec: out of range cmd 3:0:3977:f00:5
[   10.283619] hda-codec: out of range cmd 3:0:3978:f00:5
[   10.283622] hda-codec: out of range cmd 3:0:3979:f00:5
[   10.283625] hda-codec: out of range cmd 3:0:397a:f00:5
[   10.283627] hda-codec: out of range cmd 3:0:397b:f00:5
[   10.283630] hda-codec: out of range cmd 3:0:397c:f00:5
[   10.283636] hda-codec: out of range cmd 3:0:397d:f00:5
[   10.283638] hda-codec: out of range cmd 3:0:397e:f00:5
[   10.283641] hda-codec: out of range cmd 3:0:397f:f00:5
[   10.283643] hda-codec: out of range cmd 3:0:3980:f00:5
[   10.283647] hda-codec: out of range cmd 3:0:3981:f00:5
[   10.283654] hda-codec: out of range cmd 3:0:3982:f00:5
[   10.283656] hda-codec: out of range cmd 3:0:3983:f00:5
[   10.283659] hda-codec: out of range cmd 3:0:3984:f00:5
[   10.283661] hda-codec: out of range cmd 3:0:3985:f00:5
[   10.283664] hda-codec: out of range cmd 3:0:3986:f00:5
[   10.283666] hda-codec: out of range cmd 3:0:3987:f00:5
[   10.283669] hda-codec: out of range cmd 3:0:3988:f00:5
[   10.283671] hda-codec: out of range cmd 3:0:3989:f00:5
[   10.283673] hda-codec: out of range cmd 3:0:398a:f00:5
[   10.283677] hda-codec: out of range cmd 3:0:398b:f00:5
[   10.283681] hda-codec: out of range cmd 3:0:398c:f00:5
[   10.283684] hda-codec: out of range cmd 3:0:398d:f00:5
[   10.283686] hda-codec: out of range cmd 3:0:398e:f00:5
[   10.283688] hda-codec: out of range cmd 3:0:398f:f00:5
[   10.283691] hda-codec: out of range cmd 3:0:3990:f00:5
[   10.283694] hda-codec: out of range cmd 3:0:3991:f00:5
[   10.283697] hda-codec: out of range cmd 3:0:3992:f00:5
[   10.283700] hda-codec: out of range cmd 3:0:3993:f00:5
[   10.283702] hda-codec: out of range cmd 3:0:3994:f00:5
[   10.283706] hda-codec: out of range cmd 3:0:3995:f00:5
[   10.283712] hda-codec: out of range cmd 3:0:3996:f00:5
[   10.283714] hda-codec: out of range cmd 3:0:3997:f00:5
[   10.283717] hda-codec: out of range cmd 3:0:3998:f00:5
[   10.283719] hda-codec: out of range cmd 3:0:3999:f00:5
[   10.283722] hda-codec: out of range cmd 3:0:399a:f00:5
[   10.283725] hda-codec: out of range cmd 3:0:399b:f00:5
[   10.283730] hda-codec: out of range cmd 3:0:399c:f00:5
[   10.283734] hda-codec: out of range cmd 3:0:399d:f00:5
[   10.283737] hda-codec: out of range cmd 3:0:399e:f00:5
[   10.283739] hda-codec: out of range cmd 3:0:399f:f00:5
[   10.283742] hda-codec: out of range cmd 3:0:39a0:f00:5
[   10.283745] hda-codec: out of range cmd 3:0:39a1:f00:5
[   10.283748] hda-codec: out of range cmd 3:0:39a2:f00:5
[   10.283751] hda-codec: out of range cmd 3:0:39a3:f00:5
[   10.283754] hda-codec: out of range cmd 3:0:39a4:f00:5
[   10.283757] hda-codec: out of range cmd 3:0:39a5:f00:5
[   10.283760] hda-codec: out of range cmd 3:0:39a6:f00:5
[   10.283763] hda-codec: out of range cmd 3:0:39a7:f00:5
[   10.283766] hda-codec: out of range cmd 3:0:39a8:f00:5
[   10.283769] hda-codec: out of range cmd 3:0:39a9:f00:5
[   10.283772] hda-codec: out of range cmd 3:0:39aa:f00:5
[   10.283774] hda-codec: out of range cmd 3:0:39ab:f00:5
[   10.283777] hda-codec: out of range cmd 3:0:39ac:f00:5
[   10.283780] hda-codec: out of range cmd 3:0:39ad:f00:5
[   10.283783] hda-codec: out of range cmd 3:0:39ae:f00:5
[   10.283786] hda-codec: out of range cmd 3:0:39af:f00:5
[   10.283789] hda-codec: out of range cmd 3:0:39b0:f00:5
[   10.283792] hda-codec: out of range cmd 3:0:39b1:f00:5
[   10.283796] hda-codec: out of range cmd 3:0:39b2:f00:5
[   10.283800] hda-codec: out of range cmd 3:0:39b3:f00:5
[   10.283803] hda-codec: out of range cmd 3:0:39b4:f00:5
[   10.283805] hda-codec: out of range cmd 3:0:39b5:f00:5
[   10.283808] hda-codec: out of range cmd 3:0:39b6:f00:5
[   10.283812] hda-codec: out of range cmd 3:0:39b7:f00:5
[   10.283815] hda-codec: out of range cmd 3:0:39b8:f00:5
[   10.283818] hda-codec: out of range cmd 3:0:39b9:f00:5
[   10.283820] hda-codec: out of range cmd 3:0:39ba:f00:5
[   10.283823] hda-codec: out of range cmd 3:0:39bb:f00:5
[   10.283825] hda-codec: out of range cmd 3:0:39bc:f00:5
[   10.283828] hda-codec: out of range cmd 3:0:39bd:f00:5
[   10.283831] hda-codec: out of range cmd 3:0:39be:f00:5
[   10.283834] hda-codec: out of range cmd 3:0:39bf:f00:5
[   10.283837] hda-codec: out of range cmd 3:0:39c0:f00:5
[   10.283839] hda-codec: out of range cmd 3:0:39c1:f00:5
[   10.283842] hda-codec: out of range cmd 3:0:39c2:f00:5
[   10.283845] hda-codec: out of range cmd 3:0:39c3:f00:5
[   10.283848] hda-codec: out of range cmd 3:0:39c4:f00:5
[   10.283852] hda-codec: out of range cmd 3:0:39c5:f00:5
[   10.283859] hda-codec: out of range cmd 3:0:39c6:f00:5
[   10.283861] hda-codec: out of range cmd 3:0:39c7:f00:5
[   10.283863] hda-codec: out of range cmd 3:0:39c8:f00:5
[   10.283865] hda-codec: out of range cmd 3:0:39c9:f00:5
[   10.283867] hda-codec: out of range cmd 3:0:39ca:f00:5
[   10.283869] hda-codec: out of range cmd 3:0:39cb:f00:5
[   10.283872] hda-codec: out of range cmd 3:0:39cc:f00:5
[   10.283874] hda-codec: out of range cmd 3:0:39cd:f00:5
[   10.283877] hda-codec: out of range cmd 3:0:39ce:f00:5
[   10.283879] hda-codec: out of range cmd 3:0:39cf:f00:5
[   10.283881] hda-codec: out of range cmd 3:0:39d0:f00:5
[   10.283883] hda-codec: out of range cmd 3:0:39d1:f00:5
[   10.283885] hda-codec: out of range cmd 3:0:39d2:f00:5
[   10.283888] hda-codec: out of range cmd 3:0:39d3:f00:5
[   10.283890] hda-codec: out of range cmd 3:0:39d4:f00:5
[   10.283892] hda-codec: out of range cmd 3:0:39d5:f00:5
[   10.283894] hda-codec: out of range cmd 3:0:39d6:f00:5
[   10.283897] hda-codec: out of range cmd 3:0:39d7:f00:5
[   10.283899] hda-codec: out of range cmd 3:0:39d8:f00:5
[   10.283901] hda-codec: out of range cmd 3:0:39d9:f00:5
[   10.283903] hda-codec: out of range cmd 3:0:39da:f00:5
[   10.283905] hda-codec: out of range cmd 3:0:39db:f00:5
[   10.283907] hda-codec: out of range cmd 3:0:39dc:f00:5
[   10.283909] hda-codec: out of range cmd 3:0:39dd:f00:5
[   10.283911] hda-codec: out of range cmd 3:0:39de:f00:5
[   10.283914] hda-codec: out of range cmd 3:0:39df:f00:5
[   10.283916] hda-codec: out of range cmd 3:0:39e0:f00:5
[   10.283918] hda-codec: out of range cmd 3:0:39e1:f00:5
[   10.283920] hda-codec: out of range cmd 3:0:39e2:f00:5
[   10.283922] hda-codec: out of range cmd 3:0:39e3:f00:5
[   10.283924] hda-codec: out of range cmd 3:0:39e4:f00:5
[   10.283927] hda-codec: out of range cmd 3:0:39e5:f00:5
[   10.283929] hda-codec: out of range cmd 3:0:39e6:f00:5
[   10.283932] hda-codec: out of range cmd 3:0:39e7:f00:5
[   10.283935] hda-codec: out of range cmd 3:0:39e8:f00:5
[   10.283938] hda-codec: out of range cmd 3:0:39e9:f00:5
[   10.283942] hda-codec: out of range cmd 3:0:39ea:f00:5
[   10.283944] hda-codec: out of range cmd 3:0:39eb:f00:5
[   10.283949] hda-codec: out of range cmd 3:0:39ec:f00:5
[   10.283952] hda-codec: out of range cmd 3:0:39ed:f00:5
[   10.283954] hda-codec: out of range cmd 3:0:39ee:f00:5
[   10.283956] hda-codec: out of range cmd 3:0:39ef:f00:5
[   10.283960] hda-codec: out of range cmd 3:0:39f0:f00:5
[   10.283963] hda-codec: out of range cmd 3:0:39f1:f00:5
[   10.283965] hda-codec: out of range cmd 3:0:39f2:f00:5
[   10.283968] hda-codec: out of range cmd 3:0:39f3:f00:5
[   10.283970] hda-codec: out of range cmd 3:0:39f4:f00:5
[   10.283973] hda-codec: out of range cmd 3:0:39f5:f00:5
[   10.283975] hda-codec: out of range cmd 3:0:39f6:f00:5
[   10.283978] hda-codec: out of range cmd 3:0:39f7:f00:5
[   10.283980] hda-codec: out of range cmd 3:0:39f8:f00:5
[   10.283983] hda-codec: out of range cmd 3:0:39f9:f00:5
[   10.283986] hda-codec: out of range cmd 3:0:39fa:f00:5
[   10.283990] hda-codec: out of range cmd 3:0:39fb:f00:5
[   10.284017] hda-codec: out of range cmd 3:0:39fc:f00:5
[   10.284020] hda-codec: out of range cmd 3:0:39fd:f00:5
[   10.284023] hda-codec: out of range cmd 3:0:39fe:f00:5
[   10.284025] hda-codec: out of range cmd 3:0:39ff:f00:5
[   10.284027] hda-codec: out of range cmd 3:0:3a00:f00:5
[   10.284029] hda-codec: out of range cmd 3:0:3a01:f00:5
[   10.284031] hda-codec: out of range cmd 3:0:3a02:f00:5
[   10.284034] hda-codec: out of range cmd 3:0:3a03:f00:5
[   10.284037] hda-codec: out of range cmd 3:0:3a04:f00:5
[   10.284040] hda-codec: out of range cmd 3:0:3a05:f00:5
[   10.284043] hda-codec: out of range cmd 3:0:3a06:f00:5
[   10.284047] hda-codec: out of range cmd 3:0:3a07:f00:5
[   10.284050] hda-codec: out of range cmd 3:0:3a08:f00:5
[   10.284052] hda-codec: out of range cmd 3:0:3a09:f00:5
[   10.284054] hda-codec: out of range cmd 3:0:3a0a:f00:5
[   10.284057] hda-codec: out of range cmd 3:0:3a0b:f00:5
[   10.284060] hda-codec: out of range cmd 3:0:3a0c:f00:5
[   10.284063] hda-codec: out of range cmd 3:0:3a0d:f00:5
[   10.284066] hda-codec: out of range cmd 3:0:3a0e:f00:5
[   10.284068] hda-codec: out of range cmd 3:0:3a0f:f00:5
[   10.284071] hda-codec: out of range cmd 3:0:3a10:f00:5
[   10.284075] hda-codec: out of range cmd 3:0:3a11:f00:5
[   10.284078] hda-codec: out of range cmd 3:0:3a12:f00:5
[   10.284081] hda-codec: out of range cmd 3:0:3a13:f00:5
[   10.284084] hda-codec: out of range cmd 3:0:3a14:f00:5
[   10.284087] hda-codec: out of range cmd 3:0:3a15:f00:5
[   10.284091] hda-codec: out of range cmd 3:0:3a16:f00:5
[   10.284095] hda-codec: out of range cmd 3:0:3a17:f00:5
[   10.284101] hda-codec: out of range cmd 3:0:3a18:f00:5
[   10.284103] hda-codec: out of range cmd 3:0:3a19:f00:5
[   10.284107] hda-codec: out of range cmd 3:0:3a1a:f00:5
[   10.284110] hda-codec: out of range cmd 3:0:3a1b:f00:5
[   10.284112] hda-codec: out of range cmd 3:0:3a1c:f00:5
[   10.284115] hda-codec: out of range cmd 3:0:3a1d:f00:5
[   10.284117] hda-codec: out of range cmd 3:0:3a1e:f00:5
[   10.284120] hda-codec: out of range cmd 3:0:3a1f:f00:5
[   10.284122] hda-codec: out of range cmd 3:0:3a20:f00:5
[   10.284125] hda-codec: out of range cmd 3:0:3a21:f00:5
[   10.284127] hda-codec: out of range cmd 3:0:3a22:f00:5
[   10.284129] hda-codec: out of range cmd 3:0:3a23:f00:5
[   10.284132] hda-codec: out of range cmd 3:0:3a24:f00:5
[   10.284137] hda-codec: out of range cmd 3:0:3a25:f00:5
[   10.284139] hda-codec: out of range cmd 3:0:3a26:f00:5
[   10.284142] hda-codec: out of range cmd 3:0:3a27:f00:5
[   10.284144] hda-codec: out of range cmd 3:0:3a28:f00:5
[   10.284147] hda-codec: out of range cmd 3:0:3a29:f00:5
[   10.284150] hda-codec: out of range cmd 3:0:3a2a:f00:5
[   10.284152] hda-codec: out of range cmd 3:0:3a2b:f00:5
[   10.284155] hda-codec: out of range cmd 3:0:3a2c:f00:5
[   10.284157] hda-codec: out of range cmd 3:0:3a2d:f00:5
[   10.284160] hda-codec: out of range cmd 3:0:3a2e:f00:5
[   10.284162] hda-codec: out of range cmd 3:0:3a2f:f00:5
[   10.284164] hda-codec: out of range cmd 3:0:3a30:f00:5
[   10.284168] hda-codec: out of range cmd 3:0:3a31:f00:5
[   10.284171] hda-codec: out of range cmd 3:0:3a32:f00:5
[   10.284173] hda-codec: out of range cmd 3:0:3a33:f00:5
[   10.284177] hda-codec: out of range cmd 3:0:3a34:f00:5
[   10.284181] hda-codec: out of range cmd 3:0:3a35:f00:5
[   10.284185] hda-codec: out of range cmd 3:0:3a36:f00:5
[   10.284188] hda-codec: out of range cmd 3:0:3a37:f00:5
[   10.284191] hda-codec: out of range cmd 3:0:3a38:f00:5
[   10.284194] hda-codec: out of range cmd 3:0:3a39:f00:5
[   10.284197] hda-codec: out of range cmd 3:0:3a3a:f00:5
[   10.284199] hda-codec: out of range cmd 3:0:3a3b:f00:5
[   10.284201] hda-codec: out of range cmd 3:0:3a3c:f00:5
[   10.284204] hda-codec: out of range cmd 3:0:3a3d:f00:5
[   10.284209] hda-codec: out of range cmd 3:0:3a3e:f00:5
[   10.284211] hda-codec: out of range cmd 3:0:3a3f:f00:5
[   10.284215] hda-codec: out of range cmd 3:0:3a40:f00:5
[   10.284217] hda-codec: out of range cmd 3:0:3a41:f00:5
[   10.284219] hda-codec: out of range cmd 3:0:3a42:f00:5
[   10.284222] hda-codec: out of range cmd 3:0:3a43:f00:5
[   10.284224] hda-codec: out of range cmd 3:0:3a44:f00:5
[   10.284226] hda-codec: out of range cmd 3:0:3a45:f00:5
[   10.284228] hda-codec: out of range cmd 3:0:3a46:f00:5
[   10.284232] hda-codec: out of range cmd 3:0:3a47:f00:5
[   10.284235] hda-codec: out of range cmd 3:0:3a48:f00:5
[   10.284238] hda-codec: out of range cmd 3:0:3a49:f00:5
[   10.284240] hda-codec: out of range cmd 3:0:3a4a:f00:5
[   10.284242] hda-codec: out of range cmd 3:0:3a4b:f00:5
[   10.284247] hda-codec: out of range cmd 3:0:3a4c:f00:5
[   10.284251] hda-codec: out of range cmd 3:0:3a4d:f00:5
[   10.284255] hda-codec: out of range cmd 3:0:3a4e:f00:5
[   10.284259] hda-codec: out of range cmd 3:0:3a4f:f00:5
[   10.284261] hda-codec: out of range cmd 3:0:3a50:f00:5
[   10.284265] hda-codec: out of range cmd 3:0:3a51:f00:5
[   10.284268] hda-codec: out of range cmd 3:0:3a52:f00:5
[   10.284272] hda-codec: out of range cmd 3:0:3a53:f00:5
[   10.284275] hda-codec: out of range cmd 3:0:3a54:f00:5
[   10.284277] hda-codec: out of range cmd 3:0:3a55:f00:5
[   10.284279] hda-codec: out of range cmd 3:0:3a56:f00:5
[   10.284283] hda-codec: out of range cmd 3:0:3a57:f00:5
[   10.284286] hda-codec: out of range cmd 3:0:3a58:f00:5
[   10.284289] hda-codec: out of range cmd 3:0:3a59:f00:5
[   10.284291] hda-codec: out of range cmd 3:0:3a5a:f00:5
[   10.284294] hda-codec: out of range cmd 3:0:3a5b:f00:5
[   10.284297] hda-codec: out of range cmd 3:0:3a5c:f00:5
[   10.284301] hda-codec: out of range cmd 3:0:3a5d:f00:5
[   10.284303] hda-codec: out of range cmd 3:0:3a5e:f00:5
[   10.284305] hda-codec: out of range cmd 3:0:3a5f:f00:5
[   10.284308] hda-codec: out of range cmd 3:0:3a60:f00:5
[   10.284311] hda-codec: out of range cmd 3:0:3a61:f00:5
[   10.284315] hda-codec: out of range cmd 3:0:3a62:f00:5
[   10.284318] hda-codec: out of range cmd 3:0:3a63:f00:5
[   10.284320] hda-codec: out of range cmd 3:0:3a64:f00:5
[   10.284322] hda-codec: out of range cmd 3:0:3a65:f00:5
[   10.284325] hda-codec: out of range cmd 3:0:3a66:f00:5
[   10.284329] hda-codec: out of range cmd 3:0:3a67:f00:5
[   10.284332] hda-codec: out of range cmd 3:0:3a68:f00:5
[   10.284335] hda-codec: out of range cmd 3:0:3a69:f00:5
[   10.284338] hda-codec: out of range cmd 3:0:3a6a:f00:5
[   10.284340] hda-codec: out of range cmd 3:0:3a6b:f00:5
[   10.284344] hda-codec: out of range cmd 3:0:3a6c:f00:5
[   10.284347] hda-codec: out of range cmd 3:0:3a6d:f00:5
[   10.284351] hda-codec: out of range cmd 3:0:3a6e:f00:5
[   10.284354] hda-codec: out of range cmd 3:0:3a6f:f00:5
[   10.284356] hda-codec: out of range cmd 3:0:3a70:f00:5
[   10.284358] hda-codec: out of range cmd 3:0:3a71:f00:5
[   10.284361] hda-codec: out of range cmd 3:0:3a72:f00:5
[   10.284363] hda-codec: out of range cmd 3:0:3a73:f00:5
[   10.284366] hda-codec: out of range cmd 3:0:3a74:f00:5
[   10.284369] hda-codec: out of range cmd 3:0:3a75:f00:5
[   10.284371] hda-codec: out of range cmd 3:0:3a76:f00:5
[   10.284374] hda-codec: out of range cmd 3:0:3a77:f00:5
[   10.284378] hda-codec: out of range cmd 3:0:3a78:f00:5
[   10.284381] hda-codec: out of range cmd 3:0:3a79:f00:5
[   10.284383] hda-codec: out of range cmd 3:0:3a7a:f00:5
[   10.284387] hda-codec: out of range cmd 3:0:3a7b:f00:5
[   10.284389] hda-codec: out of range cmd 3:0:3a7c:f00:5
[   10.284393] hda-codec: out of range cmd 3:0:3a7d:f00:5
[   10.284397] hda-codec: out of range cmd 3:0:3a7e:f00:5
[   10.284400] hda-codec: out of range cmd 3:0:3a7f:f00:5
[   10.284402] hda-codec: out of range cmd 3:0:3a80:f00:5
[   10.284404] hda-codec: out of range cmd 3:0:3a81:f00:5
[   10.284408] hda-codec: out of range cmd 3:0:3a82:f00:5
[   10.284411] hda-codec: out of range cmd 3:0:3a83:f00:5
[   10.284415] hda-codec: out of range cmd 3:0:3a84:f00:5
[   10.284417] hda-codec: out of range cmd 3:0:3a85:f00:5
[   10.284420] hda-codec: out of range cmd 3:0:3a86:f00:5
[   10.284423] hda-codec: out of range cmd 3:0:3a87:f00:5
[   10.284428] hda-codec: out of range cmd 3:0:3a88:f00:5
[   10.284431] hda-codec: out of range cmd 3:0:3a89:f00:5
[   10.284435] hda-codec: out of range cmd 3:0:3a8a:f00:5
[   10.284439] hda-codec: out of range cmd 3:0:3a8b:f00:5
[   10.284442] hda-codec: out of range cmd 3:0:3a8c:f00:5
[   10.284447] hda-codec: out of range cmd 3:0:3a8d:f00:5
[   10.284449] hda-codec: out of range cmd 3:0:3a8e:f00:5
[   10.284451] hda-codec: out of range cmd 3:0:3a8f:f00:5
[   10.284454] hda-codec: out of range cmd 3:0:3a90:f00:5
[   10.284456] hda-codec: out of range cmd 3:0:3a91:f00:5
[   10.284458] hda-codec: out of range cmd 3:0:3a92:f00:5
[   10.284460] hda-codec: out of range cmd 3:0:3a93:f00:5
[   10.284463] hda-codec: out of range cmd 3:0:3a94:f00:5
[   10.284468] hda-codec: out of range cmd 3:0:3a95:f00:5
[   10.284471] hda-codec: out of range cmd 3:0:3a96:f00:5
[   10.284474] hda-codec: out of range cmd 3:0:3a97:f00:5
[   10.284476] hda-codec: out of range cmd 3:0:3a98:f00:5
[   10.284479] hda-codec: out of range cmd 3:0:3a99:f00:5
[   10.284485] hda-codec: out of range cmd 3:0:3a9a:f00:5
[   10.284488] hda-codec: out of range cmd 3:0:3a9b:f00:5
[   10.284490] hda-codec: out of range cmd 3:0:3a9c:f00:5
[   10.284493] hda-codec: out of range cmd 3:0:3a9d:f00:5
[   10.284495] hda-codec: out of range cmd 3:0:3a9e:f00:5
[   10.284499] hda-codec: out of range cmd 3:0:3a9f:f00:5
[   10.284503] hda-codec: out of range cmd 3:0:3aa0:f00:5
[   10.284506] hda-codec: out of range cmd 3:0:3aa1:f00:5
[   10.284509] hda-codec: out of range cmd 3:0:3aa2:f00:5
[   10.284511] hda-codec: out of range cmd 3:0:3aa3:f00:5
[   10.284514] hda-codec: out of range cmd 3:0:3aa4:f00:5
[   10.284516] hda-codec: out of range cmd 3:0:3aa5:f00:5
[   10.284518] hda-codec: out of range cmd 3:0:3aa6:f00:5
[   10.284521] hda-codec: out of range cmd 3:0:3aa7:f00:5
[   10.284523] hda-codec: out of range cmd 3:0:3aa8:f00:5
[   10.284526] hda-codec: out of range cmd 3:0:3aa9:f00:5
[   10.284529] hda-codec: out of range cmd 3:0:3aaa:f00:5
[   10.284532] hda-codec: out of range cmd 3:0:3aab:f00:5
[   10.284535] hda-codec: out of range cmd 3:0:3aac:f00:5
[   10.284538] hda-codec: out of range cmd 3:0:3aad:f00:5
[   10.284540] hda-codec: out of range cmd 3:0:3aae:f00:5
[   10.284544] hda-codec: out of range cmd 3:0:3aaf:f00:5
[   10.284549] hda-codec: out of range cmd 3:0:3ab0:f00:5
[   10.284552] hda-codec: out of range cmd 3:0:3ab1:f00:5
[   10.284555] hda-codec: out of range cmd 3:0:3ab2:f00:5
[   10.284557] hda-codec: out of range cmd 3:0:3ab3:f00:5
[   10.284560] hda-codec: out of range cmd 3:0:3ab4:f00:5
[   10.284566] hda-codec: out of range cmd 3:0:3ab5:f00:5
[   10.284569] hda-codec: out of range cmd 3:0:3ab6:f00:5
[   10.284572] hda-codec: out of range cmd 3:0:3ab7:f00:5
[   10.284574] hda-codec: out of range cmd 3:0:3ab8:f00:5
[   10.284576] hda-codec: out of range cmd 3:0:3ab9:f00:5
[   10.284579] hda-codec: out of range cmd 3:0:3aba:f00:5
[   10.284582] hda-codec: out of range cmd 3:0:3abb:f00:5
[   10.284585] hda-codec: out of range cmd 3:0:3abc:f00:5
[   10.284587] hda-codec: out of range cmd 3:0:3abd:f00:5
[   10.284590] hda-codec: out of range cmd 3:0:3abe:f00:5
[   10.284593] hda-codec: out of range cmd 3:0:3abf:f00:5
[   10.284596] hda-codec: out of range cmd 3:0:3ac0:f00:5
[   10.284598] hda-codec: out of range cmd 3:0:3ac1:f00:5
[   10.284601] hda-codec: out of range cmd 3:0:3ac2:f00:5
[   10.284603] hda-codec: out of range cmd 3:0:3ac3:f00:5
[   10.284606] hda-codec: out of range cmd 3:0:3ac4:f00:5
[   10.284609] hda-codec: out of range cmd 3:0:3ac5:f00:5
[   10.284611] hda-codec: out of range cmd 3:0:3ac6:f00:5
[   10.284614] hda-codec: out of range cmd 3:0:3ac7:f00:5
[   10.284616] hda-codec: out of range cmd 3:0:3ac8:f00:5
[   10.284622] hda-codec: out of range cmd 3:0:3ac9:f00:5
[   10.284626] hda-codec: out of range cmd 3:0:3aca:f00:5
[   10.284628] hda-codec: out of range cmd 3:0:3acb:f00:5
[   10.284631] hda-codec: out of range cmd 3:0:3acc:f00:5
[   10.284633] hda-codec: out of range cmd 3:0:3acd:f00:5
[   10.284636] hda-codec: out of range cmd 3:0:3ace:f00:5
[   10.284639] hda-codec: out of range cmd 3:0:3acf:f00:5
[   10.284642] hda-codec: out of range cmd 3:0:3ad0:f00:5
[   10.284647] hda-codec: out of range cmd 3:0:3ad1:f00:5
[   10.284651] hda-codec: out of range cmd 3:0:3ad2:f00:5
[   10.284653] hda-codec: out of range cmd 3:0:3ad3:f00:5
[   10.284656] hda-codec: out of range cmd 3:0:3ad4:f00:5
[   10.284660] hda-codec: out of range cmd 3:0:3ad5:f00:5
[   10.284663] hda-codec: out of range cmd 3:0:3ad6:f00:5
[   10.284666] hda-codec: out of range cmd 3:0:3ad7:f00:5
[   10.284668] hda-codec: out of range cmd 3:0:3ad8:f00:5
[   10.284671] hda-codec: out of range cmd 3:0:3ad9:f00:5
[   10.284675] hda-codec: out of range cmd 3:0:3ada:f00:5
[   10.284678] hda-codec: out of range cmd 3:0:3adb:f00:5
[   10.284681] hda-codec: out of range cmd 3:0:3adc:f00:5
[   10.284683] hda-codec: out of range cmd 3:0:3add:f00:5
[   10.284686] hda-codec: out of range cmd 3:0:3ade:f00:5
[   10.284689] hda-codec: out of range cmd 3:0:3adf:f00:5
[   10.284692] hda-codec: out of range cmd 3:0:3ae0:f00:5
[   10.284695] hda-codec: out of range cmd 3:0:3ae1:f00:5
[   10.284698] hda-codec: out of range cmd 3:0:3ae2:f00:5
[   10.284701] hda-codec: out of range cmd 3:0:3ae3:f00:5
[   10.284703] hda-codec: out of range cmd 3:0:3ae4:f00:5
[   10.284706] hda-codec: out of range cmd 3:0:3ae5:f00:5
[   10.284709] hda-codec: out of range cmd 3:0:3ae6:f00:5
[   10.284712] hda-codec: out of range cmd 3:0:3ae7:f00:5
[   10.284714] hda-codec: out of range cmd 3:0:3ae8:f00:5
[   10.284718] hda-codec: out of range cmd 3:0:3ae9:f00:5
[   10.284721] hda-codec: out of range cmd 3:0:3aea:f00:5
[   10.284724] hda-codec: out of range cmd 3:0:3aeb:f00:5
[   10.284727] hda-codec: out of range cmd 3:0:3aec:f00:5
[   10.284730] hda-codec: out of range cmd 3:0:3aed:f00:5
[   10.284734] hda-codec: out of range cmd 3:0:3aee:f00:5
[   10.284737] hda-codec: out of range cmd 3:0:3aef:f00:5
[   10.284740] hda-codec: out of range cmd 3:0:3af0:f00:5
[   10.284743] hda-codec: out of range cmd 3:0:3af1:f00:5
[   10.284746] hda-codec: out of range cmd 3:0:3af2:f00:5
[   10.284748] hda-codec: out of range cmd 3:0:3af3:f00:5
[   10.284752] hda-codec: out of range cmd 3:0:3af4:f00:5
[   10.284756] hda-codec: out of range cmd 3:0:3af5:f00:5
[   10.284759] hda-codec: out of range cmd 3:0:3af6:f00:5
[   10.284763] hda-codec: out of range cmd 3:0:3af7:f00:5
[   10.284765] hda-codec: out of range cmd 3:0:3af8:f00:5
[   10.284768] hda-codec: out of range cmd 3:0:3af9:f00:5
[   10.284771] hda-codec: out of range cmd 3:0:3afa:f00:5
[   10.284775] hda-codec: out of range cmd 3:0:3afb:f00:5
[   10.284778] hda-codec: out of range cmd 3:0:3afc:f00:5
[   10.284781] hda-codec: out of range cmd 3:0:3afd:f00:5
[   10.284784] hda-codec: out of range cmd 3:0:3afe:f00:5
[   10.284786] hda-codec: out of range cmd 3:0:3aff:f00:5
[   10.284788] hda-codec: out of range cmd 3:0:3b00:f00:5
[   10.284793] hda-codec: out of range cmd 3:0:3b01:f00:5
[   10.284796] hda-codec: out of range cmd 3:0:3b02:f00:5
[   10.284798] hda-codec: out of range cmd 3:0:3b03:f00:5
[   10.284800] hda-codec: out of range cmd 3:0:3b04:f00:5
[   10.284802] hda-codec: out of range cmd 3:0:3b05:f00:5
[   10.284804] hda-codec: out of range cmd 3:0:3b06:f00:5
[   10.284806] hda-codec: out of range cmd 3:0:3b07:f00:5
[   10.284808] hda-codec: out of range cmd 3:0:3b08:f00:5
[   10.284810] hda-codec: out of range cmd 3:0:3b09:f00:5
[   10.284812] hda-codec: out of range cmd 3:0:3b0a:f00:5
[   10.284815] hda-codec: out of range cmd 3:0:3b0b:f00:5
[   10.284817] hda-codec: out of range cmd 3:0:3b0c:f00:5
[   10.284820] hda-codec: out of range cmd 3:0:3b0d:f00:5
[   10.284824] hda-codec: out of range cmd 3:0:3b0e:f00:5
[   10.284826] hda-codec: out of range cmd 3:0:3b0f:f00:5
[   10.284828] hda-codec: out of range cmd 3:0:3b10:f00:5
[   10.284830] hda-codec: out of range cmd 3:0:3b11:f00:5
[   10.284832] hda-codec: out of range cmd 3:0:3b12:f00:5
[   10.284834] hda-codec: out of range cmd 3:0:3b13:f00:5
[   10.284836] hda-codec: out of range cmd 3:0:3b14:f00:5
[   10.284840] hda-codec: out of range cmd 3:0:3b15:f00:5
[   10.284842] hda-codec: out of range cmd 3:0:3b16:f00:5
[   10.284844] hda-codec: out of range cmd 3:0:3b17:f00:5
[   10.284846] hda-codec: out of range cmd 3:0:3b18:f00:5
[   10.284848] hda-codec: out of range cmd 3:0:3b19:f00:5
[   10.284851] hda-codec: out of range cmd 3:0:3b1a:f00:5
[   10.284853] hda-codec: out of range cmd 3:0:3b1b:f00:5
[   10.284856] hda-codec: out of range cmd 3:0:3b1c:f00:5
[   10.284857] hda-codec: out of range cmd 3:0:3b1d:f00:5
[   10.284860] hda-codec: out of range cmd 3:0:3b1e:f00:5
[   10.284862] hda-codec: out of range cmd 3:0:3b1f:f00:5
[   10.284864] hda-codec: out of range cmd 3:0:3b20:f00:5
[   10.284866] hda-codec: out of range cmd 3:0:3b21:f00:5
[   10.284869] hda-codec: out of range cmd 3:0:3b22:f00:5
[   10.284875] hda-codec: out of range cmd 3:0:3b23:f00:5
[   10.284878] hda-codec: out of range cmd 3:0:3b24:f00:5
[   10.284881] hda-codec: out of range cmd 3:0:3b25:f00:5
[   10.284883] hda-codec: out of range cmd 3:0:3b26:f00:5
[   10.284886] hda-codec: out of range cmd 3:0:3b27:f00:5
[   10.284891] hda-codec: out of range cmd 3:0:3b28:f00:5
[   10.284893] hda-codec: out of range cmd 3:0:3b29:f00:5
[   10.284895] hda-codec: out of range cmd 3:0:3b2a:f00:5
[   10.284898] hda-codec: out of range cmd 3:0:3b2b:f00:5
[   10.284900] hda-codec: out of range cmd 3:0:3b2c:f00:5
[   10.284902] hda-codec: out of range cmd 3:0:3b2d:f00:5
[   10.284905] hda-codec: out of range cmd 3:0:3b2e:f00:5
[   10.284907] hda-codec: out of range cmd 3:0:3b2f:f00:5
[   10.284911] hda-codec: out of range cmd 3:0:3b30:f00:5
[   10.284914] hda-codec: out of range cmd 3:0:3b31:f00:5
[   10.284920] hda-codec: out of range cmd 3:0:3b32:f00:5
[   10.284924] hda-codec: out of range cmd 3:0:3b33:f00:5
[   10.284927] hda-codec: out of range cmd 3:0:3b34:f00:5
[   10.284931] hda-codec: out of range cmd 3:0:3b35:f00:5
[   10.284934] hda-codec: out of range cmd 3:0:3b36:f00:5
[   10.284937] hda-codec: out of range cmd 3:0:3b37:f00:5
[   10.284940] hda-codec: out of range cmd 3:0:3b38:f00:5
[   10.284942] hda-codec: out of range cmd 3:0:3b39:f00:5
[   10.284944] hda-codec: out of range cmd 3:0:3b3a:f00:5
[   10.284946] hda-codec: out of range cmd 3:0:3b3b:f00:5
[   10.284950] hda-codec: out of range cmd 3:0:3b3c:f00:5
[   10.284952] hda-codec: out of range cmd 3:0:3b3d:f00:5
[   10.284955] hda-codec: out of range cmd 3:0:3b3e:f00:5
[   10.284959] hda-codec: out of range cmd 3:0:3b3f:f00:5
[   10.284961] hda-codec: out of range cmd 3:0:3b40:f00:5
[   10.284965] hda-codec: out of range cmd 3:0:3b41:f00:5
[   10.284968] hda-codec: out of range cmd 3:0:3b42:f00:5
[   10.284970] hda-codec: out of range cmd 3:0:3b43:f00:5
[   10.284973] hda-codec: out of range cmd 3:0:3b44:f00:5
[   10.284976] hda-codec: out of range cmd 3:0:3b45:f00:5
[   10.284980] hda-codec: out of range cmd 3:0:3b46:f00:5
[   10.284982] hda-codec: out of range cmd 3:0:3b47:f00:5
[   10.284984] hda-codec: out of range cmd 3:0:3b48:f00:5
[   10.284988] hda-codec: out of range cmd 3:0:3b49:f00:5
[   10.284991] hda-codec: out of range cmd 3:0:3b4a:f00:5
[   10.284994] hda-codec: out of range cmd 3:0:3b4b:f00:5
[   10.284997] hda-codec: out of range cmd 3:0:3b4c:f00:5
[   10.284999] hda-codec: out of range cmd 3:0:3b4d:f00:5
[   10.285002] hda-codec: out of range cmd 3:0:3b4e:f00:5
[   10.285006] hda-codec: out of range cmd 3:0:3b4f:f00:5
[   10.285010] hda-codec: out of range cmd 3:0:3b50:f00:5
[   10.285014] hda-codec: out of range cmd 3:0:3b51:f00:5
[   10.285016] hda-codec: out of range cmd 3:0:3b52:f00:5
[   10.285020] hda-codec: out of range cmd 3:0:3b53:f00:5
[   10.285023] hda-codec: out of range cmd 3:0:3b54:f00:5
[   10.285025] hda-codec: out of range cmd 3:0:3b55:f00:5
[   10.285028] hda-codec: out of range cmd 3:0:3b56:f00:5
[   10.285030] hda-codec: out of range cmd 3:0:3b57:f00:5
[   10.285032] hda-codec: out of range cmd 3:0:3b58:f00:5
[   10.285035] hda-codec: out of range cmd 3:0:3b59:f00:5
[   10.285037] hda-codec: out of range cmd 3:0:3b5a:f00:5
[   10.285040] hda-codec: out of range cmd 3:0:3b5b:f00:5
[   10.285042] hda-codec: out of range cmd 3:0:3b5c:f00:5
[   10.285045] hda-codec: out of range cmd 3:0:3b5d:f00:5
[   10.285048] hda-codec: out of range cmd 3:0:3b5e:f00:5
[   10.285051] hda-codec: out of range cmd 3:0:3b5f:f00:5
[   10.285054] hda-codec: out of range cmd 3:0:3b60:f00:5
[   10.285057] hda-codec: out of range cmd 3:0:3b61:f00:5
[   10.285059] hda-codec: out of range cmd 3:0:3b62:f00:5
[   10.285062] hda-codec: out of range cmd 3:0:3b63:f00:5
[   10.285064] hda-codec: out of range cmd 3:0:3b64:f00:5
[   10.285067] hda-codec: out of range cmd 3:0:3b65:f00:5
[   10.285069] hda-codec: out of range cmd 3:0:3b66:f00:5
[   10.285071] hda-codec: out of range cmd 3:0:3b67:f00:5
[   10.285073] hda-codec: out of range cmd 3:0:3b68:f00:5
[   10.285076] hda-codec: out of range cmd 3:0:3b69:f00:5
[   10.285079] hda-codec: out of range cmd 3:0:3b6a:f00:5
[   10.285082] hda-codec: out of range cmd 3:0:3b6b:f00:5
[   10.285084] hda-codec: out of range cmd 3:0:3b6c:f00:5
[   10.285087] hda-codec: out of range cmd 3:0:3b6d:f00:5
[   10.285091] hda-codec: out of range cmd 3:0:3b6e:f00:5
[   10.285095] hda-codec: out of range cmd 3:0:3b6f:f00:5
[   10.285098] hda-codec: out of range cmd 3:0:3b70:f00:5
[   10.285102] hda-codec: out of range cmd 3:0:3b71:f00:5
[   10.285105] hda-codec: out of range cmd 3:0:3b72:f00:5
[   10.285108] hda-codec: out of range cmd 3:0:3b73:f00:5
[   10.285111] hda-codec: out of range cmd 3:0:3b74:f00:5
[   10.285113] hda-codec: out of range cmd 3:0:3b75:f00:5
[   10.285116] hda-codec: out of range cmd 3:0:3b76:f00:5
[   10.285120] hda-codec: out of range cmd 3:0:3b77:f00:5
[   10.285123] hda-codec: out of range cmd 3:0:3b78:f00:5
[   10.285126] hda-codec: out of range cmd 3:0:3b79:f00:5
[   10.285128] hda-codec: out of range cmd 3:0:3b7a:f00:5
[   10.285130] hda-codec: out of range cmd 3:0:3b7b:f00:5
[   10.285133] hda-codec: out of range cmd 3:0:3b7c:f00:5
[   10.285135] hda-codec: out of range cmd 3:0:3b7d:f00:5
[   10.285138] hda-codec: out of range cmd 3:0:3b7e:f00:5
[   10.285140] hda-codec: out of range cmd 3:0:3b7f:f00:5
[   10.285143] hda-codec: out of range cmd 3:0:3b80:f00:5
[   10.285146] hda-codec: out of range cmd 3:0:3b81:f00:5
[   10.285149] hda-codec: out of range cmd 3:0:3b82:f00:5
[   10.285151] hda-codec: out of range cmd 3:0:3b83:f00:5
[   10.285153] hda-codec: out of range cmd 3:0:3b84:f00:5
[   10.285158] hda-codec: out of range cmd 3:0:3b85:f00:5
[   10.285164] hda-codec: out of range cmd 3:0:3b86:f00:5
[   10.285168] hda-codec: out of range cmd 3:0:3b87:f00:5
[   10.285172] hda-codec: out of range cmd 3:0:3b88:f00:5
[   10.285174] hda-codec: out of range cmd 3:0:3b89:f00:5
[   10.285178] hda-codec: out of range cmd 3:0:3b8a:f00:5
[   10.285182] hda-codec: out of range cmd 3:0:3b8b:f00:5
[   10.285184] hda-codec: out of range cmd 3:0:3b8c:f00:5
[   10.285187] hda-codec: out of range cmd 3:0:3b8d:f00:5
[   10.285189] hda-codec: out of range cmd 3:0:3b8e:f00:5
[   10.285192] hda-codec: out of range cmd 3:0:3b8f:f00:5
[   10.285196] hda-codec: out of range cmd 3:0:3b90:f00:5
[   10.285199] hda-codec: out of range cmd 3:0:3b91:f00:5
[   10.285202] hda-codec: out of range cmd 3:0:3b92:f00:5
[   10.285204] hda-codec: out of range cmd 3:0:3b93:f00:5
[   10.285207] hda-codec: out of range cmd 3:0:3b94:f00:5
[   10.285212] hda-codec: out of range cmd 3:0:3b95:f00:5
[   10.285214] hda-codec: out of range cmd 3:0:3b96:f00:5
[   10.285216] hda-codec: out of range cmd 3:0:3b97:f00:5
[   10.285218] hda-codec: out of range cmd 3:0:3b98:f00:5
[   10.285221] hda-codec: out of range cmd 3:0:3b99:f00:5
[   10.285225] hda-codec: out of range cmd 3:0:3b9a:f00:5
[   10.285227] hda-codec: out of range cmd 3:0:3b9b:f00:5
[   10.285230] hda-codec: out of range cmd 3:0:3b9c:f00:5
[   10.285232] hda-codec: out of range cmd 3:0:3b9d:f00:5
[   10.285235] hda-codec: out of range cmd 3:0:3b9e:f00:5
[   10.285238] hda-codec: out of range cmd 3:0:3b9f:f00:5
[   10.285241] hda-codec: out of range cmd 3:0:3ba0:f00:5
[   10.285244] hda-codec: out of range cmd 3:0:3ba1:f00:5
[   10.285247] hda-codec: out of range cmd 3:0:3ba2:f00:5
[   10.285249] hda-codec: out of range cmd 3:0:3ba3:f00:5
[   10.285252] hda-codec: out of range cmd 3:0:3ba4:f00:5
[   10.285255] hda-codec: out of range cmd 3:0:3ba5:f00:5
[   10.285258] hda-codec: out of range cmd 3:0:3ba6:f00:5
[   10.285263] hda-codec: out of range cmd 3:0:3ba7:f00:5
[   10.285266] hda-codec: out of range cmd 3:0:3ba8:f00:5
[   10.285268] hda-codec: out of range cmd 3:0:3ba9:f00:5
[   10.285271] hda-codec: out of range cmd 3:0:3baa:f00:5
[   10.285273] hda-codec: out of range cmd 3:0:3bab:f00:5
[   10.285275] hda-codec: out of range cmd 3:0:3bac:f00:5
[   10.285277] hda-codec: out of range cmd 3:0:3bad:f00:5
[   10.285280] hda-codec: out of range cmd 3:0:3bae:f00:5
[   10.285282] hda-codec: out of range cmd 3:0:3baf:f00:5
[   10.285286] hda-codec: out of range cmd 3:0:3bb0:f00:5
[   10.285289] hda-codec: out of range cmd 3:0:3bb1:f00:5
[   10.285292] hda-codec: out of range cmd 3:0:3bb2:f00:5
[   10.285294] hda-codec: out of range cmd 3:0:3bb3:f00:5
[   10.285297] hda-codec: out of range cmd 3:0:3bb4:f00:5
[   10.285300] hda-codec: out of range cmd 3:0:3bb5:f00:5
[   10.285304] hda-codec: out of range cmd 3:0:3bb6:f00:5
[   10.285307] hda-codec: out of range cmd 3:0:3bb7:f00:5
[   10.285309] hda-codec: out of range cmd 3:0:3bb8:f00:5
[   10.285312] hda-codec: out of range cmd 3:0:3bb9:f00:5
[   10.285315] hda-codec: out of range cmd 3:0:3bba:f00:5
[   10.285318] hda-codec: out of range cmd 3:0:3bbb:f00:5
[   10.285324] hda-codec: out of range cmd 3:0:3bbc:f00:5
[   10.285326] hda-codec: out of range cmd 3:0:3bbd:f00:5
[   10.285328] hda-codec: out of range cmd 3:0:3bbe:f00:5
[   10.285331] hda-codec: out of range cmd 3:0:3bbf:f00:5
[   10.285335] hda-codec: out of range cmd 3:0:3bc0:f00:5
[   10.285339] hda-codec: out of range cmd 3:0:3bc1:f00:5
[   10.285341] hda-codec: out of range cmd 3:0:3bc2:f00:5
[   10.285344] hda-codec: out of range cmd 3:0:3bc3:f00:5
[   10.285348] hda-codec: out of range cmd 3:0:3bc4:f00:5
[   10.285351] hda-codec: out of range cmd 3:0:3bc5:f00:5
[   10.285355] hda-codec: out of range cmd 3:0:3bc6:f00:5
[   10.285358] hda-codec: out of range cmd 3:0:3bc7:f00:5
[   10.285360] hda-codec: out of range cmd 3:0:3bc8:f00:5
[   10.285362] hda-codec: out of range cmd 3:0:3bc9:f00:5
[   10.285365] hda-codec: out of range cmd 3:0:3bca:f00:5
[   10.285368] hda-codec: out of range cmd 3:0:3bcb:f00:5
[   10.285370] hda-codec: out of range cmd 3:0:3bcc:f00:5
[   10.285373] hda-codec: out of range cmd 3:0:3bcd:f00:5
[   10.285376] hda-codec: out of range cmd 3:0:3bce:f00:5
[   10.285379] hda-codec: out of range cmd 3:0:3bcf:f00:5
[   10.285381] hda-codec: out of range cmd 3:0:3bd0:f00:5
[   10.285384] hda-codec: out of range cmd 3:0:3bd1:f00:5
[   10.285386] hda-codec: out of range cmd 3:0:3bd2:f00:5
[   10.285390] hda-codec: out of range cmd 3:0:3bd3:f00:5
[   10.285395] hda-codec: out of range cmd 3:0:3bd4:f00:5
[   10.285397] hda-codec: out of range cmd 3:0:3bd5:f00:5
[   10.285400] hda-codec: out of range cmd 3:0:3bd6:f00:5
[   10.285403] hda-codec: out of range cmd 3:0:3bd7:f00:5
[   10.285406] hda-codec: out of range cmd 3:0:3bd8:f00:5
[   10.285410] hda-codec: out of range cmd 3:0:3bd9:f00:5
[   10.285413] hda-codec: out of range cmd 3:0:3bda:f00:5
[   10.285416] hda-codec: out of range cmd 3:0:3bdb:f00:5
[   10.285418] hda-codec: out of range cmd 3:0:3bdc:f00:5
[   10.285421] hda-codec: out of range cmd 3:0:3bdd:f00:5
[   10.285424] hda-codec: out of range cmd 3:0:3bde:f00:5
[   10.285427] hda-codec: out of range cmd 3:0:3bdf:f00:5
[   10.285429] hda-codec: out of range cmd 3:0:3be0:f00:5
[   10.285431] hda-codec: out of range cmd 3:0:3be1:f00:5
[   10.285434] hda-codec: out of range cmd 3:0:3be2:f00:5
[   10.285436] hda-codec: out of range cmd 3:0:3be3:f00:5
[   10.285438] hda-codec: out of range cmd 3:0:3be4:f00:5
[   10.285441] hda-codec: out of range cmd 3:0:3be5:f00:5
[   10.285444] hda-codec: out of range cmd 3:0:3be6:f00:5
[   10.285446] hda-codec: out of range cmd 3:0:3be7:f00:5
[   10.285449] hda-codec: out of range cmd 3:0:3be8:f00:5
[   10.285455] hda-codec: out of range cmd 3:0:3be9:f00:5
[   10.285457] hda-codec: out of range cmd 3:0:3bea:f00:5
[   10.285460] hda-codec: out of range cmd 3:0:3beb:f00:5
[   10.285463] hda-codec: out of range cmd 3:0:3bec:f00:5
[   10.285466] hda-codec: out of range cmd 3:0:3bed:f00:5
[   10.285473] hda-codec: out of range cmd 3:0:3bee:f00:5
[   10.285475] hda-codec: out of range cmd 3:0:3bef:f00:5
[   10.285478] hda-codec: out of range cmd 3:0:3bf0:f00:5
[   10.285480] hda-codec: out of range cmd 3:0:3bf1:f00:5
[   10.285483] hda-codec: out of range cmd 3:0:3bf2:f00:5
[   10.285485] hda-codec: out of range cmd 3:0:3bf3:f00:5
[   10.285488] hda-codec: out of range cmd 3:0:3bf4:f00:5
[   10.285490] hda-codec: out of range cmd 3:0:3bf5:f00:5
[   10.285492] hda-codec: out of range cmd 3:0:3bf6:f00:5
[   10.285496] hda-codec: out of range cmd 3:0:3bf7:f00:5
[   10.285499] hda-codec: out of range cmd 3:0:3bf8:f00:5
[   10.285503] hda-codec: out of range cmd 3:0:3bf9:f00:5
[   10.285506] hda-codec: out of range cmd 3:0:3bfa:f00:5
[   10.285508] hda-codec: out of range cmd 3:0:3bfb:f00:5
[   10.285511] hda-codec: out of range cmd 3:0:3bfc:f00:5
[   10.285513] hda-codec: out of range cmd 3:0:3bfd:f00:5
[   10.285515] hda-codec: out of range cmd 3:0:3bfe:f00:5
[   10.285518] hda-codec: out of range cmd 3:0:3bff:f00:5
[   10.285520] hda-codec: out of range cmd 3:0:3c00:f00:5
[   10.285523] hda-codec: out of range cmd 3:0:3c01:f00:5
[   10.285527] hda-codec: out of range cmd 3:0:3c02:f00:5
[   10.285532] hda-codec: out of range cmd 3:0:3c03:f00:5
[   10.285534] hda-codec: out of range cmd 3:0:3c04:f00:5
[   10.285537] hda-codec: out of range cmd 3:0:3c05:f00:5
[   10.285539] hda-codec: out of range cmd 3:0:3c06:f00:5
[   10.285543] hda-codec: out of range cmd 3:0:3c07:f00:5
[   10.285546] hda-codec: out of range cmd 3:0:3c08:f00:5
[   10.285549] hda-codec: out of range cmd 3:0:3c09:f00:5
[   10.285554] hda-codec: out of range cmd 3:0:3c0a:f00:5
[   10.285557] hda-codec: out of range cmd 3:0:3c0b:f00:5
[   10.285559] hda-codec: out of range cmd 3:0:3c0c:f00:5
[   10.285562] hda-codec: out of range cmd 3:0:3c0d:f00:5
[   10.285567] hda-codec: out of range cmd 3:0:3c0e:f00:5
[   10.285570] hda-codec: out of range cmd 3:0:3c0f:f00:5
[   10.285572] hda-codec: out of range cmd 3:0:3c10:f00:5
[   10.285574] hda-codec: out of range cmd 3:0:3c11:f00:5
[   10.285577] hda-codec: out of range cmd 3:0:3c12:f00:5
[   10.285581] hda-codec: out of range cmd 3:0:3c13:f00:5
[   10.285584] hda-codec: out of range cmd 3:0:3c14:f00:5
[   10.285586] hda-codec: out of range cmd 3:0:3c15:f00:5
[   10.285589] hda-codec: out of range cmd 3:0:3c16:f00:5
[   10.285591] hda-codec: out of range cmd 3:0:3c17:f00:5
[   10.285593] hda-codec: out of range cmd 3:0:3c18:f00:5
[   10.285596] hda-codec: out of range cmd 3:0:3c19:f00:5
[   10.285600] hda-codec: out of range cmd 3:0:3c1a:f00:5
[   10.285603] hda-codec: out of range cmd 3:0:3c1b:f00:5
[   10.285606] hda-codec: out of range cmd 3:0:3c1c:f00:5
[   10.285609] hda-codec: out of range cmd 3:0:3c1d:f00:5
[   10.285613] hda-codec: out of range cmd 3:0:3c1e:f00:5
[   10.285616] hda-codec: out of range cmd 3:0:3c1f:f00:5
[   10.285618] hda-codec: out of range cmd 3:0:3c20:f00:5
[   10.285622] hda-codec: out of range cmd 3:0:3c21:f00:5
[   10.285624] hda-codec: out of range cmd 3:0:3c22:f00:5
[   10.285626] hda-codec: out of range cmd 3:0:3c23:f00:5
[   10.285629] hda-codec: out of range cmd 3:0:3c24:f00:5
[   10.285633] hda-codec: out of range cmd 3:0:3c25:f00:5
[   10.285636] hda-codec: out of range cmd 3:0:3c26:f00:5
[   10.285639] hda-codec: out of range cmd 3:0:3c27:f00:5
[   10.285643] hda-codec: out of range cmd 3:0:3c28:f00:5
[   10.285645] hda-codec: out of range cmd 3:0:3c29:f00:5
[   10.285648] hda-codec: out of range cmd 3:0:3c2a:f00:5
[   10.285651] hda-codec: out of range cmd 3:0:3c2b:f00:5
[   10.285654] hda-codec: out of range cmd 3:0:3c2c:f00:5
[   10.285658] hda-codec: out of range cmd 3:0:3c2d:f00:5
[   10.285661] hda-codec: out of range cmd 3:0:3c2e:f00:5
[   10.285664] hda-codec: out of range cmd 3:0:3c2f:f00:5
[   10.285667] hda-codec: out of range cmd 3:0:3c30:f00:5
[   10.285670] hda-codec: out of range cmd 3:0:3c31:f00:5
[   10.285673] hda-codec: out of range cmd 3:0:3c32:f00:5
[   10.285677] hda-codec: out of range cmd 3:0:3c33:f00:5
[   10.285680] hda-codec: out of range cmd 3:0:3c34:f00:5
[   10.285684] hda-codec: out of range cmd 3:0:3c35:f00:5
[   10.285686] hda-codec: out of range cmd 3:0:3c36:f00:5
[   10.285688] hda-codec: out of range cmd 3:0:3c37:f00:5
[   10.285691] hda-codec: out of range cmd 3:0:3c38:f00:5
[   10.285694] hda-codec: out of range cmd 3:0:3c39:f00:5
[   10.285697] hda-codec: out of range cmd 3:0:3c3a:f00:5
[   10.285700] hda-codec: out of range cmd 3:0:3c3b:f00:5
[   10.285703] hda-codec: out of range cmd 3:0:3c3c:f00:5
[   10.285706] hda-codec: out of range cmd 3:0:3c3d:f00:5
[   10.285710] hda-codec: out of range cmd 3:0:3c3e:f00:5
[   10.285715] hda-codec: out of range cmd 3:0:3c3f:f00:5
[   10.285717] hda-codec: out of range cmd 3:0:3c40:f00:5
[   10.285719] hda-codec: out of range cmd 3:0:3c41:f00:5
[   10.285722] hda-codec: out of range cmd 3:0:3c42:f00:5
[   10.285724] hda-codec: out of range cmd 3:0:3c43:f00:5
[   10.285726] hda-codec: out of range cmd 3:0:3c44:f00:5
[   10.285728] hda-codec: out of range cmd 3:0:3c45:f00:5
[   10.285731] hda-codec: out of range cmd 3:0:3c46:f00:5
[   10.285733] hda-codec: out of range cmd 3:0:3c47:f00:5
[   10.285735] hda-codec: out of range cmd 3:0:3c48:f00:5
[   10.285737] hda-codec: out of range cmd 3:0:3c49:f00:5
[   10.285740] hda-codec: out of range cmd 3:0:3c4a:f00:5
[   10.285743] hda-codec: out of range cmd 3:0:3c4b:f00:5
[   10.285745] hda-codec: out of range cmd 3:0:3c4c:f00:5
[   10.285747] hda-codec: out of range cmd 3:0:3c4d:f00:5
[   10.285749] hda-codec: out of range cmd 3:0:3c4e:f00:5
[   10.285751] hda-codec: out of range cmd 3:0:3c4f:f00:5
[   10.285753] hda-codec: out of range cmd 3:0:3c50:f00:5
[   10.285755] hda-codec: out of range cmd 3:0:3c51:f00:5
[   10.285757] hda-codec: out of range cmd 3:0:3c52:f00:5
[   10.285759] hda-codec: out of range cmd 3:0:3c53:f00:5
[   10.285762] hda-codec: out of range cmd 3:0:3c54:f00:5
[   10.285764] hda-codec: out of range cmd 3:0:3c55:f00:5
[   10.285767] hda-codec: out of range cmd 3:0:3c56:f00:5
[   10.285769] hda-codec: out of range cmd 3:0:3c57:f00:5
[   10.285771] hda-codec: out of range cmd 3:0:3c58:f00:5
[   10.285773] hda-codec: out of range cmd 3:0:3c59:f00:5
[   10.285776] hda-codec: out of range cmd 3:0:3c5a:f00:5
[   10.285778] hda-codec: out of range cmd 3:0:3c5b:f00:5
[   10.285781] hda-codec: out of range cmd 3:0:3c5c:f00:5
[   10.285783] hda-codec: out of range cmd 3:0:3c5d:f00:5
[   10.285785] hda-codec: out of range cmd 3:0:3c5e:f00:5
[   10.285788] hda-codec: out of range cmd 3:0:3c5f:f00:5
[   10.285790] hda-codec: out of range cmd 3:0:3c60:f00:5
[   10.285793] hda-codec: out of range cmd 3:0:3c61:f00:5
[   10.285797] hda-codec: out of range cmd 3:0:3c62:f00:5
[   10.285801] hda-codec: out of range cmd 3:0:3c63:f00:5
[   10.285804] hda-codec: out of range cmd 3:0:3c64:f00:5
[   10.285806] hda-codec: out of range cmd 3:0:3c65:f00:5
[   10.285809] hda-codec: out of range cmd 3:0:3c66:f00:5
[   10.285811] hda-codec: out of range cmd 3:0:3c67:f00:5
[   10.285814] hda-codec: out of range cmd 3:0:3c68:f00:5
[   10.285816] hda-codec: out of range cmd 3:0:3c69:f00:5
[   10.285819] hda-codec: out of range cmd 3:0:3c6a:f00:5
[   10.285821] hda-codec: out of range cmd 3:0:3c6b:f00:5
[   10.285825] hda-codec: out of range cmd 3:0:3c6c:f00:5
[   10.285827] hda-codec: out of range cmd 3:0:3c6d:f00:5
[   10.285834] hda-codec: out of range cmd 3:0:3c6e:f00:5
[   10.285836] hda-codec: out of range cmd 3:0:3c6f:f00:5
[   10.285839] hda-codec: out of range cmd 3:0:3c70:f00:5
[   10.285843] hda-codec: out of range cmd 3:0:3c71:f00:5
[   10.285846] hda-codec: out of range cmd 3:0:3c72:f00:5
[   10.285849] hda-codec: out of range cmd 3:0:3c73:f00:5
[   10.285851] hda-codec: out of range cmd 3:0:3c74:f00:5
[   10.285853] hda-codec: out of range cmd 3:0:3c75:f00:5
[   10.285855] hda-codec: out of range cmd 3:0:3c76:f00:5
[   10.285857] hda-codec: out of range cmd 3:0:3c77:f00:5
[   10.285860] hda-codec: out of range cmd 3:0:3c78:f00:5
[   10.285863] hda-codec: out of range cmd 3:0:3c79:f00:5
[   10.285866] hda-codec: out of range cmd 3:0:3c7a:f00:5
[   10.285869] hda-codec: out of range cmd 3:0:3c7b:f00:5
[   10.285873] hda-codec: out of range cmd 3:0:3c7c:f00:5
[   10.285875] hda-codec: out of range cmd 3:0:3c7d:f00:5
[   10.285878] hda-codec: out of range cmd 3:0:3c7e:f00:5
[   10.285880] hda-codec: out of range cmd 3:0:3c7f:f00:5
[   10.285882] hda-codec: out of range cmd 3:0:3c80:f00:5
[   10.285886] hda-codec: out of range cmd 3:0:3c81:f00:5
[   10.285888] hda-codec: out of range cmd 3:0:3c82:f00:5
[   10.285891] hda-codec: out of range cmd 3:0:3c83:f00:5
[   10.285893] hda-codec: out of range cmd 3:0:3c84:f00:5
[   10.285896] hda-codec: out of range cmd 3:0:3c85:f00:5
[   10.285901] hda-codec: out of range cmd 3:0:3c86:f00:5
[   10.285904] hda-codec: out of range cmd 3:0:3c87:f00:5
[   10.285907] hda-codec: out of range cmd 3:0:3c88:f00:5
[   10.285909] hda-codec: out of range cmd 3:0:3c89:f00:5
[   10.285913] hda-codec: out of range cmd 3:0:3c8a:f00:5
[   10.285917] hda-codec: out of range cmd 3:0:3c8b:f00:5
[   10.285921] hda-codec: out of range cmd 3:0:3c8c:f00:5
[   10.285926] hda-codec: out of range cmd 3:0:3c8d:f00:5
[   10.285928] hda-codec: out of range cmd 3:0:3c8e:f00:5
[   10.285933] hda-codec: out of range cmd 3:0:3c8f:f00:5
[   10.285937] hda-codec: out of range cmd 3:0:3c90:f00:5
[   10.285940] hda-codec: out of range cmd 3:0:3c91:f00:5
[   10.285942] hda-codec: out of range cmd 3:0:3c92:f00:5
[   10.285944] hda-codec: out of range cmd 3:0:3c93:f00:5
[   10.285947] hda-codec: out of range cmd 3:0:3c94:f00:5
[   10.285949] hda-codec: out of range cmd 3:0:3c95:f00:5
[   10.285952] hda-codec: out of range cmd 3:0:3c96:f00:5
[   10.285955] hda-codec: out of range cmd 3:0:3c97:f00:5
[   10.285957] hda-codec: out of range cmd 3:0:3c98:f00:5
[   10.285960] hda-codec: out of range cmd 3:0:3c99:f00:5
[   10.285964] hda-codec: out of range cmd 3:0:3c9a:f00:5
[   10.285966] hda-codec: out of range cmd 3:0:3c9b:f00:5
[   10.285968] hda-codec: out of range cmd 3:0:3c9c:f00:5
[   10.285971] hda-codec: out of range cmd 3:0:3c9d:f00:5
[   10.285973] hda-codec: out of range cmd 3:0:3c9e:f00:5
[   10.285976] hda-codec: out of range cmd 3:0:3c9f:f00:5
[   10.285979] hda-codec: out of range cmd 3:0:3ca0:f00:5
[   10.285981] hda-codec: out of range cmd 3:0:3ca1:f00:5
[   10.285984] hda-codec: out of range cmd 3:0:3ca2:f00:5
[   10.285986] hda-codec: out of range cmd 3:0:3ca3:f00:5
[   10.285988] hda-codec: out of range cmd 3:0:3ca4:f00:5
[   10.285990] hda-codec: out of range cmd 3:0:3ca5:f00:5
[   10.285992] hda-codec: out of range cmd 3:0:3ca6:f00:5
[   10.285994] hda-codec: out of range cmd 3:0:3ca7:f00:5
[   10.285997] hda-codec: out of range cmd 3:0:3ca8:f00:5
[   10.285999] hda-codec: out of range cmd 3:0:3ca9:f00:5
[   10.286003] hda-codec: out of range cmd 3:0:3caa:f00:5
[   10.286006] hda-codec: out of range cmd 3:0:3cab:f00:5
[   10.286010] hda-codec: out of range cmd 3:0:3cac:f00:5
[   10.286014] hda-codec: out of range cmd 3:0:3cad:f00:5
[   10.286017] hda-codec: out of range cmd 3:0:3cae:f00:5
[   10.286021] hda-codec: out of range cmd 3:0:3caf:f00:5
[   10.286025] hda-codec: out of range cmd 3:0:3cb0:f00:5
[   10.286027] hda-codec: out of range cmd 3:0:3cb1:f00:5
[   10.286030] hda-codec: out of range cmd 3:0:3cb2:f00:5
[   10.286034] hda-codec: out of range cmd 3:0:3cb3:f00:5
[   10.286036] hda-codec: out of range cmd 3:0:3cb4:f00:5
[   10.286039] hda-codec: out of range cmd 3:0:3cb5:f00:5
[   10.286041] hda-codec: out of range cmd 3:0:3cb6:f00:5
[   10.286044] hda-codec: out of range cmd 3:0:3cb7:f00:5
[   10.286046] hda-codec: out of range cmd 3:0:3cb8:f00:5
[   10.286048] hda-codec: out of range cmd 3:0:3cb9:f00:5
[   10.286051] hda-codec: out of range cmd 3:0:3cba:f00:5
[   10.286053] hda-codec: out of range cmd 3:0:3cbb:f00:5
[   10.286057] hda-codec: out of range cmd 3:0:3cbc:f00:5
[   10.286061] hda-codec: out of range cmd 3:0:3cbd:f00:5
[   10.286063] hda-codec: out of range cmd 3:0:3cbe:f00:5
[   10.286065] hda-codec: out of range cmd 3:0:3cbf:f00:5
[   10.286068] hda-codec: out of range cmd 3:0:3cc0:f00:5
[   10.286073] hda-codec: out of range cmd 3:0:3cc1:f00:5
[   10.286077] hda-codec: out of range cmd 3:0:3cc2:f00:5
[   10.286081] hda-codec: out of range cmd 3:0:3cc3:f00:5
[   10.286085] hda-codec: out of range cmd 3:0:3cc4:f00:5
[   10.286087] hda-codec: out of range cmd 3:0:3cc5:f00:5
[   10.286091] hda-codec: out of range cmd 3:0:3cc6:f00:5
[   10.286093] hda-codec: out of range cmd 3:0:3cc7:f00:5
[   10.286096] hda-codec: out of range cmd 3:0:3cc8:f00:5
[   10.286098] hda-codec: out of range cmd 3:0:3cc9:f00:5
[   10.286100] hda-codec: out of range cmd 3:0:3cca:f00:5
[   10.286103] hda-codec: out of range cmd 3:0:3ccb:f00:5
[   10.286107] hda-codec: out of range cmd 3:0:3ccc:f00:5
[   10.286110] hda-codec: out of range cmd 3:0:3ccd:f00:5
[   10.286113] hda-codec: out of range cmd 3:0:3cce:f00:5
[   10.286116] hda-codec: out of range cmd 3:0:3ccf:f00:5
[   10.286118] hda-codec: out of range cmd 3:0:3cd0:f00:5
[   10.286123] hda-codec: out of range cmd 3:0:3cd1:f00:5
[   10.286126] hda-codec: out of range cmd 3:0:3cd2:f00:5
[   10.286128] hda-codec: out of range cmd 3:0:3cd3:f00:5
[   10.286130] hda-codec: out of range cmd 3:0:3cd4:f00:5
[   10.286134] hda-codec: out of range cmd 3:0:3cd5:f00:5
[   10.286138] hda-codec: out of range cmd 3:0:3cd6:f00:5
[   10.286140] hda-codec: out of range cmd 3:0:3cd7:f00:5
[   10.286142] hda-codec: out of range cmd 3:0:3cd8:f00:5
[   10.286145] hda-codec: out of range cmd 3:0:3cd9:f00:5
[   10.286147] hda-codec: out of range cmd 3:0:3cda:f00:5
[   10.286151] hda-codec: out of range cmd 3:0:3cdb:f00:5
[   10.286154] hda-codec: out of range cmd 3:0:3cdc:f00:5
[   10.286156] hda-codec: out of range cmd 3:0:3cdd:f00:5
[   10.286160] hda-codec: out of range cmd 3:0:3cde:f00:5
[   10.286162] hda-codec: out of range cmd 3:0:3cdf:f00:5
[   10.286165] hda-codec: out of range cmd 3:0:3ce0:f00:5
[   10.286169] hda-codec: out of range cmd 3:0:3ce1:f00:5
[   10.286172] hda-codec: out of range cmd 3:0:3ce2:f00:5
[   10.286177] hda-codec: out of range cmd 3:0:3ce3:f00:5
[   10.286180] hda-codec: out of range cmd 3:0:3ce4:f00:5
[   10.286182] hda-codec: out of range cmd 3:0:3ce5:f00:5
[   10.286184] hda-codec: out of range cmd 3:0:3ce6:f00:5
[   10.286187] hda-codec: out of range cmd 3:0:3ce7:f00:5
[   10.286189] hda-codec: out of range cmd 3:0:3ce8:f00:5
[   10.286192] hda-codec: out of range cmd 3:0:3ce9:f00:5
[   10.286194] hda-codec: out of range cmd 3:0:3cea:f00:5
[   10.286197] hda-codec: out of range cmd 3:0:3ceb:f00:5
[   10.286200] hda-codec: out of range cmd 3:0:3cec:f00:5
[   10.286203] hda-codec: out of range cmd 3:0:3ced:f00:5
[   10.286207] hda-codec: out of range cmd 3:0:3cee:f00:5
[   10.286209] hda-codec: out of range cmd 3:0:3cef:f00:5
[   10.286212] hda-codec: out of range cmd 3:0:3cf0:f00:5
[   10.286216] hda-codec: out of range cmd 3:0:3cf1:f00:5
[   10.286219] hda-codec: out of range cmd 3:0:3cf2:f00:5
[   10.286222] hda-codec: out of range cmd 3:0:3cf3:f00:5
[   10.286225] hda-codec: out of range cmd 3:0:3cf4:f00:5
[   10.286227] hda-codec: out of range cmd 3:0:3cf5:f00:5
[   10.286230] hda-codec: out of range cmd 3:0:3cf6:f00:5
[   10.286235] hda-codec: out of range cmd 3:0:3cf7:f00:5
[   10.286238] hda-codec: out of range cmd 3:0:3cf8:f00:5
[   10.286240] hda-codec: out of range cmd 3:0:3cf9:f00:5
[   10.286243] hda-codec: out of range cmd 3:0:3cfa:f00:5
[   10.286245] hda-codec: out of range cmd 3:0:3cfb:f00:5
[   10.286248] hda-codec: out of range cmd 3:0:3cfc:f00:5
[   10.286252] hda-codec: out of range cmd 3:0:3cfd:f00:5
[   10.286254] hda-codec: out of range cmd 3:0:3cfe:f00:5
[   10.286257] hda-codec: out of range cmd 3:0:3cff:f00:5
[   10.286261] hda-codec: out of range cmd 3:0:3d00:f00:5
[   10.286263] hda-codec: out of range cmd 3:0:3d01:f00:5
[   10.286268] hda-codec: out of range cmd 3:0:3d02:f00:5
[   10.286271] hda-codec: out of range cmd 3:0:3d03:f00:5
[   10.286274] hda-codec: out of range cmd 3:0:3d04:f00:5
[   10.286276] hda-codec: out of range cmd 3:0:3d05:f00:5
[   10.286278] hda-codec: out of range cmd 3:0:3d06:f00:5
[   10.286281] hda-codec: out of range cmd 3:0:3d07:f00:5
[   10.286283] hda-codec: out of range cmd 3:0:3d08:f00:5
[   10.286285] hda-codec: out of range cmd 3:0:3d09:f00:5
[   10.286289] hda-codec: out of range cmd 3:0:3d0a:f00:5
[   10.286293] hda-codec: out of range cmd 3:0:3d0b:f00:5
[   10.286295] hda-codec: out of range cmd 3:0:3d0c:f00:5
[   10.286299] hda-codec: out of range cmd 3:0:3d0d:f00:5
[   10.286301] hda-codec: out of range cmd 3:0:3d0e:f00:5
[   10.286304] hda-codec: out of range cmd 3:0:3d0f:f00:5
[   10.286309] hda-codec: out of range cmd 3:0:3d10:f00:5
[   10.286313] hda-codec: out of range cmd 3:0:3d11:f00:5
[   10.286316] hda-codec: out of range cmd 3:0:3d12:f00:5
[   10.286318] hda-codec: out of range cmd 3:0:3d13:f00:5
[   10.286320] hda-codec: out of range cmd 3:0:3d14:f00:5
[   10.286324] hda-codec: out of range cmd 3:0:3d15:f00:5
[   10.286327] hda-codec: out of range cmd 3:0:3d16:f00:5
[   10.286330] hda-codec: out of range cmd 3:0:3d17:f00:5
[   10.286333] hda-codec: out of range cmd 3:0:3d18:f00:5
[   10.286335] hda-codec: out of range cmd 3:0:3d19:f00:5
[   10.286337] hda-codec: out of range cmd 3:0:3d1a:f00:5
[   10.286339] hda-codec: out of range cmd 3:0:3d1b:f00:5
[   10.286343] hda-codec: out of range cmd 3:0:3d1c:f00:5
[   10.286346] hda-codec: out of range cmd 3:0:3d1d:f00:5
[   10.286348] hda-codec: out of range cmd 3:0:3d1e:f00:5
[   10.286351] hda-codec: out of range cmd 3:0:3d1f:f00:5
[   10.286353] hda-codec: out of range cmd 3:0:3d20:f00:5
[   10.286356] hda-codec: out of range cmd 3:0:3d21:f00:5
[   10.286359] hda-codec: out of range cmd 3:0:3d22:f00:5
[   10.286362] hda-codec: out of range cmd 3:0:3d23:f00:5
[   10.286363] hda-codec: out of range cmd 3:0:3d24:f00:5
[   10.286369] hda-codec: out of range cmd 3:0:3d25:f00:5
[   10.286373] hda-codec: out of range cmd 3:0:3d26:f00:5
[   10.286376] hda-codec: out of range cmd 3:0:3d27:f00:5
[   10.286379] hda-codec: out of range cmd 3:0:3d28:f00:5
[   10.286381] hda-codec: out of range cmd 3:0:3d29:f00:5
[   10.286387] hda-codec: out of range cmd 3:0:3d2a:f00:5
[   10.286391] hda-codec: out of range cmd 3:0:3d2b:f00:5
[   10.286394] hda-codec: out of range cmd 3:0:3d2c:f00:5
[   10.286397] hda-codec: out of range cmd 3:0:3d2d:f00:5
[   10.286399] hda-codec: out of range cmd 3:0:3d2e:f00:5
[   10.286402] hda-codec: out of range cmd 3:0:3d2f:f00:5
[   10.286405] hda-codec: out of range cmd 3:0:3d30:f00:5
[   10.286408] hda-codec: out of range cmd 3:0:3d31:f00:5
[   10.286411] hda-codec: out of range cmd 3:0:3d32:f00:5
[   10.286413] hda-codec: out of range cmd 3:0:3d33:f00:5
[   10.286416] hda-codec: out of range cmd 3:0:3d34:f00:5
[   10.286420] hda-codec: out of range cmd 3:0:3d35:f00:5
[   10.286422] hda-codec: out of range cmd 3:0:3d36:f00:5
[   10.286426] hda-codec: out of range cmd 3:0:3d37:f00:5
[   10.286429] hda-codec: out of range cmd 3:0:3d38:f00:5
[   10.286431] hda-codec: out of range cmd 3:0:3d39:f00:5
[   10.286433] hda-codec: out of range cmd 3:0:3d3a:f00:5
[   10.286435] hda-codec: out of range cmd 3:0:3d3b:f00:5
[   10.286439] hda-codec: out of range cmd 3:0:3d3c:f00:5
[   10.286442] hda-codec: out of range cmd 3:0:3d3d:f00:5
[   10.286444] hda-codec: out of range cmd 3:0:3d3e:f00:5
[   10.286447] hda-codec: out of range cmd 3:0:3d3f:f00:5
[   10.286453] hda-codec: out of range cmd 3:0:3d40:f00:5
[   10.286455] hda-codec: out of range cmd 3:0:3d41:f00:5
[   10.286458] hda-codec: out of range cmd 3:0:3d42:f00:5
[   10.286460] hda-codec: out of range cmd 3:0:3d43:f00:5
[   10.286463] hda-codec: out of range cmd 3:0:3d44:f00:5
[   10.286468] hda-codec: out of range cmd 3:0:3d45:f00:5
[   10.286471] hda-codec: out of range cmd 3:0:3d46:f00:5
[   10.286476] hda-codec: out of range cmd 3:0:3d47:f00:5
[   10.286479] hda-codec: out of range cmd 3:0:3d48:f00:5
[   10.286482] hda-codec: out of range cmd 3:0:3d49:f00:5
[   10.286486] hda-codec: out of range cmd 3:0:3d4a:f00:5
[   10.286489] hda-codec: out of range cmd 3:0:3d4b:f00:5
[   10.286492] hda-codec: out of range cmd 3:0:3d4c:f00:5
[   10.286494] hda-codec: out of range cmd 3:0:3d4d:f00:5
[   10.286496] hda-codec: out of range cmd 3:0:3d4e:f00:5
[   10.286500] hda-codec: out of range cmd 3:0:3d4f:f00:5
[   10.286503] hda-codec: out of range cmd 3:0:3d50:f00:5
[   10.286506] hda-codec: out of range cmd 3:0:3d51:f00:5
[   10.286508] hda-codec: out of range cmd 3:0:3d52:f00:5
[   10.286510] hda-codec: out of range cmd 3:0:3d53:f00:5
[   10.286515] hda-codec: out of range cmd 3:0:3d54:f00:5
[   10.286518] hda-codec: out of range cmd 3:0:3d55:f00:5
[   10.286521] hda-codec: out of range cmd 3:0:3d56:f00:5
[   10.286524] hda-codec: out of range cmd 3:0:3d57:f00:5
[   10.286526] hda-codec: out of range cmd 3:0:3d58:f00:5
[   10.286529] hda-codec: out of range cmd 3:0:3d59:f00:5
[   10.286532] hda-codec: out of range cmd 3:0:3d5a:f00:5
[   10.286535] hda-codec: out of range cmd 3:0:3d5b:f00:5
[   10.286538] hda-codec: out of range cmd 3:0:3d5c:f00:5
[   10.286540] hda-codec: out of range cmd 3:0:3d5d:f00:5
[   10.286544] hda-codec: out of range cmd 3:0:3d5e:f00:5
[   10.286547] hda-codec: out of range cmd 3:0:3d5f:f00:5
[   10.286550] hda-codec: out of range cmd 3:0:3d60:f00:5
[   10.286553] hda-codec: out of range cmd 3:0:3d61:f00:5
[   10.286556] hda-codec: out of range cmd 3:0:3d62:f00:5
[   10.286559] hda-codec: out of range cmd 3:0:3d63:f00:5
[   10.286562] hda-codec: out of range cmd 3:0:3d64:f00:5
[   10.286565] hda-codec: out of range cmd 3:0:3d65:f00:5
[   10.286567] hda-codec: out of range cmd 3:0:3d66:f00:5
[   10.286571] hda-codec: out of range cmd 3:0:3d67:f00:5
[   10.286573] hda-codec: out of range cmd 3:0:3d68:f00:5
[   10.286577] hda-codec: out of range cmd 3:0:3d69:f00:5
[   10.286579] hda-codec: out of range cmd 3:0:3d6a:f00:5
[   10.286582] hda-codec: out of range cmd 3:0:3d6b:f00:5
[   10.286585] hda-codec: out of range cmd 3:0:3d6c:f00:5
[   10.286588] hda-codec: out of range cmd 3:0:3d6d:f00:5
[   10.286590] hda-codec: out of range cmd 3:0:3d6e:f00:5
[   10.286595] hda-codec: out of range cmd 3:0:3d6f:f00:5
[   10.286597] hda-codec: out of range cmd 3:0:3d70:f00:5
[   10.286601] hda-codec: out of range cmd 3:0:3d71:f00:5
[   10.286604] hda-codec: out of range cmd 3:0:3d72:f00:5
[   10.286607] hda-codec: out of range cmd 3:0:3d73:f00:5
[   10.286610] hda-codec: out of range cmd 3:0:3d74:f00:5
[   10.286613] hda-codec: out of range cmd 3:0:3d75:f00:5
[   10.286616] hda-codec: out of range cmd 3:0:3d76:f00:5
[   10.286619] hda-codec: out of range cmd 3:0:3d77:f00:5
[   10.286622] hda-codec: out of range cmd 3:0:3d78:f00:5
[   10.286625] hda-codec: out of range cmd 3:0:3d79:f00:5
[   10.286628] hda-codec: out of range cmd 3:0:3d7a:f00:5
[   10.286631] hda-codec: out of range cmd 3:0:3d7b:f00:5
[   10.286634] hda-codec: out of range cmd 3:0:3d7c:f00:5
[   10.286636] hda-codec: out of range cmd 3:0:3d7d:f00:5
[   10.286640] hda-codec: out of range cmd 3:0:3d7e:f00:5
[   10.286645] hda-codec: out of range cmd 3:0:3d7f:f00:5
[   10.286648] hda-codec: out of range cmd 3:0:3d80:f00:5
[   10.286650] hda-codec: out of range cmd 3:0:3d81:f00:5
[   10.286652] hda-codec: out of range cmd 3:0:3d82:f00:5
[   10.286654] hda-codec: out of range cmd 3:0:3d83:f00:5
[   10.286657] hda-codec: out of range cmd 3:0:3d84:f00:5
[   10.286659] hda-codec: out of range cmd 3:0:3d85:f00:5
[   10.286661] hda-codec: out of range cmd 3:0:3d86:f00:5
[   10.286663] hda-codec: out of range cmd 3:0:3d87:f00:5
[   10.286665] hda-codec: out of range cmd 3:0:3d88:f00:5
[   10.286667] hda-codec: out of range cmd 3:0:3d89:f00:5
[   10.286670] hda-codec: out of range cmd 3:0:3d8a:f00:5
[   10.286672] hda-codec: out of range cmd 3:0:3d8b:f00:5
[   10.286675] hda-codec: out of range cmd 3:0:3d8c:f00:5
[   10.286677] hda-codec: out of range cmd 3:0:3d8d:f00:5
[   10.286679] hda-codec: out of range cmd 3:0:3d8e:f00:5
[   10.286681] hda-codec: out of range cmd 3:0:3d8f:f00:5
[   10.286683] hda-codec: out of range cmd 3:0:3d90:f00:5
[   10.286685] hda-codec: out of range cmd 3:0:3d91:f00:5
[   10.286687] hda-codec: out of range cmd 3:0:3d92:f00:5
[   10.286690] hda-codec: out of range cmd 3:0:3d93:f00:5
[   10.286692] hda-codec: out of range cmd 3:0:3d94:f00:5
[   10.286694] hda-codec: out of range cmd 3:0:3d95:f00:5
[   10.286696] hda-codec: out of range cmd 3:0:3d96:f00:5
[   10.286699] hda-codec: out of range cmd 3:0:3d97:f00:5
[   10.286702] hda-codec: out of range cmd 3:0:3d98:f00:5
[   10.286704] hda-codec: out of range cmd 3:0:3d99:f00:5
[   10.286706] hda-codec: out of range cmd 3:0:3d9a:f00:5
[   10.286708] hda-codec: out of range cmd 3:0:3d9b:f00:5
[   10.286711] hda-codec: out of range cmd 3:0:3d9c:f00:5
[   10.286713] hda-codec: out of range cmd 3:0:3d9d:f00:5
[   10.286715] hda-codec: out of range cmd 3:0:3d9e:f00:5
[   10.286717] hda-codec: out of range cmd 3:0:3d9f:f00:5
[   10.286719] hda-codec: out of range cmd 3:0:3da0:f00:5
[   10.286723] hda-codec: out of range cmd 3:0:3da1:f00:5
[   10.286725] hda-codec: out of range cmd 3:0:3da2:f00:5
[   10.286728] hda-codec: out of range cmd 3:0:3da3:f00:5
[   10.286730] hda-codec: out of range cmd 3:0:3da4:f00:5
[   10.286733] hda-codec: out of range cmd 3:0:3da5:f00:5
[   10.286735] hda-codec: out of range cmd 3:0:3da6:f00:5
[   10.286737] hda-codec: out of range cmd 3:0:3da7:f00:5
[   10.286741] hda-codec: out of range cmd 3:0:3da8:f00:5
[   10.286744] hda-codec: out of range cmd 3:0:3da9:f00:5
[   10.286747] hda-codec: out of range cmd 3:0:3daa:f00:5
[   10.286752] hda-codec: out of range cmd 3:0:3dab:f00:5
[   10.286754] hda-codec: out of range cmd 3:0:3dac:f00:5
[   10.286759] hda-codec: out of range cmd 3:0:3dad:f00:5
[   10.286763] hda-codec: out of range cmd 3:0:3dae:f00:5
[   10.286765] hda-codec: out of range cmd 3:0:3daf:f00:5
[   10.286768] hda-codec: out of range cmd 3:0:3db0:f00:5
[   10.286770] hda-codec: out of range cmd 3:0:3db1:f00:5
[   10.286772] hda-codec: out of range cmd 3:0:3db2:f00:5
[   10.286774] hda-codec: out of range cmd 3:0:3db3:f00:5
[   10.286777] hda-codec: out of range cmd 3:0:3db4:f00:5
[   10.286779] hda-codec: out of range cmd 3:0:3db5:f00:5
[   10.286781] hda-codec: out of range cmd 3:0:3db6:f00:5
[   10.286785] hda-codec: out of range cmd 3:0:3db7:f00:5
[   10.286789] hda-codec: out of range cmd 3:0:3db8:f00:5
[   10.286791] hda-codec: out of range cmd 3:0:3db9:f00:5
[   10.286793] hda-codec: out of range cmd 3:0:3dba:f00:5
[   10.286796] hda-codec: out of range cmd 3:0:3dbb:f00:5
[   10.286798] hda-codec: out of range cmd 3:0:3dbc:f00:5
[   10.286801] hda-codec: out of range cmd 3:0:3dbd:f00:5
[   10.286803] hda-codec: out of range cmd 3:0:3dbe:f00:5
[   10.286806] hda-codec: out of range cmd 3:0:3dbf:f00:5
[   10.286808] hda-codec: out of range cmd 3:0:3dc0:f00:5
[   10.286810] hda-codec: out of range cmd 3:0:3dc1:f00:5
[   10.286814] hda-codec: out of range cmd 3:0:3dc2:f00:5
[   10.286816] hda-codec: out of range cmd 3:0:3dc3:f00:5
[   10.286819] hda-codec: out of range cmd 3:0:3dc4:f00:5
[   10.286822] hda-codec: out of range cmd 3:0:3dc5:f00:5
[   10.286824] hda-codec: out of range cmd 3:0:3dc6:f00:5
[   10.286827] hda-codec: out of range cmd 3:0:3dc7:f00:5
[   10.286831] hda-codec: out of range cmd 3:0:3dc8:f00:5
[   10.286835] hda-codec: out of range cmd 3:0:3dc9:f00:5
[   10.286840] hda-codec: out of range cmd 3:0:3dca:f00:5
[   10.286842] hda-codec: out of range cmd 3:0:3dcb:f00:5
[   10.286846] hda-codec: out of range cmd 3:0:3dcc:f00:5
[   10.286850] hda-codec: out of range cmd 3:0:3dcd:f00:5
[   10.286852] hda-codec: out of range cmd 3:0:3dce:f00:5
[   10.286855] hda-codec: out of range cmd 3:0:3dcf:f00:5
[   10.286857] hda-codec: out of range cmd 3:0:3dd0:f00:5
[   10.286859] hda-codec: out of range cmd 3:0:3dd1:f00:5
[   10.286861] hda-codec: out of range cmd 3:0:3dd2:f00:5
[   10.286863] hda-codec: out of range cmd 3:0:3dd3:f00:5
[   10.286866] hda-codec: out of range cmd 3:0:3dd4:f00:5
[   10.286868] hda-codec: out of range cmd 3:0:3dd5:f00:5
[   10.286871] hda-codec: out of range cmd 3:0:3dd6:f00:5
[   10.286875] hda-codec: out of range cmd 3:0:3dd7:f00:5
[   10.286878] hda-codec: out of range cmd 3:0:3dd8:f00:5
[   10.286880] hda-codec: out of range cmd 3:0:3dd9:f00:5
[   10.286883] hda-codec: out of range cmd 3:0:3dda:f00:5
[   10.286885] hda-codec: out of range cmd 3:0:3ddb:f00:5
[   10.286888] hda-codec: out of range cmd 3:0:3ddc:f00:5
[   10.286890] hda-codec: out of range cmd 3:0:3ddd:f00:5
[   10.286892] hda-codec: out of range cmd 3:0:3dde:f00:5
[   10.286895] hda-codec: out of range cmd 3:0:3ddf:f00:5
[   10.286897] hda-codec: out of range cmd 3:0:3de0:f00:5
[   10.286899] hda-codec: out of range cmd 3:0:3de1:f00:5
[   10.286901] hda-codec: out of range cmd 3:0:3de2:f00:5
[   10.286904] hda-codec: out of range cmd 3:0:3de3:f00:5
[   10.286906] hda-codec: out of range cmd 3:0:3de4:f00:5
[   10.286909] hda-codec: out of range cmd 3:0:3de5:f00:5
[   10.286911] hda-codec: out of range cmd 3:0:3de6:f00:5
[   10.286915] hda-codec: out of range cmd 3:0:3de7:f00:5
[   10.286919] hda-codec: out of range cmd 3:0:3de8:f00:5
[   10.286922] hda-codec: out of range cmd 3:0:3de9:f00:5
[   10.286926] hda-codec: out of range cmd 3:0:3dea:f00:5
[   10.286930] hda-codec: out of range cmd 3:0:3deb:f00:5
[   10.286934] hda-codec: out of range cmd 3:0:3dec:f00:5
[   10.286937] hda-codec: out of range cmd 3:0:3ded:f00:5
[   10.286939] hda-codec: out of range cmd 3:0:3dee:f00:5
[   10.286942] hda-codec: out of range cmd 3:0:3def:f00:5
[   10.286946] hda-codec: out of range cmd 3:0:3df0:f00:5
[   10.286948] hda-codec: out of range cmd 3:0:3df1:f00:5
[   10.286952] hda-codec: out of range cmd 3:0:3df2:f00:5
[   10.286954] hda-codec: out of range cmd 3:0:3df3:f00:5
[   10.286956] hda-codec: out of range cmd 3:0:3df4:f00:5
[   10.286959] hda-codec: out of range cmd 3:0:3df5:f00:5
[   10.286962] hda-codec: out of range cmd 3:0:3df6:f00:5
[   10.286965] hda-codec: out of range cmd 3:0:3df7:f00:5
[   10.286968] hda-codec: out of range cmd 3:0:3df8:f00:5
[   10.286970] hda-codec: out of range cmd 3:0:3df9:f00:5
[   10.286973] hda-codec: out of range cmd 3:0:3dfa:f00:5
[   10.286978] hda-codec: out of range cmd 3:0:3dfb:f00:5
[   10.286980] hda-codec: out of range cmd 3:0:3dfc:f00:5
[   10.286983] hda-codec: out of range cmd 3:0:3dfd:f00:5
[   10.286986] hda-codec: out of range cmd 3:0:3dfe:f00:5
[   10.286991] hda-codec: out of range cmd 3:0:3dff:f00:5
[   10.286995] hda-codec: out of range cmd 3:0:3e00:f00:5
[   10.286998] hda-codec: out of range cmd 3:0:3e01:f00:5
[   10.287002] hda-codec: out of range cmd 3:0:3e02:f00:5
[   10.287004] hda-codec: out of range cmd 3:0:3e03:f00:5
[   10.287008] hda-codec: out of range cmd 3:0:3e04:f00:5
[   10.287012] hda-codec: out of range cmd 3:0:3e05:f00:5
[   10.287015] hda-codec: out of range cmd 3:0:3e06:f00:5
[   10.287017] hda-codec: out of range cmd 3:0:3e07:f00:5
[   10.287019] hda-codec: out of range cmd 3:0:3e08:f00:5
[   10.287022] hda-codec: out of range cmd 3:0:3e09:f00:5
[   10.287027] hda-codec: out of range cmd 3:0:3e0a:f00:5
[   10.287029] hda-codec: out of range cmd 3:0:3e0b:f00:5
[   10.287032] hda-codec: out of range cmd 3:0:3e0c:f00:5
[   10.287034] hda-codec: out of range cmd 3:0:3e0d:f00:5
[   10.287037] hda-codec: out of range cmd 3:0:3e0e:f00:5
[   10.287041] hda-codec: out of range cmd 3:0:3e0f:f00:5
[   10.287044] hda-codec: out of range cmd 3:0:3e10:f00:5
[   10.287046] hda-codec: out of range cmd 3:0:3e11:f00:5
[   10.287048] hda-codec: out of range cmd 3:0:3e12:f00:5
[   10.287051] hda-codec: out of range cmd 3:0:3e13:f00:5
[   10.287055] hda-codec: out of range cmd 3:0:3e14:f00:5
[   10.287057] hda-codec: out of range cmd 3:0:3e15:f00:5
[   10.287060] hda-codec: out of range cmd 3:0:3e16:f00:5
[   10.287062] hda-codec: out of range cmd 3:0:3e17:f00:5
[   10.287066] hda-codec: out of range cmd 3:0:3e18:f00:5
[   10.287070] hda-codec: out of range cmd 3:0:3e19:f00:5
[   10.287073] hda-codec: out of range cmd 3:0:3e1a:f00:5
[   10.287076] hda-codec: out of range cmd 3:0:3e1b:f00:5
[   10.287079] hda-codec: out of range cmd 3:0:3e1c:f00:5
[   10.287081] hda-codec: out of range cmd 3:0:3e1d:f00:5
[   10.287084] hda-codec: out of range cmd 3:0:3e1e:f00:5
[   10.287087] hda-codec: out of range cmd 3:0:3e1f:f00:5
[   10.287092] hda-codec: out of range cmd 3:0:3e20:f00:5
[   10.287096] hda-codec: out of range cmd 3:0:3e21:f00:5
[   10.287098] hda-codec: out of range cmd 3:0:3e22:f00:5
[   10.287101] hda-codec: out of range cmd 3:0:3e23:f00:5
[   10.287103] hda-codec: out of range cmd 3:0:3e24:f00:5
[   10.287106] hda-codec: out of range cmd 3:0:3e25:f00:5
[   10.287109] hda-codec: out of range cmd 3:0:3e26:f00:5
[   10.287112] hda-codec: out of range cmd 3:0:3e27:f00:5
[   10.287114] hda-codec: out of range cmd 3:0:3e28:f00:5
[   10.287117] hda-codec: out of range cmd 3:0:3e29:f00:5
[   10.287121] hda-codec: out of range cmd 3:0:3e2a:f00:5
[   10.287123] hda-codec: out of range cmd 3:0:3e2b:f00:5
[   10.287126] hda-codec: out of range cmd 3:0:3e2c:f00:5
[   10.287129] hda-codec: out of range cmd 3:0:3e2d:f00:5
[   10.287131] hda-codec: out of range cmd 3:0:3e2e:f00:5
[   10.287135] hda-codec: out of range cmd 3:0:3e2f:f00:5
[   10.287139] hda-codec: out of range cmd 3:0:3e30:f00:5
[   10.287142] hda-codec: out of range cmd 3:0:3e31:f00:5
[   10.287145] hda-codec: out of range cmd 3:0:3e32:f00:5
[   10.287147] hda-codec: out of range cmd 3:0:3e33:f00:5
[   10.287151] hda-codec: out of range cmd 3:0:3e34:f00:5
[   10.287155] hda-codec: out of range cmd 3:0:3e35:f00:5
[   10.287159] hda-codec: out of range cmd 3:0:3e36:f00:5
[   10.287161] hda-codec: out of range cmd 3:0:3e37:f00:5
[   10.287163] hda-codec: out of range cmd 3:0:3e38:f00:5
[   10.287166] hda-codec: out of range cmd 3:0:3e39:f00:5
[   10.287169] hda-codec: out of range cmd 3:0:3e3a:f00:5
[   10.287172] hda-codec: out of range cmd 3:0:3e3b:f00:5
[   10.287175] hda-codec: out of range cmd 3:0:3e3c:f00:5
[   10.287177] hda-codec: out of range cmd 3:0:3e3d:f00:5
[   10.287182] hda-codec: out of range cmd 3:0:3e3e:f00:5
[   10.287184] hda-codec: out of range cmd 3:0:3e3f:f00:5
[   10.287188] hda-codec: out of range cmd 3:0:3e40:f00:5
[   10.287192] hda-codec: out of range cmd 3:0:3e41:f00:5
[   10.287194] hda-codec: out of range cmd 3:0:3e42:f00:5
[   10.287197] hda-codec: out of range cmd 3:0:3e43:f00:5
[   10.287199] hda-codec: out of range cmd 3:0:3e44:f00:5
[   10.287202] hda-codec: out of range cmd 3:0:3e45:f00:5
[   10.287204] hda-codec: out of range cmd 3:0:3e46:f00:5
[   10.287206] hda-codec: out of range cmd 3:0:3e47:f00:5
[   10.287210] hda-codec: out of range cmd 3:0:3e48:f00:5
[   10.287214] hda-codec: out of range cmd 3:0:3e49:f00:5
[   10.287216] hda-codec: out of range cmd 3:0:3e4a:f00:5
[   10.287220] hda-codec: out of range cmd 3:0:3e4b:f00:5
[   10.287222] hda-codec: out of range cmd 3:0:3e4c:f00:5
[   10.287225] hda-codec: out of range cmd 3:0:3e4d:f00:5
[   10.287229] hda-codec: out of range cmd 3:0:3e4e:f00:5
[   10.287232] hda-codec: out of range cmd 3:0:3e4f:f00:5
[   10.287236] hda-codec: out of range cmd 3:0:3e50:f00:5
[   10.287238] hda-codec: out of range cmd 3:0:3e51:f00:5
[   10.287242] hda-codec: out of range cmd 3:0:3e52:f00:5
[   10.287245] hda-codec: out of range cmd 3:0:3e53:f00:5
[   10.287248] hda-codec: out of range cmd 3:0:3e54:f00:5
[   10.287252] hda-codec: out of range cmd 3:0:3e55:f00:5
[   10.287254] hda-codec: out of range cmd 3:0:3e56:f00:5
[   10.287256] hda-codec: out of range cmd 3:0:3e57:f00:5
[   10.287259] hda-codec: out of range cmd 3:0:3e58:f00:5
[   10.287261] hda-codec: out of range cmd 3:0:3e59:f00:5
[   10.287264] hda-codec: out of range cmd 3:0:3e5a:f00:5
[   10.287266] hda-codec: out of range cmd 3:0:3e5b:f00:5
[   10.287269] hda-codec: out of range cmd 3:0:3e5c:f00:5
[   10.287271] hda-codec: out of range cmd 3:0:3e5d:f00:5
[   10.287274] hda-codec: out of range cmd 3:0:3e5e:f00:5
[   10.287276] hda-codec: out of range cmd 3:0:3e5f:f00:5
[   10.287279] hda-codec: out of range cmd 3:0:3e60:f00:5
[   10.287281] hda-codec: out of range cmd 3:0:3e61:f00:5
[   10.287285] hda-codec: out of range cmd 3:0:3e62:f00:5
[   10.287290] hda-codec: out of range cmd 3:0:3e63:f00:5
[   10.287293] hda-codec: out of range cmd 3:0:3e64:f00:5
[   10.287296] hda-codec: out of range cmd 3:0:3e65:f00:5
[   10.287298] hda-codec: out of range cmd 3:0:3e66:f00:5
[   10.287302] hda-codec: out of range cmd 3:0:3e67:f00:5
[   10.287308] hda-codec: out of range cmd 3:0:3e68:f00:5
[   10.287311] hda-codec: out of range cmd 3:0:3e69:f00:5
[   10.287313] hda-codec: out of range cmd 3:0:3e6a:f00:5
[   10.287316] hda-codec: out of range cmd 3:0:3e6b:f00:5
[   10.287318] hda-codec: out of range cmd 3:0:3e6c:f00:5
[   10.287321] hda-codec: out of range cmd 3:0:3e6d:f00:5
[   10.287325] hda-codec: out of range cmd 3:0:3e6e:f00:5
[   10.287327] hda-codec: out of range cmd 3:0:3e6f:f00:5
[   10.287329] hda-codec: out of range cmd 3:0:3e70:f00:5
[   10.287332] hda-codec: out of range cmd 3:0:3e71:f00:5
[   10.287335] hda-codec: out of range cmd 3:0:3e72:f00:5
[   10.287338] hda-codec: out of range cmd 3:0:3e73:f00:5
[   10.287342] hda-codec: out of range cmd 3:0:3e74:f00:5
[   10.287344] hda-codec: out of range cmd 3:0:3e75:f00:5
[   10.287347] hda-codec: out of range cmd 3:0:3e76:f00:5
[   10.287350] hda-codec: out of range cmd 3:0:3e77:f00:5
[   10.287352] hda-codec: out of range cmd 3:0:3e78:f00:5
[   10.287356] hda-codec: out of range cmd 3:0:3e79:f00:5
[   10.287358] hda-codec: out of range cmd 3:0:3e7a:f00:5
[   10.287362] hda-codec: out of range cmd 3:0:3e7b:f00:5
[   10.287367] hda-codec: out of range cmd 3:0:3e7c:f00:5
[   10.287370] hda-codec: out of range cmd 3:0:3e7d:f00:5
[   10.287372] hda-codec: out of range cmd 3:0:3e7e:f00:5
[   10.287374] hda-codec: out of range cmd 3:0:3e7f:f00:5
[   10.287378] hda-codec: out of range cmd 3:0:3e80:f00:5
[   10.287383] hda-codec: out of range cmd 3:0:3e81:f00:5
[   10.287385] hda-codec: out of range cmd 3:0:3e82:f00:5
[   10.287389] hda-codec: out of range cmd 3:0:3e83:f00:5
[   10.287392] hda-codec: out of range cmd 3:0:3e84:f00:5
[   10.287394] hda-codec: out of range cmd 3:0:3e85:f00:5
[   10.287398] hda-codec: out of range cmd 3:0:3e86:f00:5
[   10.287402] hda-codec: out of range cmd 3:0:3e87:f00:5
[   10.287404] hda-codec: out of range cmd 3:0:3e88:f00:5
[   10.287407] hda-codec: out of range cmd 3:0:3e89:f00:5
[   10.287409] hda-codec: out of range cmd 3:0:3e8a:f00:5
[   10.287413] hda-codec: out of range cmd 3:0:3e8b:f00:5
[   10.287415] hda-codec: out of range cmd 3:0:3e8c:f00:5
[   10.287419] hda-codec: out of range cmd 3:0:3e8d:f00:5
[   10.287422] hda-codec: out of range cmd 3:0:3e8e:f00:5
[   10.287425] hda-codec: out of range cmd 3:0:3e8f:f00:5
[   10.287427] hda-codec: out of range cmd 3:0:3e90:f00:5
[   10.287430] hda-codec: out of range cmd 3:0:3e91:f00:5
[   10.287434] hda-codec: out of range cmd 3:0:3e92:f00:5
[   10.287436] hda-codec: out of range cmd 3:0:3e93:f00:5
[   10.287439] hda-codec: out of range cmd 3:0:3e94:f00:5
[   10.287441] hda-codec: out of range cmd 3:0:3e95:f00:5
[   10.287443] hda-codec: out of range cmd 3:0:3e96:f00:5
[   10.287445] hda-codec: out of range cmd 3:0:3e97:f00:5
[   10.287448] hda-codec: out of range cmd 3:0:3e98:f00:5
[   10.287450] hda-codec: out of range cmd 3:0:3e99:f00:5
[   10.287453] hda-codec: out of range cmd 3:0:3e9a:f00:5
[   10.287455] hda-codec: out of range cmd 3:0:3e9b:f00:5
[   10.287458] hda-codec: out of range cmd 3:0:3e9c:f00:5
[   10.287462] hda-codec: out of range cmd 3:0:3e9d:f00:5
[   10.287465] hda-codec: out of range cmd 3:0:3e9e:f00:5
[   10.287469] hda-codec: out of range cmd 3:0:3e9f:f00:5
[   10.287471] hda-codec: out of range cmd 3:0:3ea0:f00:5
[   10.287474] hda-codec: out of range cmd 3:0:3ea1:f00:5
[   10.287477] hda-codec: out of range cmd 3:0:3ea2:f00:5
[   10.287481] hda-codec: out of range cmd 3:0:3ea3:f00:5
[   10.287484] hda-codec: out of range cmd 3:0:3ea4:f00:5
[   10.287488] hda-codec: out of range cmd 3:0:3ea5:f00:5
[   10.287491] hda-codec: out of range cmd 3:0:3ea6:f00:5
[   10.287494] hda-codec: out of range cmd 3:0:3ea7:f00:5
[   10.287497] hda-codec: out of range cmd 3:0:3ea8:f00:5
[   10.287500] hda-codec: out of range cmd 3:0:3ea9:f00:5
[   10.287502] hda-codec: out of range cmd 3:0:3eaa:f00:5
[   10.287505] hda-codec: out of range cmd 3:0:3eab:f00:5
[   10.287508] hda-codec: out of range cmd 3:0:3eac:f00:5
[   10.287511] hda-codec: out of range cmd 3:0:3ead:f00:5
[   10.287514] hda-codec: out of range cmd 3:0:3eae:f00:5
[   10.287517] hda-codec: out of range cmd 3:0:3eaf:f00:5
[   10.287520] hda-codec: out of range cmd 3:0:3eb0:f00:5
[   10.287524] hda-codec: out of range cmd 3:0:3eb1:f00:5
[   10.287527] hda-codec: out of range cmd 3:0:3eb2:f00:5
[   10.287529] hda-codec: out of range cmd 3:0:3eb3:f00:5
[   10.287533] hda-codec: out of range cmd 3:0:3eb4:f00:5
[   10.287535] hda-codec: out of range cmd 3:0:3eb5:f00:5
[   10.287537] hda-codec: out of range cmd 3:0:3eb6:f00:5
[   10.287540] hda-codec: out of range cmd 3:0:3eb7:f00:5
[   10.287543] hda-codec: out of range cmd 3:0:3eb8:f00:5
[   10.287546] hda-codec: out of range cmd 3:0:3eb9:f00:5
[   10.287549] hda-codec: out of range cmd 3:0:3eba:f00:5
[   10.287552] hda-codec: out of range cmd 3:0:3ebb:f00:5
[   10.287555] hda-codec: out of range cmd 3:0:3ebc:f00:5
[   10.287559] hda-codec: out of range cmd 3:0:3ebd:f00:5
[   10.287563] hda-codec: out of range cmd 3:0:3ebe:f00:5
[   10.287565] hda-codec: out of range cmd 3:0:3ebf:f00:5
[   10.287568] hda-codec: out of range cmd 3:0:3ec0:f00:5
[   10.287572] hda-codec: out of range cmd 3:0:3ec1:f00:5
[   10.287577] hda-codec: out of range cmd 3:0:3ec2:f00:5
[   10.287580] hda-codec: out of range cmd 3:0:3ec3:f00:5
[   10.287582] hda-codec: out of range cmd 3:0:3ec4:f00:5
[   10.287584] hda-codec: out of range cmd 3:0:3ec5:f00:5
[   10.287586] hda-codec: out of range cmd 3:0:3ec6:f00:5
[   10.287588] hda-codec: out of range cmd 3:0:3ec7:f00:5
[   10.287591] hda-codec: out of range cmd 3:0:3ec8:f00:5
[   10.287593] hda-codec: out of range cmd 3:0:3ec9:f00:5
[   10.287595] hda-codec: out of range cmd 3:0:3eca:f00:5
[   10.287597] hda-codec: out of range cmd 3:0:3ecb:f00:5
[   10.287599] hda-codec: out of range cmd 3:0:3ecc:f00:5
[   10.287601] hda-codec: out of range cmd 3:0:3ecd:f00:5
[   10.287605] hda-codec: out of range cmd 3:0:3ece:f00:5
[   10.287607] hda-codec: out of range cmd 3:0:3ecf:f00:5
[   10.287609] hda-codec: out of range cmd 3:0:3ed0:f00:5
[   10.287612] hda-codec: out of range cmd 3:0:3ed1:f00:5
[   10.287614] hda-codec: out of range cmd 3:0:3ed2:f00:5
[   10.287617] hda-codec: out of range cmd 3:0:3ed3:f00:5
[   10.287619] hda-codec: out of range cmd 3:0:3ed4:f00:5
[   10.287622] hda-codec: out of range cmd 3:0:3ed5:f00:5
[   10.287624] hda-codec: out of range cmd 3:0:3ed6:f00:5
[   10.287626] hda-codec: out of range cmd 3:0:3ed7:f00:5
[   10.287629] hda-codec: out of range cmd 3:0:3ed8:f00:5
[   10.287632] hda-codec: out of range cmd 3:0:3ed9:f00:5
[   10.287634] hda-codec: out of range cmd 3:0:3eda:f00:5
[   10.287636] hda-codec: out of range cmd 3:0:3edb:f00:5
[   10.287638] hda-codec: out of range cmd 3:0:3edc:f00:5
[   10.287641] hda-codec: out of range cmd 3:0:3edd:f00:5
[   10.287643] hda-codec: out of range cmd 3:0:3ede:f00:5
[   10.287645] hda-codec: out of range cmd 3:0:3edf:f00:5
[   10.287647] hda-codec: out of range cmd 3:0:3ee0:f00:5
[   10.287651] hda-codec: out of range cmd 3:0:3ee1:f00:5
[   10.287653] hda-codec: out of range cmd 3:0:3ee2:f00:5
[   10.287657] hda-codec: out of range cmd 3:0:3ee3:f00:5
[   10.287661] hda-codec: out of range cmd 3:0:3ee4:f00:5
[   10.287664] hda-codec: out of range cmd 3:0:3ee5:f00:5
[   10.287669] hda-codec: out of range cmd 3:0:3ee6:f00:5
[   10.287673] hda-codec: out of range cmd 3:0:3ee7:f00:5
[   10.287676] hda-codec: out of range cmd 3:0:3ee8:f00:5
[   10.287679] hda-codec: out of range cmd 3:0:3ee9:f00:5
[   10.287682] hda-codec: out of range cmd 3:0:3eea:f00:5
[   10.287685] hda-codec: out of range cmd 3:0:3eeb:f00:5
[   10.287688] hda-codec: out of range cmd 3:0:3eec:f00:5
[   10.287690] hda-codec: out of range cmd 3:0:3eed:f00:5
[   10.287692] hda-codec: out of range cmd 3:0:3eee:f00:5
[   10.287694] hda-codec: out of range cmd 3:0:3eef:f00:5
[   10.287697] hda-codec: out of range cmd 3:0:3ef0:f00:5
[   10.287699] hda-codec: out of range cmd 3:0:3ef1:f00:5
[   10.287702] hda-codec: out of range cmd 3:0:3ef2:f00:5
[   10.287706] hda-codec: out of range cmd 3:0:3ef3:f00:5
[   10.287709] hda-codec: out of range cmd 3:0:3ef4:f00:5
[   10.287712] hda-codec: out of range cmd 3:0:3ef5:f00:5
[   10.287714] hda-codec: out of range cmd 3:0:3ef6:f00:5
[   10.287716] hda-codec: out of range cmd 3:0:3ef7:f00:5
[   10.287719] hda-codec: out of range cmd 3:0:3ef8:f00:5
[   10.287722] hda-codec: out of range cmd 3:0:3ef9:f00:5
[   10.287724] hda-codec: out of range cmd 3:0:3efa:f00:5
[   10.287727] hda-codec: out of range cmd 3:0:3efb:f00:5
[   10.287729] hda-codec: out of range cmd 3:0:3efc:f00:5
[   10.287732] hda-codec: out of range cmd 3:0:3efd:f00:5
[   10.287736] hda-codec: out of range cmd 3:0:3efe:f00:5
[   10.287739] hda-codec: out of range cmd 3:0:3eff:f00:5
[   10.287742] hda-codec: out of range cmd 3:0:3f00:f00:5
[   10.287745] hda-codec: out of range cmd 3:0:3f01:f00:5
[   10.287747] hda-codec: out of range cmd 3:0:3f02:f00:5
[   10.287751] hda-codec: out of range cmd 3:0:3f03:f00:5
[   10.287755] hda-codec: out of range cmd 3:0:3f04:f00:5
[   10.287760] hda-codec: out of range cmd 3:0:3f05:f00:5
[   10.287762] hda-codec: out of range cmd 3:0:3f06:f00:5
[   10.287766] hda-codec: out of range cmd 3:0:3f07:f00:5
[   10.287770] hda-codec: out of range cmd 3:0:3f08:f00:5
[   10.287773] hda-codec: out of range cmd 3:0:3f09:f00:5
[   10.287776] hda-codec: out of range cmd 3:0:3f0a:f00:5
[   10.287779] hda-codec: out of range cmd 3:0:3f0b:f00:5
[   10.287781] hda-codec: out of range cmd 3:0:3f0c:f00:5
[   10.287783] hda-codec: out of range cmd 3:0:3f0d:f00:5
[   10.287786] hda-codec: out of range cmd 3:0:3f0e:f00:5
[   10.287788] hda-codec: out of range cmd 3:0:3f0f:f00:5
[   10.287790] hda-codec: out of range cmd 3:0:3f10:f00:5
[   10.287794] hda-codec: out of range cmd 3:0:3f11:f00:5
[   10.287798] hda-codec: out of range cmd 3:0:3f12:f00:5
[   10.287800] hda-codec: out of range cmd 3:0:3f13:f00:5
[   10.287803] hda-codec: out of range cmd 3:0:3f14:f00:5
[   10.287805] hda-codec: out of range cmd 3:0:3f15:f00:5
[   10.287808] hda-codec: out of range cmd 3:0:3f16:f00:5
[   10.287811] hda-codec: out of range cmd 3:0:3f17:f00:5
[   10.287813] hda-codec: out of range cmd 3:0:3f18:f00:5
[   10.287816] hda-codec: out of range cmd 3:0:3f19:f00:5
[   10.287818] hda-codec: out of range cmd 3:0:3f1a:f00:5
[   10.287820] hda-codec: out of range cmd 3:0:3f1b:f00:5
[   10.287822] hda-codec: out of range cmd 3:0:3f1c:f00:5
[   10.287824] hda-codec: out of range cmd 3:0:3f1d:f00:5
[   10.287827] hda-codec: out of range cmd 3:0:3f1e:f00:5
[   10.287830] hda-codec: out of range cmd 3:0:3f1f:f00:5
[   10.287832] hda-codec: out of range cmd 3:0:3f20:f00:5
[   10.287836] hda-codec: out of range cmd 3:0:3f21:f00:5
[   10.287839] hda-codec: out of range cmd 3:0:3f22:f00:5
[   10.287842] hda-codec: out of range cmd 3:0:3f23:f00:5
[   10.287846] hda-codec: out of range cmd 3:0:3f24:f00:5
[   10.287850] hda-codec: out of range cmd 3:0:3f25:f00:5
[   10.287854] hda-codec: out of range cmd 3:0:3f26:f00:5
[   10.287857] hda-codec: out of range cmd 3:0:3f27:f00:5
[   10.287859] hda-codec: out of range cmd 3:0:3f28:f00:5
[   10.287863] hda-codec: out of range cmd 3:0:3f29:f00:5
[   10.287866] hda-codec: out of range cmd 3:0:3f2a:f00:5
[   10.287869] hda-codec: out of range cmd 3:0:3f2b:f00:5
[   10.287872] hda-codec: out of range cmd 3:0:3f2c:f00:5
[   10.287875] hda-codec: out of range cmd 3:0:3f2d:f00:5
[   10.287877] hda-codec: out of range cmd 3:0:3f2e:f00:5
[   10.287879] hda-codec: out of range cmd 3:0:3f2f:f00:5
[   10.287882] hda-codec: out of range cmd 3:0:3f30:f00:5
[   10.287884] hda-codec: out of range cmd 3:0:3f31:f00:5
[   10.287887] hda-codec: out of range cmd 3:0:3f32:f00:5
[   10.287889] hda-codec: out of range cmd 3:0:3f33:f00:5
[   10.287893] hda-codec: out of range cmd 3:0:3f34:f00:5
[   10.287896] hda-codec: out of range cmd 3:0:3f35:f00:5
[   10.287899] hda-codec: out of range cmd 3:0:3f36:f00:5
[   10.287901] hda-codec: out of range cmd 3:0:3f37:f00:5
[   10.287903] hda-codec: out of range cmd 3:0:3f38:f00:5
[   10.287909] hda-codec: out of range cmd 3:0:3f39:f00:5
[   10.287913] hda-codec: out of range cmd 3:0:3f3a:f00:5
[   10.287918] hda-codec: out of range cmd 3:0:3f3b:f00:5
[   10.287922] hda-codec: out of range cmd 3:0:3f3c:f00:5
[   10.287925] hda-codec: out of range cmd 3:0:3f3d:f00:5
[   10.287928] hda-codec: out of range cmd 3:0:3f3e:f00:5
[   10.287931] hda-codec: out of range cmd 3:0:3f3f:f00:5
[   10.287933] hda-codec: out of range cmd 3:0:3f40:f00:5
[   10.287936] hda-codec: out of range cmd 3:0:3f41:f00:5
[   10.287938] hda-codec: out of range cmd 3:0:3f42:f00:5
[   10.287942] hda-codec: out of range cmd 3:0:3f43:f00:5
[   10.287946] hda-codec: out of range cmd 3:0:3f44:f00:5
[   10.287948] hda-codec: out of range cmd 3:0:3f45:f00:5
[   10.287952] hda-codec: out of range cmd 3:0:3f46:f00:5
[   10.287954] hda-codec: out of range cmd 3:0:3f47:f00:5
[   10.287958] hda-codec: out of range cmd 3:0:3f48:f00:5
[   10.287961] hda-codec: out of range cmd 3:0:3f49:f00:5
[   10.287964] hda-codec: out of range cmd 3:0:3f4a:f00:5
[   10.287966] hda-codec: out of range cmd 3:0:3f4b:f00:5
[   10.287968] hda-codec: out of range cmd 3:0:3f4c:f00:5
[   10.287972] hda-codec: out of range cmd 3:0:3f4d:f00:5
[   10.287976] hda-codec: out of range cmd 3:0:3f4e:f00:5
[   10.287978] hda-codec: out of range cmd 3:0:3f4f:f00:5
[   10.287981] hda-codec: out of range cmd 3:0:3f50:f00:5
[   10.287983] hda-codec: out of range cmd 3:0:3f51:f00:5
[   10.287986] hda-codec: out of range cmd 3:0:3f52:f00:5
[   10.287989] hda-codec: out of range cmd 3:0:3f53:f00:5
[   10.288020] hda-codec: out of range cmd 3:0:3f54:f00:5
[   10.288023] hda-codec: out of range cmd 3:0:3f55:f00:5
[   10.288027] hda-codec: out of range cmd 3:0:3f56:f00:5
[   10.288030] hda-codec: out of range cmd 3:0:3f57:f00:5
[   10.288032] hda-codec: out of range cmd 3:0:3f58:f00:5
[   10.288035] hda-codec: out of range cmd 3:0:3f59:f00:5
[   10.288038] hda-codec: out of range cmd 3:0:3f5a:f00:5
[   10.288040] hda-codec: out of range cmd 3:0:3f5b:f00:5
[   10.288044] hda-codec: out of range cmd 3:0:3f5c:f00:5
[   10.288046] hda-codec: out of range cmd 3:0:3f5d:f00:5
[   10.288049] hda-codec: out of range cmd 3:0:3f5e:f00:5
[   10.288053] hda-codec: out of range cmd 3:0:3f5f:f00:5
[   10.288056] hda-codec: out of range cmd 3:0:3f60:f00:5
[   10.288058] hda-codec: out of range cmd 3:0:3f61:f00:5
[   10.288060] hda-codec: out of range cmd 3:0:3f62:f00:5
[   10.288062] hda-codec: out of range cmd 3:0:3f63:f00:5
[   10.288066] hda-codec: out of range cmd 3:0:3f64:f00:5
[   10.288069] hda-codec: out of range cmd 3:0:3f65:f00:5
[   10.288072] hda-codec: out of range cmd 3:0:3f66:f00:5
[   10.288075] hda-codec: out of range cmd 3:0:3f67:f00:5
[   10.288078] hda-codec: out of range cmd 3:0:3f68:f00:5
[   10.288080] hda-codec: out of range cmd 3:0:3f69:f00:5
[   10.288084] hda-codec: out of range cmd 3:0:3f6a:f00:5
[   10.288089] hda-codec: out of range cmd 3:0:3f6b:f00:5
[   10.288091] hda-codec: out of range cmd 3:0:3f6c:f00:5
[   10.288094] hda-codec: out of range cmd 3:0:3f6d:f00:5
[   10.288096] hda-codec: out of range cmd 3:0:3f6e:f00:5
[   10.288099] hda-codec: out of range cmd 3:0:3f6f:f00:5
[   10.288104] hda-codec: out of range cmd 3:0:3f70:f00:5
[   10.288106] hda-codec: out of range cmd 3:0:3f71:f00:5
[   10.288110] hda-codec: out of range cmd 3:0:3f72:f00:5
[   10.288114] hda-codec: out of range cmd 3:0:3f73:f00:5
[   10.288117] hda-codec: out of range cmd 3:0:3f74:f00:5
[   10.288120] hda-codec: out of range cmd 3:0:3f75:f00:5
[   10.288123] hda-codec: out of range cmd 3:0:3f76:f00:5
[   10.288125] hda-codec: out of range cmd 3:0:3f77:f00:5
[   10.288128] hda-codec: out of range cmd 3:0:3f78:f00:5
[   10.288131] hda-codec: out of range cmd 3:0:3f79:f00:5
[   10.288133] hda-codec: out of range cmd 3:0:3f7a:f00:5
[   10.288135] hda-codec: out of range cmd 3:0:3f7b:f00:5
[   10.288137] hda-codec: out of range cmd 3:0:3f7c:f00:5
[   10.288140] hda-codec: out of range cmd 3:0:3f7d:f00:5
[   10.288144] hda-codec: out of range cmd 3:0:3f7e:f00:5
[   10.288146] hda-codec: out of range cmd 3:0:3f7f:f00:5
[   10.288149] hda-codec: out of range cmd 3:0:3f80:f00:5
[   10.288152] hda-codec: out of range cmd 3:0:3f81:f00:5
[   10.288155] hda-codec: out of range cmd 3:0:3f82:f00:5
[   10.288160] hda-codec: out of range cmd 3:0:3f83:f00:5
[   10.288163] hda-codec: out of range cmd 3:0:3f84:f00:5
[   10.288166] hda-codec: out of range cmd 3:0:3f85:f00:5
[   10.288168] hda-codec: out of range cmd 3:0:3f86:f00:5
[   10.288171] hda-codec: out of range cmd 3:0:3f87:f00:5
[   10.288175] hda-codec: out of range cmd 3:0:3f88:f00:5
[   10.288178] hda-codec: out of range cmd 3:0:3f89:f00:5
[   10.288180] hda-codec: out of range cmd 3:0:3f8a:f00:5
[   10.288183] hda-codec: out of range cmd 3:0:3f8b:f00:5
[   10.288185] hda-codec: out of range cmd 3:0:3f8c:f00:5
[   10.288187] hda-codec: out of range cmd 3:0:3f8d:f00:5
[   10.288191] hda-codec: out of range cmd 3:0:3f8e:f00:5
[   10.288193] hda-codec: out of range cmd 3:0:3f8f:f00:5
[   10.288196] hda-codec: out of range cmd 3:0:3f90:f00:5
[   10.288198] hda-codec: out of range cmd 3:0:3f91:f00:5
[   10.288201] hda-codec: out of range cmd 3:0:3f92:f00:5
[   10.288203] hda-codec: out of range cmd 3:0:3f93:f00:5
[   10.288206] hda-codec: out of range cmd 3:0:3f94:f00:5
[   10.288208] hda-codec: out of range cmd 3:0:3f95:f00:5
[   10.288212] hda-codec: out of range cmd 3:0:3f96:f00:5
[   10.288214] hda-codec: out of range cmd 3:0:3f97:f00:5
[   10.288219] hda-codec: out of range cmd 3:0:3f98:f00:5
[   10.288224] hda-codec: out of range cmd 3:0:3f99:f00:5
[   10.288227] hda-codec: out of range cmd 3:0:3f9a:f00:5
[   10.288230] hda-codec: out of range cmd 3:0:3f9b:f00:5
[   10.288232] hda-codec: out of range cmd 3:0:3f9c:f00:5
[   10.288235] hda-codec: out of range cmd 3:0:3f9d:f00:5
[   10.288241] hda-codec: out of range cmd 3:0:3f9e:f00:5
[   10.288244] hda-codec: out of range cmd 3:0:3f9f:f00:5
[   10.288246] hda-codec: out of range cmd 3:0:3fa0:f00:5
[   10.288248] hda-codec: out of range cmd 3:0:3fa1:f00:5
[   10.288251] hda-codec: out of range cmd 3:0:3fa2:f00:5
[   10.288254] hda-codec: out of range cmd 3:0:3fa3:f00:5
[   10.288256] hda-codec: out of range cmd 3:0:3fa4:f00:5
[   10.288259] hda-codec: out of range cmd 3:0:3fa5:f00:5
[   10.288261] hda-codec: out of range cmd 3:0:3fa6:f00:5
[   10.288264] hda-codec: out of range cmd 3:0:3fa7:f00:5
[   10.288268] hda-codec: out of range cmd 3:0:3fa8:f00:5
[   10.288271] hda-codec: out of range cmd 3:0:3fa9:f00:5
[   10.288274] hda-codec: out of range cmd 3:0:3faa:f00:5
[   10.288276] hda-codec: out of range cmd 3:0:3fab:f00:5
[   10.288278] hda-codec: out of range cmd 3:0:3fac:f00:5
[   10.288281] hda-codec: out of range cmd 3:0:3fad:f00:5
[   10.288284] hda-codec: out of range cmd 3:0:3fae:f00:5
[   10.288287] hda-codec: out of range cmd 3:0:3faf:f00:5
[   10.288289] hda-codec: out of range cmd 3:0:3fb0:f00:5
[   10.288291] hda-codec: out of range cmd 3:0:3fb1:f00:5
[   10.288297] hda-codec: out of range cmd 3:0:3fb2:f00:5
[   10.288301] hda-codec: out of range cmd 3:0:3fb3:f00:5
[   10.288303] hda-codec: out of range cmd 3:0:3fb4:f00:5
[   10.288306] hda-codec: out of range cmd 3:0:3fb5:f00:5
[   10.288308] hda-codec: out of range cmd 3:0:3fb6:f00:5
[   10.288311] hda-codec: out of range cmd 3:0:3fb7:f00:5
[   10.288314] hda-codec: out of range cmd 3:0:3fb8:f00:5
[   10.288318] hda-codec: out of range cmd 3:0:3fb9:f00:5
[   10.288320] hda-codec: out of range cmd 3:0:3fba:f00:5
[   10.288324] hda-codec: out of range cmd 3:0:3fbb:f00:5
[   10.288327] hda-codec: out of range cmd 3:0:3fbc:f00:5
[   10.288330] hda-codec: out of range cmd 3:0:3fbd:f00:5
[   10.288334] hda-codec: out of range cmd 3:0:3fbe:f00:5
[   10.288337] hda-codec: out of range cmd 3:0:3fbf:f00:5
[   10.288340] hda-codec: out of range cmd 3:0:3fc0:f00:5
[   10.288342] hda-codec: out of range cmd 3:0:3fc1:f00:5
[   10.288346] hda-codec: out of range cmd 3:0:3fc2:f00:5
[   10.288350] hda-codec: out of range cmd 3:0:3fc3:f00:5
[   10.288353] hda-codec: out of range cmd 3:0:3fc4:f00:5
[   10.288356] hda-codec: out of range cmd 3:0:3fc5:f00:5
[   10.288358] hda-codec: out of range cmd 3:0:3fc6:f00:5
[   10.288363] hda-codec: out of range cmd 3:0:3fc7:f00:5
[   10.288366] hda-codec: out of range cmd 3:0:3fc8:f00:5
[   10.288370] hda-codec: out of range cmd 3:0:3fc9:f00:5
[   10.288372] hda-codec: out of range cmd 3:0:3fca:f00:5
[   10.288374] hda-codec: out of range cmd 3:0:3fcb:f00:5
[   10.288376] hda-codec: out of range cmd 3:0:3fcc:f00:5
[   10.288379] hda-codec: out of range cmd 3:0:3fcd:f00:5
[   10.288381] hda-codec: out of range cmd 3:0:3fce:f00:5
[   10.288383] hda-codec: out of range cmd 3:0:3fcf:f00:5
[   10.288386] hda-codec: out of range cmd 3:0:3fd0:f00:5
[   10.288389] hda-codec: out of range cmd 3:0:3fd1:f00:5
[   10.288394] hda-codec: out of range cmd 3:0:3fd2:f00:5
[   10.288396] hda-codec: out of range cmd 3:0:3fd3:f00:5
[   10.288400] hda-codec: out of range cmd 3:0:3fd4:f00:5
[   10.288402] hda-codec: out of range cmd 3:0:3fd5:f00:5
[   10.288405] hda-codec: out of range cmd 3:0:3fd6:f00:5
[   10.288407] hda-codec: out of range cmd 3:0:3fd7:f00:5
[   10.288411] hda-codec: out of range cmd 3:0:3fd8:f00:5
[   10.288413] hda-codec: out of range cmd 3:0:3fd9:f00:5
[   10.288417] hda-codec: out of range cmd 3:0:3fda:f00:5
[   10.288421] hda-codec: out of range cmd 3:0:3fdb:f00:5
[   10.288424] hda-codec: out of range cmd 3:0:3fdc:f00:5
[   10.288426] hda-codec: out of range cmd 3:0:3fdd:f00:5
[   10.288429] hda-codec: out of range cmd 3:0:3fde:f00:5
[   10.288432] hda-codec: out of range cmd 3:0:3fdf:f00:5
[   10.288436] hda-codec: out of range cmd 3:0:3fe0:f00:5
[   10.288439] hda-codec: out of range cmd 3:0:3fe1:f00:5
[   10.288442] hda-codec: out of range cmd 3:0:3fe2:f00:5
[   10.288445] hda-codec: out of range cmd 3:0:3fe3:f00:5
[   10.288447] hda-codec: out of range cmd 3:0:3fe4:f00:5
[   10.288450] hda-codec: out of range cmd 3:0:3fe5:f00:5
[   10.288453] hda-codec: out of range cmd 3:0:3fe6:f00:5
[   10.288456] hda-codec: out of range cmd 3:0:3fe7:f00:5
[   10.288459] hda-codec: out of range cmd 3:0:3fe8:f00:5
[   10.288462] hda-codec: out of range cmd 3:0:3fe9:f00:5
[   10.288465] hda-codec: out of range cmd 3:0:3fea:f00:5
[   10.288467] hda-codec: out of range cmd 3:0:3feb:f00:5
[   10.288470] hda-codec: out of range cmd 3:0:3fec:f00:5
[   10.288473] hda-codec: out of range cmd 3:0:3fed:f00:5
[   10.288475] hda-codec: out of range cmd 3:0:3fee:f00:5
[   10.288479] hda-codec: out of range cmd 3:0:3fef:f00:5
[   10.288481] hda-codec: out of range cmd 3:0:3ff0:f00:5
[   10.288483] hda-codec: out of range cmd 3:0:3ff1:f00:5
[   10.288486] hda-codec: out of range cmd 3:0:3ff2:f00:5
[   10.288489] hda-codec: out of range cmd 3:0:3ff3:f00:5
[   10.288492] hda-codec: out of range cmd 3:0:3ff4:f00:5
[   10.288494] hda-codec: out of range cmd 3:0:3ff5:f00:5
[   10.288497] hda-codec: out of range cmd 3:0:3ff6:f00:5
[   10.288500] hda-codec: out of range cmd 3:0:3ff7:f00:5
[   10.288503] hda-codec: out of range cmd 3:0:3ff8:f00:5
[   10.288506] hda-codec: out of range cmd 3:0:3ff9:f00:5
[   10.288509] hda-codec: out of range cmd 3:0:3ffa:f00:5
[   10.288511] hda-codec: out of range cmd 3:0:3ffb:f00:5
[   10.288515] hda-codec: out of range cmd 3:0:3ffc:f00:5
[   10.288517] hda-codec: out of range cmd 3:0:3ffd:f00:5
[   10.288519] hda-codec: out of range cmd 3:0:3ffe:f00:5
[   10.288521] hda-codec: out of range cmd 3:0:3fff:f00:5
[   10.288526] hda-codec: out of range cmd 3:0:4000:f00:5
[   10.288529] hda-codec: out of range cmd 3:0:4001:f00:5
[   10.288531] hda-codec: out of range cmd 3:0:4002:f00:5
[   10.288534] hda-codec: out of range cmd 3:0:4003:f00:5
[   10.288536] hda-codec: out of range cmd 3:0:4004:f00:5
[   10.288538] hda-codec: out of range cmd 3:0:4005:f00:5
[   10.288540] hda-codec: out of range cmd 3:0:4006:f00:5
[   10.288543] hda-codec: out of range cmd 3:0:4007:f00:5
[   10.288545] hda-codec: out of range cmd 3:0:4008:f00:5
[   10.288547] hda-codec: out of range cmd 3:0:4009:f00:5
[   10.288550] hda-codec: out of range cmd 3:0:400a:f00:5
[   10.288553] hda-codec: out of range cmd 3:0:400b:f00:5
[   10.288555] hda-codec: out of range cmd 3:0:400c:f00:5
[   10.288558] hda-codec: out of range cmd 3:0:400d:f00:5
[   10.288560] hda-codec: out of range cmd 3:0:400e:f00:5
[   10.288562] hda-codec: out of range cmd 3:0:400f:f00:5
[   10.288564] hda-codec: out of range cmd 3:0:4010:f00:5
[   10.288567] hda-codec: out of range cmd 3:0:4011:f00:5
[   10.288569] hda-codec: out of range cmd 3:0:4012:f00:5
[   10.288572] hda-codec: out of range cmd 3:0:4013:f00:5
[   10.288574] hda-codec: out of range cmd 3:0:4014:f00:5
[   10.288576] hda-codec: out of range cmd 3:0:4015:f00:5
[   10.288579] hda-codec: out of range cmd 3:0:4016:f00:5
[   10.288581] hda-codec: out of range cmd 3:0:4017:f00:5
[   10.288584] hda-codec: out of range cmd 3:0:4018:f00:5
[   10.288597] hda-codec: out of range cmd 3:0:4019:f00:5
[   10.288599] hda-codec: out of range cmd 3:0:401a:f00:5
[   10.288602] hda-codec: out of range cmd 3:0:401b:f00:5
[   10.288604] hda-codec: out of range cmd 3:0:401c:f00:5
[   10.288607] hda-codec: out of range cmd 3:0:401d:f00:5
[   10.288610] hda-codec: out of range cmd 3:0:401e:f00:5
[   10.288613] hda-codec: out of range cmd 3:0:401f:f00:5
[   10.288615] hda-codec: out of range cmd 3:0:4020:f00:5
[   10.288619] hda-codec: out of range cmd 3:0:4021:f00:5
[   10.288621] hda-codec: out of range cmd 3:0:4022:f00:5
[   10.288625] hda-codec: out of range cmd 3:0:4023:f00:5
[   10.288627] hda-codec: out of range cmd 3:0:4024:f00:5
[   10.288629] hda-codec: out of range cmd 3:0:4025:f00:5
[   10.288631] hda-codec: out of range cmd 3:0:4026:f00:5
[   10.288634] hda-codec: out of range cmd 3:0:4027:f00:5
[   10.288637] hda-codec: out of range cmd 3:0:4028:f00:5
[   10.288640] hda-codec: out of range cmd 3:0:4029:f00:5
[   10.288644] hda-codec: out of range cmd 3:0:402a:f00:5
[   10.288647] hda-codec: out of range cmd 3:0:402b:f00:5
[   10.288650] hda-codec: out of range cmd 3:0:402c:f00:5
[   10.288652] hda-codec: out of range cmd 3:0:402d:f00:5
[   10.288654] hda-codec: out of range cmd 3:0:402e:f00:5
[   10.288657] hda-codec: out of range cmd 3:0:402f:f00:5
[   10.288660] hda-codec: out of range cmd 3:0:4030:f00:5
[   10.288662] hda-codec: out of range cmd 3:0:4031:f00:5
[   10.288665] hda-codec: out of range cmd 3:0:4032:f00:5
[   10.288667] hda-codec: out of range cmd 3:0:4033:f00:5
[   10.288670] hda-codec: out of range cmd 3:0:4034:f00:5
[   10.288676] hda-codec: out of range cmd 3:0:4035:f00:5
[   10.288679] hda-codec: out of range cmd 3:0:4036:f00:5
[   10.288681] hda-codec: out of range cmd 3:0:4037:f00:5
[   10.288684] hda-codec: out of range cmd 3:0:4038:f00:5
[   10.288686] hda-codec: out of range cmd 3:0:4039:f00:5
[   10.288690] hda-codec: out of range cmd 3:0:403a:f00:5
[   10.288693] hda-codec: out of range cmd 3:0:403b:f00:5
[   10.288696] hda-codec: out of range cmd 3:0:403c:f00:5
[   10.288700] hda-codec: out of range cmd 3:0:403d:f00:5
[   10.288702] hda-codec: out of range cmd 3:0:403e:f00:5
[   10.288706] hda-codec: out of range cmd 3:0:403f:f00:5
[   10.288710] hda-codec: out of range cmd 3:0:4040:f00:5
[   10.288712] hda-codec: out of range cmd 3:0:4041:f00:5
[   10.288715] hda-codec: out of range cmd 3:0:4042:f00:5
[   10.288717] hda-codec: out of range cmd 3:0:4043:f00:5
[   10.288719] hda-codec: out of range cmd 3:0:4044:f00:5
[   10.288721] hda-codec: out of range cmd 3:0:4045:f00:5
[   10.288724] hda-codec: out of range cmd 3:0:4046:f00:5
[   10.288726] hda-codec: out of range cmd 3:0:4047:f00:5
[   10.288728] hda-codec: out of range cmd 3:0:4048:f00:5
[   10.288732] hda-codec: out of range cmd 3:0:4049:f00:5
[   10.288735] hda-codec: out of range cmd 3:0:404a:f00:5
[   10.288737] hda-codec: out of range cmd 3:0:404b:f00:5
[   10.288740] hda-codec: out of range cmd 3:0:404c:f00:5
[   10.288742] hda-codec: out of range cmd 3:0:404d:f00:5
[   10.288746] hda-codec: out of range cmd 3:0:404e:f00:5
[   10.288749] hda-codec: out of range cmd 3:0:404f:f00:5
[   10.288751] hda-codec: out of range cmd 3:0:4050:f00:5
[   10.288754] hda-codec: out of range cmd 3:0:4051:f00:5
[   10.288756] hda-codec: out of range cmd 3:0:4052:f00:5
[   10.288758] hda-codec: out of range cmd 3:0:4053:f00:5
[   10.288760] hda-codec: out of range cmd 3:0:4054:f00:5
[   10.288762] hda-codec: out of range cmd 3:0:4055:f00:5
[   10.288765] hda-codec: out of range cmd 3:0:4056:f00:5
[   10.288767] hda-codec: out of range cmd 3:0:4057:f00:5
[   10.288769] hda-codec: out of range cmd 3:0:4058:f00:5
[   10.288774] hda-codec: out of range cmd 3:0:4059:f00:5
[   10.288778] hda-codec: out of range cmd 3:0:405a:f00:5
[   10.288782] hda-codec: out of range cmd 3:0:405b:f00:5
[   10.288786] hda-codec: out of range cmd 3:0:405c:f00:5
[   10.288789] hda-codec: out of range cmd 3:0:405d:f00:5
[   10.288792] hda-codec: out of range cmd 3:0:405e:f00:5
[   10.288795] hda-codec: out of range cmd 3:0:405f:f00:5
[   10.288797] hda-codec: out of range cmd 3:0:4060:f00:5
[   10.288800] hda-codec: out of range cmd 3:0:4061:f00:5
[   10.288804] hda-codec: out of range cmd 3:0:4062:f00:5
[   10.288807] hda-codec: out of range cmd 3:0:4063:f00:5
[   10.288810] hda-codec: out of range cmd 3:0:4064:f00:5
[   10.288812] hda-codec: out of range cmd 3:0:4065:f00:5
[   10.288814] hda-codec: out of range cmd 3:0:4066:f00:5
[   10.288818] hda-codec: out of range cmd 3:0:4067:f00:5
[   10.288820] hda-codec: out of range cmd 3:0:4068:f00:5
[   10.288823] hda-codec: out of range cmd 3:0:4069:f00:5
[   10.288825] hda-codec: out of range cmd 3:0:406a:f00:5
[   10.288828] hda-codec: out of range cmd 3:0:406b:f00:5
[   10.288833] hda-codec: out of range cmd 3:0:406c:f00:5
[   10.288836] hda-codec: out of range cmd 3:0:406d:f00:5
[   10.288838] hda-codec: out of range cmd 3:0:406e:f00:5
[   10.288840] hda-codec: out of range cmd 3:0:406f:f00:5
[   10.288843] hda-codec: out of range cmd 3:0:4070:f00:5
[   10.288848] hda-codec: out of range cmd 3:0:4071:f00:5
[   10.288852] hda-codec: out of range cmd 3:0:4072:f00:5
[   10.288856] hda-codec: out of range cmd 3:0:4073:f00:5
[   10.288859] hda-codec: out of range cmd 3:0:4074:f00:5
[   10.288861] hda-codec: out of range cmd 3:0:4075:f00:5
[   10.288865] hda-codec: out of range cmd 3:0:4076:f00:5
[   10.288869] hda-codec: out of range cmd 3:0:4077:f00:5
[   10.288871] hda-codec: out of range cmd 3:0:4078:f00:5
[   10.288874] hda-codec: out of range cmd 3:0:4079:f00:5
[   10.288876] hda-codec: out of range cmd 3:0:407a:f00:5
[   10.288879] hda-codec: out of range cmd 3:0:407b:f00:5
[   10.288883] hda-codec: out of range cmd 3:0:407c:f00:5
[   10.288885] hda-codec: out of range cmd 3:0:407d:f00:5
[   10.288889] hda-codec: out of range cmd 3:0:407e:f00:5
[   10.288892] hda-codec: out of range cmd 3:0:407f:f00:5
[   10.288894] hda-codec: out of range cmd 3:0:4080:f00:5
[   10.288898] hda-codec: out of range cmd 3:0:4081:f00:5
[   10.288901] hda-codec: out of range cmd 3:0:4082:f00:5
[   10.288903] hda-codec: out of range cmd 3:0:4083:f00:5
[   10.288905] hda-codec: out of range cmd 3:0:4084:f00:5
[   10.288909] hda-codec: out of range cmd 3:0:4085:f00:5
[   10.288913] hda-codec: out of range cmd 3:0:4086:f00:5
[   10.288915] hda-codec: out of range cmd 3:0:4087:f00:5
[   10.288918] hda-codec: out of range cmd 3:0:4088:f00:5
[   10.288920] hda-codec: out of range cmd 3:0:4089:f00:5
[   10.288924] hda-codec: out of range cmd 3:0:408a:f00:5
[   10.288926] hda-codec: out of range cmd 3:0:408b:f00:5
[   10.288929] hda-codec: out of range cmd 3:0:408c:f00:5
[   10.288933] hda-codec: out of range cmd 3:0:408d:f00:5
[   10.288935] hda-codec: out of range cmd 3:0:408e:f00:5
[   10.288937] hda-codec: out of range cmd 3:0:408f:f00:5
[   10.288941] hda-codec: out of range cmd 3:0:4090:f00:5
[   10.288944] hda-codec: out of range cmd 3:0:4091:f00:5
[   10.288948] hda-codec: out of range cmd 3:0:4092:f00:5
[   10.288952] hda-codec: out of range cmd 3:0:4093:f00:5
[   10.288954] hda-codec: out of range cmd 3:0:4094:f00:5
[   10.288956] hda-codec: out of range cmd 3:0:4095:f00:5
[   10.288959] hda-codec: out of range cmd 3:0:4096:f00:5
[   10.288961] hda-codec: out of range cmd 3:0:4097:f00:5
[   10.288963] hda-codec: out of range cmd 3:0:4098:f00:5
[   10.288966] hda-codec: out of range cmd 3:0:4099:f00:5
[   10.288968] hda-codec: out of range cmd 3:0:409a:f00:5
[   10.288973] hda-codec: out of range cmd 3:0:409b:f00:5
[   10.288976] hda-codec: out of range cmd 3:0:409c:f00:5
[   10.288979] hda-codec: out of range cmd 3:0:409d:f00:5
[   10.288982] hda-codec: out of range cmd 3:0:409e:f00:5
[   10.288984] hda-codec: out of range cmd 3:0:409f:f00:5
[   10.288987] hda-codec: out of range cmd 3:0:40a0:f00:5
[   10.288992] hda-codec: out of range cmd 3:0:40a1:f00:5
[   10.288995] hda-codec: out of range cmd 3:0:40a2:f00:5
[   10.288998] hda-codec: out of range cmd 3:0:40a3:f00:5
[   10.289000] hda-codec: out of range cmd 3:0:40a4:f00:5
[   10.289004] hda-codec: out of range cmd 3:0:40a5:f00:5
[   10.289007] hda-codec: out of range cmd 3:0:40a6:f00:5
[   10.289012] hda-codec: out of range cmd 3:0:40a7:f00:5
[   10.289014] hda-codec: out of range cmd 3:0:40a8:f00:5
[   10.289017] hda-codec: out of range cmd 3:0:40a9:f00:5
[   10.289019] hda-codec: out of range cmd 3:0:40aa:f00:5
[   10.289026] hda-codec: out of range cmd 3:0:40ab:f00:5
[   10.289028] hda-codec: out of range cmd 3:0:40ac:f00:5
[   10.289031] hda-codec: out of range cmd 3:0:40ad:f00:5
[   10.289035] hda-codec: out of range cmd 3:0:40ae:f00:5
[   10.289038] hda-codec: out of range cmd 3:0:40af:f00:5
[   10.289041] hda-codec: out of range cmd 3:0:40b0:f00:5
[   10.289045] hda-codec: out of range cmd 3:0:40b1:f00:5
[   10.289047] hda-codec: out of range cmd 3:0:40b2:f00:5
[   10.289050] hda-codec: out of range cmd 3:0:40b3:f00:5
[   10.289053] hda-codec: out of range cmd 3:0:40b4:f00:5
[   10.289055] hda-codec: out of range cmd 3:0:40b5:f00:5
[   10.289057] hda-codec: out of range cmd 3:0:40b6:f00:5
[   10.289060] hda-codec: out of range cmd 3:0:40b7:f00:5
[   10.289065] hda-codec: out of range cmd 3:0:40b8:f00:5
[   10.289068] hda-codec: out of range cmd 3:0:40b9:f00:5
[   10.289071] hda-codec: out of range cmd 3:0:40ba:f00:5
[   10.289074] hda-codec: out of range cmd 3:0:40bb:f00:5
[   10.289076] hda-codec: out of range cmd 3:0:40bc:f00:5
[   10.289082] hda-codec: out of range cmd 3:0:40bd:f00:5
[   10.289086] hda-codec: out of range cmd 3:0:40be:f00:5
[   10.289089] hda-codec: out of range cmd 3:0:40bf:f00:5
[   10.289092] hda-codec: out of range cmd 3:0:40c0:f00:5
[   10.289094] hda-codec: out of range cmd 3:0:40c1:f00:5
[   10.289097] hda-codec: out of range cmd 3:0:40c2:f00:5
[   10.289100] hda-codec: out of range cmd 3:0:40c3:f00:5
[   10.289103] hda-codec: out of range cmd 3:0:40c4:f00:5
[   10.289106] hda-codec: out of range cmd 3:0:40c5:f00:5
[   10.289108] hda-codec: out of range cmd 3:0:40c6:f00:5
[   10.289110] hda-codec: out of range cmd 3:0:40c7:f00:5
[   10.289113] hda-codec: out of range cmd 3:0:40c8:f00:5
[   10.289115] hda-codec: out of range cmd 3:0:40c9:f00:5
[   10.289118] hda-codec: out of range cmd 3:0:40ca:f00:5
[   10.289120] hda-codec: out of range cmd 3:0:40cb:f00:5
[   10.289122] hda-codec: out of range cmd 3:0:40cc:f00:5
[   10.289125] hda-codec: out of range cmd 3:0:40cd:f00:5
[   10.289127] hda-codec: out of range cmd 3:0:40ce:f00:5
[   10.289130] hda-codec: out of range cmd 3:0:40cf:f00:5
[   10.289133] hda-codec: out of range cmd 3:0:40d0:f00:5
[   10.289136] hda-codec: out of range cmd 3:0:40d1:f00:5
[   10.289138] hda-codec: out of range cmd 3:0:40d2:f00:5
[   10.289142] hda-codec: out of range cmd 3:0:40d3:f00:5
[   10.289148] hda-codec: out of range cmd 3:0:40d4:f00:5
[   10.289151] hda-codec: out of range cmd 3:0:40d5:f00:5
[   10.289153] hda-codec: out of range cmd 3:0:40d6:f00:5
[   10.289156] hda-codec: out of range cmd 3:0:40d7:f00:5
[   10.289159] hda-codec: out of range cmd 3:0:40d8:f00:5
[   10.289166] hda-codec: out of range cmd 3:0:40d9:f00:5
[   10.289168] hda-codec: out of range cmd 3:0:40da:f00:5
[   10.289171] hda-codec: out of range cmd 3:0:40db:f00:5
[   10.289174] hda-codec: out of range cmd 3:0:40dc:f00:5
[   10.289176] hda-codec: out of range cmd 3:0:40dd:f00:5
[   10.289178] hda-codec: out of range cmd 3:0:40de:f00:5
[   10.289181] hda-codec: out of range cmd 3:0:40df:f00:5
[   10.289183] hda-codec: out of range cmd 3:0:40e0:f00:5
[   10.289187] hda-codec: out of range cmd 3:0:40e1:f00:5
[   10.289189] hda-codec: out of range cmd 3:0:40e2:f00:5
[   10.289192] hda-codec: out of range cmd 3:0:40e3:f00:5
[   10.289196] hda-codec: out of range cmd 3:0:40e4:f00:5
[   10.289199] hda-codec: out of range cmd 3:0:40e5:f00:5
[   10.289201] hda-codec: out of range cmd 3:0:40e6:f00:5
[   10.289204] hda-codec: out of range cmd 3:0:40e7:f00:5
[   10.289206] hda-codec: out of range cmd 3:0:40e8:f00:5
[   10.289208] hda-codec: out of range cmd 3:0:40e9:f00:5
[   10.289210] hda-codec: out of range cmd 3:0:40ea:f00:5
[   10.289214] hda-codec: out of range cmd 3:0:40eb:f00:5
[   10.289216] hda-codec: out of range cmd 3:0:40ec:f00:5
[   10.289220] hda-codec: out of range cmd 3:0:40ed:f00:5
[   10.289226] hda-codec: out of range cmd 3:0:40ee:f00:5
[   10.289228] hda-codec: out of range cmd 3:0:40ef:f00:5
[   10.289231] hda-codec: out of range cmd 3:0:40f0:f00:5
[   10.289233] hda-codec: out of range cmd 3:0:40f1:f00:5
[   10.289237] hda-codec: out of range cmd 3:0:40f2:f00:5
[   10.289241] hda-codec: out of range cmd 3:0:40f3:f00:5
[   10.289243] hda-codec: out of range cmd 3:0:40f4:f00:5
[   10.289247] hda-codec: out of range cmd 3:0:40f5:f00:5
[   10.289251] hda-codec: out of range cmd 3:0:40f6:f00:5
[   10.289254] hda-codec: out of range cmd 3:0:40f7:f00:5
[   10.289258] hda-codec: out of range cmd 3:0:40f8:f00:5
[   10.289261] hda-codec: out of range cmd 3:0:40f9:f00:5
[   10.289263] hda-codec: out of range cmd 3:0:40fa:f00:5
[   10.289267] hda-codec: out of range cmd 3:0:40fb:f00:5
[   10.289269] hda-codec: out of range cmd 3:0:40fc:f00:5
[   10.289272] hda-codec: out of range cmd 3:0:40fd:f00:5
[   10.289276] hda-codec: out of range cmd 3:0:40fe:f00:5
[   10.289278] hda-codec: out of range cmd 3:0:40ff:f00:5
[   10.289281] hda-codec: out of range cmd 3:0:4100:f00:5
[   10.289283] hda-codec: out of range cmd 3:0:4101:f00:5
[   10.301352] hda-intel 0000:00:14.2: no codecs initialized
[   10.448743] type=1400 audit(1373805013.931:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=612 comm="apparmor_parser"

---

### Post by Yellow Pasque on 2013-07-14
I would encourage you to file a bug, as that will grab your whole dmesg (alsa-info only shows part of it because of the repetitive error), and also because it's a regression in a stable release.
```
ubuntu-bug audio
```

---

