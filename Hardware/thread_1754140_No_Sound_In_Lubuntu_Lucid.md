---
title: "No Sound In Lubuntu Lucid"
date: 2011-05-09
forum: Hardware
---

### Post by Virgo53 on 2011-05-09
Hello All,
  I just installed Lubuntu Lucid on my old Compaq Presario 5150-
(AMD K6 3D-Now 350 MHz processor with 256 Mb RAM). I know everyone
must think I'm a glutton for punishment, right? Anyway, This was more-or-less just to see if it would work or not. Although not likely to set any speed records, it works pretty fair. I'm posting this thread using it, btw.
Previously was running Vector 6.0 Light, and had the soundcard configured using alsa.conf. (Compaq states the audio as being: Aureal A3D Interactive 360 Degrees Positional Sound.) I had it working by choosing the ESS AudioDrive ES1869 card/chip, but sure could use and will appreciate some help getting the sound working in Lubuntu. Here's the output from the alsa-info-script:

[http://www.alsa-project.org/db/?f=af6013c43b4875bf86176e5b255b0af5b6a9578b]("http://www.alsa-project.org/db/?f=af6013c43b4875bf86176e5b255b0af5b6a9578b")

Also, here's the output of lspci -v:

> 00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)
	Flags: bus master, medium devsel, latency 16
	Memory at 44000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [a0] AGP version 1.0
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 40000000-410fffff
	Prefetchable memory behind bridge: 10000000-100fffff
	Kernel modules: shpchp

00:04.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Subsystem: RaLink Device 2561
	Flags: bus master, slow devsel, latency 66, IRQ 11
	Memory at 41100000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: rt61pci
	Kernel modules: rt61pci

00:05.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)
	Subsystem: Compaq Computer Corporation Device b0bb
	Flags: bus master, medium devsel, latency 66, IRQ 10
	I/O ports at 2000 [size=128]
	Memory at 41200000 (32-bit, non-prefetchable) [size=1K]
	[virtual] Expansion ROM at 10100000 [disabled] [size=256K]
	Capabilities: [dc] Power Management version 1
	Kernel driver in use: tulip
	Kernel modules: tulip

00:14.0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] (rev 45)
	Flags: bus master, stepping, medium devsel, latency 0

00:14.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Flags: bus master, medium devsel, latency 66
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at 20a0 [size=16]
	Kernel driver in use: pata_via
	Kernel modules: pata_via

00:14.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
	Subsystem: First International Computer, Inc. Device 1234
	Flags: bus master, medium devsel, latency 66, IRQ 10
	I/O ports at 2080 [size=32]
	Kernel driver in use: uhci_hcd

00:14.3 Bridge: VIA Technologies, Inc. VT82C586B ACPI (rev 10)
	Flags: medium devsel
	Kernel driver in use: vt586b_smbus
	Kernel modules: i2c-via

01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
	Subsystem: Compaq Computer Corporation Device b0e7
	Flags: bus master, stepping, medium devsel, latency 66, IRQ 11
	Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
	I/O ports at 1000 [size=256]
	Memory at 41000000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 10000000 [disabled] [size=128K]
	Capabilities: [50] AGP version 1.0
	Capabilities: [5c] Power Management version 1
	Kernel modules: atyfb

richard@richard-desktop:~$ 


---

### Post by cavalier911 on 2011-05-09
```
sudo modprobe snd-es18xx
```
```
alsamixer
```
```
sudo echo snd-es18xx >> /etc/modules
```

---

### Post by Virgo53 on 2011-05-10
> **cavalier911 said:**
> ```
sudo modprobe snd-es18xx
```
```
alsamixer
```
```
sudo echo snd-es18xx >> /etc/modules
```

cavalier911, Here are the results of your suggested code(s):

```
bash: /etc/profile.d/*.sh: No such file or directory
richard@richard-desktop:~$ sudo modprobe snd-es18xx
[sudo] password for richard: 
WARNING: All config files need .conf: /etc/modprobe.d/soundcard, it will be ignored in a future release.
richard@richard-desktop:~$ alsamixer
cannot open mixer: No such file or directory
richard@richard-desktop:~$ sudo echo snd-es18xx >> /etc/modules
bash: /etc/modules: Permission denied
richard@richard-desktop:~$ 
```

---

### Post by lidex on 2011-05-10
Post this output please:
```
sudo lshw -C multimedia
```

---

### Post by Virgo53 on 2011-05-10
> **lidex said:**
> Post this output please:
```
sudo lshw -C multimedia
```

I tried the sudo lshw -C multimedia command and it briefly
displayed DMI and disappeared being replaced by PCI (sysfs),
(again briefly) which also disappeared being replaced by SCSI
(once again briefly), then displayed the regular command line
prompt with no output being left displayed from entering the command.  :confused:

---

### Post by cavalier911 on 2011-05-11
There are no tools for detecting ISA devices in the buntu's.
Give this a try.
Open terminal.
```
sudo -s
```
```
echo snd-es18xx >> /etc/modules
```
```
leafpad /etc/modprobe.d/alsa-base.conf
```
Add this:
[SIZE="1"][COLOR="Red"][SIZE="1"]alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x38 fm_port=0x330 irq=5 dma1=1 dma2=0[/SIZE][/COLOR][/SIZE]
Save/Quit leafpad
Reboot
See if alsamixer will open.
If it does unmute/turn up Master,PCM

---

### Post by Virgo53 on 2011-05-12
cavalier911,
 I followed your suggestions, and sound was now ready! But encountered problems- tried playing an audio cd using alsaplayer, but starting it caused the system to crash. Went into Synaptic and re-installed alsaplayer-alsa, alsaplayer-common, alsaplayer-daemon, and alsaplayer-gtk.
Tried opening alsaplayer again, which resulted in another crash.
Back into Synaptic, this time completely removed alsaplayer-alsa,
alsaplayer-common, alsaplayer-daemon, and alsaplayer-gtk. Opened
Aqualung to try the audio cd again, and it worked fine until into the second cd track- another system crash after working for 3:53.
Is there a particular keystroke combination to safely shutdown or reboot after a crash in 'buntu? Tried the holding down the right Alt key and SysRq key while individually pressing REISUB keys, but nothing happened, and I hate having to do a hard shutdown. Thank you
cavalier for your assistance!

---

### Post by cavalier911 on 2011-05-13
Your hardware is locking up because it is too slow to decode the audio cd stream with a software plugin while running lubuntu. Connect the analog out on the back of the cdrom drive to the cd analog audio in of your sound card with a cd audio patch cable. 
Tiny CD player will control the drive:
```
sudo apt-get install tcd
```
Type **tcd** in terminal to start it.

_Enable ctrl+alt+bksp Xserver Kill/Respawn_
```
sudo leafpad /etc/X11/xorg.conf
```
Add,Save then Quit:
[COLOR="Red"]Section "InputClass"
    Identifier      "Keyboard Defaults"
    MatchIsKeyboard "yes"
    Option          "XkbOptions" "terminate:ctrl_alt_bksp"
EndSection[/COLOR]

---

### Post by Virgo53 on 2011-05-13
Thanks cavalier911,
  I will try what you recommended when I get a chance- just for the record, I opened GNOME MPlayer and played an internet radio mp3 stream in stereo (bitrate was 96 kb/s and the sample rate was 44 kb/s). My wireless network connection was showing about 82%, so between that and this "prehistoric" hardware, it would choke and stumble once in a while, but did not ever lock up. I closed it after about 19 minutes of it playing.
Can you or anyone recommend a safe shutdown method in case of any more system freeze-ups?

---

