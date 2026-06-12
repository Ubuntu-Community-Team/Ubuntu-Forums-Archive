---
title: "Realtek High Definition Audio not working"
date: 2009-05-09
forum: Hardware
---

### Post by acer8930 on 2009-05-09
I have an Acer Aspire 8930 laptop. Installed Ubuntu 9.04 jaunty whatever.

I get no sound. It doesn't say there is no audio device or driver or anything like that. The volume is maxed out and nothing still comes out. Selecting different options from "Preferences" doesn't give me any sound either.

I've tried installing the ALSA drivers (which I read could work). However, when I "make", I get a "alsa-patch: 24: patch not found" but when I navigate to the directory, the file "alsa-patch" is present.

Help is greatly apreciated as no working modem or audio really defeats the purpose for me to even experiment with Ubuntu or Linux really. Yeah, my modem doesn't work either, but I already posted a thread for that. 

This is the information I have for the device (used System Information for Windows):

[HTML]
Property	Value
Device ID	HDAUDIO\FUNC_01VEN_10ECDEV_0889SUBSYS_10250145REV_1000\432A4A68B00001
Status	0x0180200a Started
Problem	0x00000000 (0)
Service	IntcAzAudAddService
Capabilities	0x00000000
Config Flags	0x00000000
Class	MEDIA
Manufacturer	Realtek
Hardware IDs	HDAUDIO\FUNC_01VEN_10ECDEV_0889SUBSYS_10250145REV_1000
	HDAUDIO\FUNC_01VEN_10ECDEV_0889SUBSYS_10250145
Compatible IDs	HDAUDIO\FUNC_01CTLR_VEN_8086CTLR_DEV_293EVEN_10ECDEV_0889REV_1000
	HDAUDIO\FUNC_01CTLR_VEN_8086VEN_10ECDEV_0889REV_1000
	HDAUDIO\FUNC_01VEN_10ECDEV_0889REV_1000
	HDAUDIO\FUNC_01CTLR_VEN_8086CTLR_DEV_293EVEN_10ECDEV_0889
	HDAUDIO\FUNC_01CTLR_VEN_8086VEN_10ECDEV_0889
	HDAUDIO\FUNC_01VEN_10ECDEV_0889
	HDAUDIO\FUNC_01CTLR_VEN_8086CTLR_DEV_293EVEN_10EC
	HDAUDIO\FUNC_01CTLR_VEN_8086VEN_10EC
	HDAUDIO\FUNC_01VEN_10EC
	HDAUDIO\FUNC_01CTLR_VEN_8086CTLR_DEV_293E
	HDAUDIO\FUNC_01CTLR_VEN_8086
	HDAUDIO\FUNC_01GFVEN_10ECDEV_0889SUBSYS_10250145REV_1000
	HDAUDIO\FUNC_01
Class GUID	{4d36e96c-e325-11ce-bfc1-08002be10318}
Location	Internal High Definition Audio Bus
Bus number	0x00000000
Enumerator name	HDAUDIO
Description	Realtek High Definition Audio
Driver	{4d36e96c-e325-11ce-bfc1-08002be10318}\0007
Physical Object Name	\Device\00000073
UI number	0x00000000
Bustype GUID	{41203534-2037-3144-2042-422044362041}
Legacy bus type	0x00000005
Device Type	0x0000001d
Install State	0x00000000
Security	01 00 04 90 00 00 00 00 00 00 00 00 00 00 00 00 14 00 00 00 02 00 5C 00 04 00 00 00 00 00 14 00 00 00 00 10 01 01 00 00 00 00 00 05 12 00 00 00 00 00 18 00 00 00 00 E0 01 02 00 00 00 00 00 05 20 00 00 00 20 02 00 00 00 00 14 00 00 00 00 E0 01 01 00 00 00 00 00 01 00 00 00 00 00 00 14 00 00 00 00 E0 01 01 00 00 00 00 00 05 0C 00 00 00 
Security (SDS form)	D:P(A;;GA;;;SY)(A;;GXGWGR;;;BA)(A;;GXGWGR;;;WD)(A;;GXGWGR;;;RC)
Device Address	0x00000001
	
Device Configuration File	oem18.inf
DisableSetupDiChangeState	00 00 00 00 
InfPath	oem18.inf
IncludedInfs	ks.inf
	wdmaudio.inf
InfSection	IntcAzAudModel
ProviderName	Realtek Semiconductor Corp.
DriverDateData	00 00 ED 4A D5 AF C8 01 
DriverDate	5-7-2008
DriverVersion	6.0.1.5618
MatchingDeviceId	hdaudio\func_01ven_10ecdev_0889
DriverDesc	Realtek High Definition Audio
KS	1
SetupPreferredAudioDevices	01 00 00 00 
InfSectionExt	.NTAMD64
CoInstallers32	RCoInst64.dll,RtkCoInstaller
AssociatedFilters	wdmaud,swmidi,redbook
Driver	RTKVHD64.sys
	
Class	MEDIA
ClassDesc	@mmci.dll,-3000
	Sound, video and game controllers
IconPath	%systemroot%\system32\mmsys.cpl,-3004
LowerLogoVersion	5.1
Installer32	mmci.dll,MediaClassInstaller
UpperFilters	ksthunk
[/HTML]

---

### Post by Pratt on 2009-07-26
Did you get your sound working after?  I have the same laptop as you with the same sound specs. and problem, but no way of knowing how to correct the sound problem, absolutely no sound on anything!

Regards

Pratt

---

### Post by acer8930 on 2009-07-28
I've since given up, but I'll be trying again in a month when I get a hi-speed connection so it'll be easier to download packages.

I've also stopped recieving messages from linmodems so I'll need to resubscribe. 

Hopefully by then they'll have working drivers, because Linux has no appeal for me if I can't get any sound.

---

