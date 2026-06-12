---
title: "No sound from internal mic - Realtek ALC268, Toshiba A305"
date: 2012-05-19
forum: Hardware
---

### Post by dandaman96 on 2012-05-19
After two days of google searches and trying everything, I'm giving up and posting a thread.

I have a Toshiba A305 laptop.  Audio output works fine, but I cannot get the internal mic to work.  The best I can get is static.  

I've managed not to care for quite a while, but I have a daughter on the way with family that want to see her.  So I need to get Skype working ASAP.  

Some info below.  

```

$ uname -a

Linux ubutop 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686 i686 i386 GNU/Linux
```

```
$ gnome-session --version

gnome-session 3.2.1

```

```
$ cat /proc/asound/card0/codec#0 | grep Codec

Codec: Realtek ALC268
```

```
$ lsmod |grep intel

snd_hda_intel          32765  5 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd                    62064  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
```


```
$ lspci | grep Audio

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

```
$ sudo dmidecode -t bios

# dmidecode 2.11

SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: INSYDE
	Version: 1.50
	Release Date: 08/21/2008
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 kB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		8042 keyboard services are supported (int 9h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		Targeted content distribution is supported

```


```

$ sudo dmidecode -t baseboard

# dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 16 bytes
Base Board Information
	Manufacturer: Intel Corp.
	Product Name: Base Board Product Name
	Version: Base Board Version
	Serial Number: Base Board Serial Number
	Asset Tag: Base Board Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Base Board Chassis Location
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0


```


```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```
[http://www.alsa-project.org/db/?f=cad3e1230fd428a8796d268a9456ac0c400bab99](http://www.alsa-project.org/db/?f=cad3e1230fd428a8796d268a9456ac0c400bab99)



I've tried adding the line below to the config file with no luck.

```
$ sudo vim /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=toshiba
```


I've tried messing w/ pavucontrol, alsamixer, etc but with no luck.   

I'm hoping someone here can help out.  Thanks.

---

### Post by dandaman96 on 2012-05-21
Anyone??

---

### Post by dandaman96 on 2012-06-01
Still hoping someone can help me out...   :popcorn:

---

### Post by moz1 on 2012-06-01
This may be something you have passed already but I will ask anyway, have you tried downloading the audio driver from a trusted website source.

---

