---
title: "headphone not working"
date: 2011-05-25
forum: Hardware
---

### Post by maruf10 on 2011-05-25
hi

i am using ubuntu 10.04 . My headphone works well with windows not for ubuntu . No connection at all .
want to know the solution

thanks in advance

maruf

---

### Post by gordintoronto on 2011-05-25
Did they ever work in Ubuntu? If you click on the speaker icon, are they muted? If you select Sound Preferences, what appears under the Hardware tab? Is the volume set very low? In the Output tab, what device is chosen? Are there other devices? What "Connector" appears?

What brand and model of computer?

---

### Post by maruf10 on 2011-05-25
Q: Did they ever work in Ubuntu?
A:using ubuntu for more than 2 years ... headphone never worked

Q:If you click on the speaker icon, are they muted? 
A:my speaker mutes

Q:If you select Sound Preferences, what appears under the Hardware tab?
A: internal audio
   1 output/1 input 
   Analog stereo duplex

Q:Is the volume set very low
A:no

Q:In the Output tab, what device is chosen? 
A:internal audio analog stereo (only this option)

Q:What "Connector" appears?
A:analog headphones

---

### Post by gordintoronto on 2011-05-25
> **maruf10 said:**
> Q:If you click on the speaker icon, are they muted? 
A:my speaker mutes


I can't figure out what you mean.

You might try changing the connector to "analog output."

What brand and model of computer?

---

### Post by lidex on 2011-05-25
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications-> Accessories-> Terminal"]

---

### Post by maruf10 on 2011-05-26
@lidex :
here is the [link]("http://www.alsa-project.org/db/?f=d3e32a5bfb5901a924f059deef965fd6f6324ea2")

@gordintoronto:
actually i didn't understand the question . my headphone is not working at all . so there is no question of mute . as speaker(sound box) is working well , when i click on mute .. my speakers(sound box) mute :-)

---

### Post by gordintoronto on 2011-05-26
It would have been really useful if you had described the problem as, "my speakers work fine, but my earphones don't." Are the speakers internal or external?

What brand and model of computer?

---

### Post by lidex on 2011-05-26
What is this output please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by maruf10 on 2011-05-27
@lidex :

> 
#sudo dmidecode -t bios

# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0004, DMI type 0, 24 bytes
BIOS Information
	Vendor: Intel Corp.
	Version: NL94510J.86A.0017.2007.0828.1137
	Release Date: 08/28/2007
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 0.0
	Firmware Revision: 0.0

Handle 0x0012, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		enUS
	Currently Installed Language: enUS




*******************************************************************************


#sudo dmidecode -t baseboard

# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0006, DMI type 2, 20 bytes
Base Board Information
	Manufacturer: Intel Corporation
	Product Name: D945GCNL
	Version: AAD97184-105
	Serial Number: BTNL740009GL
	Asset Tag: Base Board Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Base Board Chassis Location
	Chassis Handle: 0x0007
	Type: Unknown
	Contained Object Handles: 0

Handle 0x000F, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description: Intel(R) Extreme Graphics 3 Controller

Handle 0x0010, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description: Realtek 811B-GR Ethernet Device

Handle 0x0011, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description: Intel(R) Azalia Audio Device





@gordintoronto:
sorry for bad title . mine is a desktop pc and external speaker

---

### Post by lidex on 2011-05-27
Try running alsamixer from the terminal:
```
alsamixer
```
You'll see an element labelled 'Front'. Scroll to it using L/R arrow keys then unmute it with the M key. Adjust the level with the Up/Dn keys. 
In concert with that try toggling the 'Connector' option in output tab of 'Sound Preferences'

---

### Post by maruf10 on 2011-05-27
this is the alsamixer screenshot ..

[link]("https://picasaweb.google.com/lh/photo/vNtc7xyacsSXGJwJ2J58MICwBPyAfkU1wt3hWNIq1W8?feat=directlink")

what do you suggest ??

---

### Post by lidex on 2011-05-27
The front level is up, so plug in the headphones and toggle the connector in output tab of sound preferences.

---

### Post by maruf10 on 2011-05-27
no result :(

---

### Post by maruf10 on 2011-06-17
please help meeeeeeeeeeeeeeeeeeeeeeeeee:confused:

---

### Post by lidex on 2011-06-18
Follow the alsa upgrade link in my sig and update your alsa install.

---

