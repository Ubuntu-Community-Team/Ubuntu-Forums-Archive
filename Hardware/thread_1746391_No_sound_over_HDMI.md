---
title: "No sound over HDMI"
date: 2011-05-01
forum: Hardware
---

### Post by Rivendor on 2011-05-01
I just built a HTPC and purchased a Gigabyte GA-880-D2H motherboard. I installed 10.10 and upgraded to 11.4. I have gotten integrated audio working but I cannot get audio over HDMI to my TV to work.
I have also booted up to the kernel matching the alsa-drivers, since thats what my alsa-drivers are.

I found this thread, and still cannot get any audio.
[http://ubuntuforums.org/showthread.php?t=1677587]("http://ubuntuforums.org/showthread.php?t=1677587")

Ive checked in alsamixer and set HDA ATI HDMI soundcard S/PDIF to 00 instead of being MM.

Under sound preferences the output is set to :
RS880 Audio Device [Radeon HD 4200] Digital Stereo (HDMI)

To test this i'll set the HDMI audio to the default out, and try running a song from the web, or through banshee, ive also tried this command
```
aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav
```
but there's never any audio.

Here is some of my system information

**uname -r**
```
2.6.35-28-generic
```

**dmidecode -t bios**
```
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Award Software International, Inc.
	Version: F6
	Release Date: 08/31/2010
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
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
		AGP is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported

Handle 0x0020, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		n|US|iso8859-1
		n|US|iso8859-1
		r|CA|iso8859-1
	Currently Installed Language: n|US|iso8859-1
```

**dmidecode -t baseboard**
```
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: GA-880GM-D2H
	Version: x.x
	Serial Number:  
```

**aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

**dpkg --get-selections | grep alsa**
```
linux-alsa-driver-modules-2.6.35-28-generic	install
linux-headers-alsa-driver-2.6.35-28-generic	install
```

**alsa info**
[http://www.alsa-project.org/db/?f=13e7951341c23f9c63ab12e5137a5fb5b56fe93b](http://www.alsa-project.org/db/?f=13e7951341c23f9c63ab12e5137a5fb5b56fe93b)



I've searched over the internet and tried many suggestions, but to no avail. So I figured i'd ask if anyone out there has any idea what's going on.

---

### Post by Rivendor on 2011-05-02
Anybody? 

Should I just get an Nvidia graphics card to use instead?

---

### Post by Rivendor on 2011-05-02
Well I now have sound over HDMI. It worked out of the box with fedora 14.

---

### Post by Swifty31703 on 2011-05-03
Here is a manual work around to get it working. It is a bit of a pain to have to set it everytime but it does work.

Sound Preferences>Hardware(Tab)>Settings for selected device(drop down menu)>Digital Stereo (HDMI) Output

Just remember to set it back to Analog Stereo Duplex if you want your computer speakers to play sound again.

Hope this helps.

---

### Post by Rivendor on 2011-05-03
> **Swifty31703 said:**
> 
Sound Preferences>Hardware(Tab)>Settings for selected device(drop down menu)>Digital Stereo (HDMI) Output

Thanks for the reply! 
Unfortunately I've tried that and there was still no sound.


I'm thinking it could be a bug in the ATI Catalyst drivers, since in fedora I'm using the stock system drivers not the ATI drivers from the fusion repo.

Also I upgraded from 10.10 to 11.4 though the Ubuntu GUI, and not with a fresh install from a liveCD. I haven't done that since Drapper and it didn't work well then.

Everything might work perfectly fine if I do a fresh reinstall with 11.4. Also disabling the Catalyst drivers might work too. 
But right now my HTPC is working so i'm happy.

---

