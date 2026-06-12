---
title: "Line input being recognized as CD input"
date: 2010-08-25
forum: Hardware
---

### Post by ejbrant_ibo on 2010-08-25
I love Ubuntu and I've been trying to make it work. I've found several posts by different users who've had similar problems to mine, but I haven't found any of their solutions to be helping my problem. I've checked the ubuntu-bug audio app and the launchpad posts, but nothing seems to work. Here is as much information as I can get as to my hardware (if I'm missing something, please let me know because I'm not 100% fluent in Ubuntu innerworkings): 

uname -a
Linux CORE 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

cat /proc/asound/cards
0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe9f8000 irq 16
 1 [M2x2           ]: USB-Audio - MidiSport 2x2
                      M-Audio MidiSport 2x2 at usb-0000:00:13.1-1, full speed

aplay -l
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul  6 2010 for kernel 2.6.32-24-generic (SMP).

head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC888

Hopefully this can be resolved cause I love Ubuntu and would love to be able to work with music. Thanks for the help!

---

### Post by lidex on 2010-08-26
Where is the bug report location?

---

### Post by ejbrant_ibo on 2010-08-26
Do you mean the url for the launchpad bug report or some sort of bug report from Ubuntu? I've never gotten error messages on my screen, but when I went through the diagnostic tool it sent something to launchpad.

---

### Post by lidex on 2010-08-27
> **ejbrant_ibo said:**
> Do you mean the url for the launchpad bug report 

Yes.

---

### Post by ejbrant_ibo on 2010-08-27
Here's the url:

[https://bugs.launchpad.net/ubuntu/+bug/625580](https://bugs.launchpad.net/ubuntu/+bug/625580)

Hopefully that helps.

---

### Post by lidex on 2010-08-27
I don't understand. The info you posted originally does not match up with the bug report data.

---

### Post by ejbrant_ibo on 2010-08-29
I think one of the changes I had made in the past few days of troubleshooting was I booted with the real-time kernel because I had read that it's better for audio work. I found that I have the same problem either way.

---

### Post by ejbrant_ibo on 2010-09-02
Is there more information you need? Please let me know what the next step is. It's getting real frustrating not being able to record audio.

---

### Post by lidex on 2010-09-02
To troubleshoot your problem effectively it's best for you to return your system to defaults and post alsa-info.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by ejbrant_ibo on 2010-09-04
Here's the link: [http://www.alsa-project.org/db/?f=e9ceeb7c2a9841c1697a1574d37df4f7bd80d33f](http://www.alsa-project.org/db/?f=e9ceeb7c2a9841c1697a1574d37df4f7bd80d33f)

---

### Post by lidex on 2010-09-04
If you cannot get a later version of the realtime kernel, I suggest upgrading alsa. You can do that using the link in my sig.
Also, what do you get for these terminal outputs:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by ejbrant_ibo on 2010-09-05
sudo dmidecode -t bios

# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 3.23
	Release Date: 11/30/2006
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 3.23

Handle 0x0026, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

sudo dmidecode -t baseboard

# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ECS                                                             
	Product Name: Asterope3
	Version: 1.1                                                            
	Serial Number:                                                                 
	Asset Tag:                                                                 
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis:                                                                 
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0024, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description:

---

### Post by lidex on 2010-09-06
I would start with a bios update.

---

### Post by ejbrant_ibo on 2010-09-13
Sorry it took me a while to respond. I had to find the MB info and that was an involved process. After my searches I found that I have the most up-to-date BIOS available from the manufacturer. Also from my searches, I have the latest ALSA and kernel (as far as I know.) What next?

---

### Post by lidex on 2010-09-14
Wow. 2006 was the most recent bios update? Where are you looking?

---

### Post by ejbrant_ibo on 2010-09-14
[http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=601&CategoryID=1&MenuID=16&LanID=0](http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=601&CategoryID=1&MenuID=16&LanID=0)

It's the motherboard manufacturer's website. I have a made to order computer with cheaper parts. In the information I found it said that ECS makes this motherboard for HP computers (even though my computer's not really an HP)

---

### Post by ejbrant_ibo on 2010-09-17
Thank you, lidex for all of your help. I decided to just get a sound card that is Linux compatible, so hopefully I can get back to recording. Again, I really appreciate your time and help with this matter, and I will let you know how the sound card works out.

---

