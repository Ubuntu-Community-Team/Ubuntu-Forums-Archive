---
title: "No Nvidia Sound Card in New Cutting Edge Hp Omen X - GTX 1080m -"
date: 2018-09-16
forum: Hardware
---

### Post by markackerman8@gmail.com on 2018-09-16
(edit Nov. 11th 2018)
Any help would be greatly appreciated.

I have been helping hundreds of others in UBUNTU for 13 years happily, and below you will see many solutions for this new cutting edge FARGING Hp laptop (Hp is getting as proprietary as Windows and SONY :confused:)

... but am stuck with this one.

I Just relisted this as UNSOLVED as after an update I have a serious GLITCH ... **I almost feel it is a conspiracy!!!!!!!** :(

The last problem is simple ...
Video pass through is not working "PROPERLY or at ALL!, with the Nvidia Drivers through My HDMI and Home Theater System (it works fine with Nouveau Driver, and Windows).

I have tried:
1/  changing HDMI cables
2/ tried purging and re-installing  Nvidia for all three drivers ... 390, 396, 410
3/ re-installing Ubuntu 18.10 then 18.04 LTR

and I know it is not entirely a linux problem but a **Linux/Nvidia** problem!

Other Symptoms are Alt F2 shows screen in a** pink HAZE!!**, and using tried and true "r" with Alt F2 just makes the screen go blank! 
It also will show for a second then go black! WTF!!!!

Please Help!

p.s. Below are fixes for GTX 1080 HDMI Audio patch to get NVHDA visible and working :)
and other fixes for ACPI infuriating errors!
#######################################################################



This will be a deal breaker for my linux 13 years later - please help and Thanks in advance.

Symptoms:
No HDMI Option in Settings/Sound
HDMI acting funky, as in Direct to TV No Issues (though no Digital Sound of course)
but through my Home Theater Receiver it is in consistent and trickily glitched to get it to pass through 50% of the restarts.
$ aplay -l  ...  Shows no Nvidia or HDMI or Digital Sound card

Nvidias VGA Port? is at
pci:0   &   bus info:       pci@0000:01:00.0

So now you know there is no driver for the sound Card - so I hope it will either come soon, or can be found now!

Also I have read that some new Omen Hp have the same issue that can be solved.  Any help Please.

I will list my Sysinfo here

Ubuntu 18.04.1 LTR

Intel(R) Core(TM) i7-7820HK CPU @ 2.90GHz,  
16 GBs RAM,  
1TB NVMe,  512 gbs PCIe-Sata,  1 TB 7200 HDD
Thunderbolt USB Ports
**NVidia GTX 1080m !!!!  The problem I guess**
and oddly No Intel Graphics - Only Nvidia

Exhausted and don't want to write more, but I will work all night to get it fixed - Just give any ideas or insight.

Thanks for at least reading this far, Mark:(

---

### Post by Autodave on 2018-09-16
Did you install a driver for the Nvidia card?  Go to Settings -> Session & Startup -> Additional Drivers and chose the one that it recommends.  That should fix everything.

---

### Post by markackerman8@gmail.com on 2018-09-16
Of Course I did both the recommended 390 (no go) and even with developer options (no go) and 2 days of frustrations, ...

 and than added the ppa (sudo add-apt-repository ppa:graphics-drivers) which allowed the nvidia-396.  This is still installed 20 reboots and 2 more days and even developer options NOGO, but finally a stable system (SOOO many acpi errors - unbearable but semi fixed with grub line [GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=strict"])

But no hint of any Nvidia or HDMI or Digital Sound ... Option / Card or Device
Checked all the normal
lspci, lshw, aplay -l(L), Settings/Sound/Config PulesAudio Volume Control/Configuration

I have installed Linux and Ubuntu Variations on likely a 50-100 computers over thye past 10+ Years Help all my friends and family get Linux and off of the MS cash Cow.   But it has been over 4 years and 30 computers with no sound issues I could not remedy EASILY.  This one is beyond me.

Surely this card has been around long enough (and many people have it working so I HOPE it must an Hp oddity)

Any suggestions Surely Welcome - i don't want to go into Windows for  my home / Entertainment Machine but Digital and Surround Sound is CRUCIAL!.

Thanks at least for caring, Mark

---

### Post by markackerman8@gmail.com on 2018-09-16
I went to [HTML]https://help.ubuntu.com/community/SoundTroubleshootingProcedure[/HTML] AGAIN, and just got to the part of the last thing which suggest file a bug report and gives a script to run / copy / paste.  I will put it here but it is huge so I hope it ends up in a scrolling window 
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Sun Sep 16 13:13:04 UTC 2018


!!Linux Distribution
!!------------------

Ubuntu 18.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 18.04.1 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 18.04.1 LTS" HOME_URL="https://www.ubuntu.com/" SUPPORT_URL="https://help.ubuntu.com/" BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" UBUNTU_CODENAME=bionic


!!DMI Information
!!---------------

Manufacturer:      HP
Product Name:      OMEN X by HP Laptop 17-ap0xx
Product Version:   
Firmware Version:  F.18
Board Vendor:      HP
Board Name:        83A5


!!ACPI Device Status Information
!!---------------

/sys/bus/acpi/devices/ACPI0003:00/status 	 15
/sys/bus/acpi/devices/ACPI000C:00/status 	 15
/sys/bus/acpi/devices/HPIC0003:00/status 	 15
/sys/bus/acpi/devices/HPIC0004:00/status 	 15
/sys/bus/acpi/devices/HPQ6007:00/status 	 15
/sys/bus/acpi/devices/HPQ8001:00/status 	 15
/sys/bus/acpi/devices/INT33A1:00/status 	 15
/sys/bus/acpi/devices/INT3400:00/status 	 15
/sys/bus/acpi/devices/INT3403:00/status 	 15
/sys/bus/acpi/devices/INT3403:01/status 	 15
/sys/bus/acpi/devices/INT3403:02/status 	 15
/sys/bus/acpi/devices/INT3403:03/status 	 15
/sys/bus/acpi/devices/INT340E:00/status 	 15
/sys/bus/acpi/devices/INT345D:00/status 	 15
/sys/bus/acpi/devices/INT3F0D:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:00/status 	 1
/sys/bus/acpi/devices/PNP0103:00/status 	 15
/sys/bus/acpi/devices/PNP0C02:01/status 	 15
/sys/bus/acpi/devices/PNP0C02:03/status 	 3
/sys/bus/acpi/devices/PNP0C02:05/status 	 3
/sys/bus/acpi/devices/PNP0C04:00/status 	 31
/sys/bus/acpi/devices/PNP0C09:00/status 	 15
/sys/bus/acpi/devices/PNP0C0A:00/status 	 31
/sys/bus/acpi/devices/PNP0C0C:00/status 	 15
/sys/bus/acpi/devices/PNP0C0F:00/status 	 9
/sys/bus/acpi/devices/PNP0C0F:01/status 	 9
/sys/bus/acpi/devices/PNP0C0F:02/status 	 9
/sys/bus/acpi/devices/PNP0C0F:03/status 	 9
/sys/bus/acpi/devices/PNP0C0F:04/status 	 9
/sys/bus/acpi/devices/PNP0C0F:05/status 	 9
/sys/bus/acpi/devices/PNP0C0F:06/status 	 9
/sys/bus/acpi/devices/PNP0C0F:07/status 	 9
/sys/bus/acpi/devices/SYN3265:00/status 	 15
/sys/bus/acpi/devices/device:11/status 	 15
/sys/bus/acpi/devices/device:72/status 	 15
/sys/bus/acpi/devices/device:81/status 	 11


!!Kernel Information
!!------------------

Kernel release:    4.15.0-35-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.15.0-35-generic
Library version:    1.1.3
Utilities version:  1.1.3


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xdc628000 irq 137


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.3 Audio device: Intel Corporation CM238 HD Audio Controller (rev 31)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1f.3 0403: 8086:a171 (rev 31) (prog-if 80)
	Subsystem: 103c:83a5


!!Modprobe options (Sound related)
!!--------------------------------

snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
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

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	pm_blacklist : Y
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : N
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : -1
	snoop : -1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC295
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0295
Subsystem Id: 0x103c83a5
Revision Id: 0x100002
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 D3cold CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC295 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=1, channel=0
  PCM:
    rates [0x40]: 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x51 0x51]
  Converter: stream=1, channel=0
  PCM:
    rates [0x40]: 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x40]: 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x07 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x97 0x97]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x40]: 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC295 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x26 0x26]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x97 0x97]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0xb7a60130: [Fixed] Mic at Oth Mobile-In
    Conn = Digital, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40000000: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x02
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 2
     0x02* 0x03
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 3
     0x02 0x03* 0x06
Node 0x18 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x19 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x03a11040: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1a [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost Volume", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00013734: IN OUT EAPD Detect
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x03a19050: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=03, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 2
     0x02* 0x03
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40600001: [N/A] Modem Line at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1e [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=104
Node 0x21 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x03211020: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 2
     0x02* 0x03
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 5
     0x19 0x1a 0x1b 0x1d 0x13
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x00 0x00]
  Connection: 5
     0x19 0x1a 0x1b 0x1d 0x12
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x12* 0x13 0x18
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  2 Sep 16 06:09 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  5 Sep 16 06:09 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  4 Sep 16 06:11 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  3 Sep 16 06:11 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  1 Sep 16 06:09 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Sep 16 06:09 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Sep 16 06:09 .
drwxr-xr-x 3 root root 180 Sep 16 06:09 ..
lrwxrwxrwx 1 root root  12 Sep 16 06:09 pci-0000:00:1f.3 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC295 Analog [ALC295 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC295 Analog [ALC295 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [PCH]

Card hw:0 'PCH'/'HDA Intel PCH at 0xdc628000 irq 137'
  Mixer name	: 'Realtek ALC295'
  Components	: 'HDA:10ec0295,103c83a5,00100002'
  Controls      : 21
  Simple ctrls  : 12
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 81 [93%] [-4.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 0 [0%] [-65.25dB] [off]
  Front Right: Playback 0 [0%] [-65.25dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic 1',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Mic Boost',1
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 63
  Front Left: Capture 38 [60%] [11.25dB] [on]
  Front Right: Capture 38 [60%] [11.25dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Internal Mic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]


!!Alsactl output
!!--------------

--startcollapse--
state.PCH {
	control.1 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 -6525
			dbvalue.1 -6525
		}
	}
	control.2 {
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 87
		value.1 87
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.4 {
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.5 {
		iface MIXER
		name 'Auto-Mute Mode'
		value Enabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.6 {
		iface MIXER
		name 'Capture Source'
		value 'Internal Mic'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Mic
			item.1 'Mic 1'
			item.2 'Internal Mic'
		}
	}
	control.7 {
		iface MIXER
		name 'Capture Volume'
		value.0 38
		value.1 38
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 63'
			dbmin -1725
			dbmax 3000
			dbvalue.0 1125
			dbvalue.1 1125
		}
	}
	control.8 {
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.9 {
		iface MIXER
		name 'Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.10 {
		iface MIXER
		name 'Mic Boost Volume'
		index 1
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.11 {
		iface MIXER
		name 'Internal Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.12 {
		iface MIXER
		name 'Master Playback Volume'
		value 81
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 -450
		}
	}
	control.13 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.14 {
		iface CARD
		name 'Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.15 {
		iface CARD
		name 'Mic Jack'
		index 1
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.16 {
		iface CARD
		name 'Internal Mic Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.17 {
		iface CARD
		name 'Headphone Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.18 {
		iface CARD
		name 'Speaker Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.19 {
		iface PCM
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.20 {
		iface PCM
		name 'Capture Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.21 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
ccm
thunderbolt
btrfs
zstd_compress
xor
raid6_pq
cmac
bnep
binfmt_misc
nls_iso8859_1
btusb
btrtl
btbcm
btintel
uvcvideo
bluetooth
videobuf2_vmalloc
videobuf2_memops
videobuf2_v4l2
videobuf2_core
ecdh_generic
videodev
media
intel_rapl
x86_pkg_temp_thermal
intel_powerclamp
coretemp
kvm
irqbypass
crct10dif_pclmul
crc32_pclmul
ghash_clmulni_intel
pcbc
aesni_intel
aes_x86_64
crypto_simd
glue_helper
cryptd
snd_hda_codec_realtek
snd_hda_codec_generic
hp_wmi
intel_wmi_thunderbolt
wmi_bmof
snd_hda_intel
mxm_wmi
sparse_keymap
snd_hda_codec
snd_hda_core
snd_hwdep
arc4
snd_pcm
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
r8822be
snd_seq
mac80211
snd_seq_device
snd_timer
snd
intel_cstate
intel_rapl_perf
joydev
input_leds
mei_me
serio_raw
rtsx_pci_ms
cfg80211
memstick
soundcore
mei
intel_pch_thermal
processor_thermal_device
shpchp
intel_soc_dts_iosf
nvidia_uvm
wmi
hp_accel
lis3lv02d
input_polldev
int3400_thermal
acpi_thermal_rel
int3403_thermal
mac_hid
int340x_thermal_zone
acpi_pad
sch_fq_codel
parport_pc
ppdev
lp
parport
ip_tables
x_tables
autofs4
hid_logitech
ff_memless
hid_generic
usbhid
hid
uas
usb_storage
nvidia_drm
nvidia_modeset
nvidia
drm_kms_helper
syscopyarea
sysfillrect
sysimgblt
nvme
fb_sys_fops
rtsx_pci_sdmmc
psmouse
drm
rtsx_pci
nvme_core
r8169
ahci
ipmi_devintf
mii
libahci
ipmi_msghandler
video
pinctrl_sunrisepoint


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x12 0xb7a60130
0x13 0x40000000
0x14 0x411111f0
0x16 0x411111f0
0x17 0x90170110
0x18 0x411111f0
0x19 0x03a11040
0x1a 0x411111f0
0x1b 0x03a19050
0x1d 0x40600001
0x1e 0x411111f0
0x21 0x03211020

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:


!!ALSA/HDA dmesg
!!--------------

[    0.044894] ACPI: Added _OSI(Linux-Dell-Video)
[    0.044894] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.049471] ACPI Error: [_SB_.PCI0.RP05.PXSX] Namespace lookup failure, AE_NOT_FOUND (20170831/dswload2-191)
--
[    4.043598] r8822be: rtlwifi: wireless switch is on
[    4.237519] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    4.238813] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20170831/dsopcode-235)
--
[    4.242275] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20170831/psparse-550)
[    4.264799] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC295: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:speaker
[    4.264801] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.264802] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    4.264803] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    4.264804] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    4.264805] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x19
[    4.264806] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x1b
[    4.264807] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[    4.273616] r8822be 0000:6f:00.0 wlo1: renamed from wlan0
[    4.314535] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[    4.314575] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[    4.314613] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[    4.352733] AVX2 version of gcm_enc/dec engaged.
--
[    9.727343] thunderbolt 0000:05:00.0:   NFC Credits: 0x800000
[    9.727470] thunderbolt 0000:05:00.0:  Port 8: 8086:15d3 (Revision: 6, TB Version: 1, Type: DP/HDMI (0xe0102))
[    9.727470] thunderbolt 0000:05:00.0:   Max hop id (in/out): 9/9
--
[    9.727472] thunderbolt 0000:05:00.0:   NFC Credits: 0x800000
[    9.727597] thunderbolt 0000:05:00.0:  Port 9: 8086:15d3 (Revision: 6, TB Version: 1, Type: DP/HDMI (0xe0101))
[    9.727598] thunderbolt 0000:05:00.0:   Max hop id (in/out): 9/9
--
[    9.727599] thunderbolt 0000:05:00.0:   NFC Credits: 0x1000000
[    9.727725] thunderbolt 0000:05:00.0:  Port 10: 8086:15d3 (Revision: 6, TB Version: 1, Type: DP/HDMI (0xe0101))
[    9.727726] thunderbolt 0000:05:00.0:   Max hop id (in/out): 9/9
--
[    9.727728] thunderbolt 0000:05:00.0:   NFC Credits: 0x1000000
[    9.727836] thunderbolt 0000:05:00.0:  Port 11: 8086:15d3 (Revision: 6, TB Version: 1, Type: DP/HDMI (0xe0102))
[    9.727836] thunderbolt 0000:05:00.0:   Max hop id (in/out): 9/9
--
[  136.604777] thunderbolt 0000:05:00.0:   NFC Credits: 0x800000
[  136.604903] thunderbolt 0000:05:00.0:  Port 8: 8086:15d3 (Revision: 6, TB Version: 1, Type: DP/HDMI (0xe0102))
[  136.604904] thunderbolt 0000:05:00.0:   Max hop id (in/out): 9/9
--
[  136.604906] thunderbolt 0000:05:00.0:   NFC Credits: 0x800000
[  136.605031] thunderbolt 0000:05:00.0:  Port 9: 8086:15d3 (Revision: 6, TB Version: 1, Type: DP/HDMI (0xe0101))
[  136.605032] thunderbolt 0000:05:00.0:   Max hop id (in/out): 9/9
--
[  136.605034] thunderbolt 0000:05:00.0:   NFC Credits: 0x1000000
[  136.605179] thunderbolt 0000:05:00.0:  Port 10: 8086:15d3 (Revision: 6, TB Version: 1, Type: DP/HDMI (0xe0101))
[  136.605180] tupload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Sun Sep 16 13:13:04 UTC 2018


!!Linux Distribution
!!------------------

Ubuntu 18.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 18.04.1 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 18.04.1 LTS" HOME_URL="https://www.ubuntu.com/" SUPPORT_URL="https://help.ubuntu.com/" BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" UBUNTU_CODENAME=bionic


!!DMI Information
!!---------------

Manufacturer:      HP
Product Name:      OMEN X by HP Laptop 17-ap0xx
Product Version:   
Firmware Version:  F.18
Board Vendor:      HP
Board Name:        83A5


!!ACPI Device Status Information
!!---------------

/sys/bus/acpi/devices/ACPI0003:00/status 	 15
/sys/bus/acpi/devices/ACPI000C:00/status 	 15
/sys/bus/acpi/devices/HPIC0003:00/status 	 15
/sys/bus/acpi/devices/HPIC0004:00/status 	 15
/sys/bus/acpi/devices/HPQ6007:00/status 	 15
/sys/bus/acpi/devices/HPQ8001:00/status 	 15
/sys/bus/acpi/devices/INT33A1:00/status 	 15
/sys/bus/acpi/devices/INT3400:00/status 	 15
/sys/bus/acpi/devices/INT3403:00/status 	 15
/sys/bus/acpi/devices/INT3403:01/status 	 15
/sys/bus/acpi/devices/INT3403:02/status 	 15
/sys/bus/acpi/devices/INT3403:03/status 	 15
/sys/bus/acpi/devices/INT340E:00/status 	 15
/sys/bus/acpi/devices/INT345D:00/status 	 15
/sys/bus/acpi/devices/INT3F0D:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:00/status 	 1
/sys/bus/acpi/devices/PNP0103:00/status 	 15
/sys/bus/acpi/devices/PNP0C02:01/status 	 15
/sys/bus/acpi/devices/PNP0C02:03/status 	 3
/sys/bus/acpi/devices/PNP0C02:05/status 	 3
/sys/bus/acpi/devices/PNP0C04:00/status 	 31
/sys/bus/acpi/devices/PNP0C09:00/status 	 15
/sys/bus/acpi/devices/PNP0C0A:00/status 	 31
/sys/bus/acpi/devices/PNP0C0C:00/status 	 15
/sys/bus/acpi/devices/PNP0C0F:00/status 	 9
/sys/bus/acpi/devices/PNP0C0F:01/status 	 9
/sys/bus/acpi/devices/PNP0C0F:02/status 	 9
/sys/bus/acpi/devices/PNP0C0F:03/status 	 9
/sys/bus/acpi/devices/PNP0C0F:04/status 	 9
/sys/bus/acpi/devices/PNP0C0F:05/status 	 9
/sys/bus/acpi/devices/PNP0C0F:06/status 	 9
/sys/bus/acpi/devices/PNP0C0F:07/status 	 9
/sys/bus/acpi/devices/SYN3265:00/status 	 15
/sys/bus/acpi/devices/device:11/status 	 15
/sys/bus/acpi/devices/device:72/status 	 15
/sys/bus/acpi/devices/device:81/status 	 11


!!Kernel Information
!!------------------

Kernel release:    4.15.0-35-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.15.0-35-generic
Library version:    1.1.3
Utilities version:  1.1.3


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xdc628000 irq 137


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.3 Audio device: Intel Corporation CM238 HD Audio Controller (rev 31)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1f.3 0403: 8086:a171 (rev 31) (prog-if 80)
	Subsystem: 103c:83a5

hunderbolt 0000:05:00.0:   Max hop id (in/out): 9/9
--
[  136.605182] thunderbolt 0000:05:00.0:   NFC Credits: 0x1000000
[  136.605287] thunderbolt 0000:05:00.0:  Port 11: 8086:15d3 (Revision: 6, TB Version: 1, Type: DP/HDMI (0xe0102))
[  136.605289] thunderbolt 0000:05:00.0:   Max hop id (in/out): 9/9
```

---

### Post by markackerman8@gmail.com on 2018-09-16
and somewhere Another Hp Omen guy was asked the results from this
ack@ack-OMEN-X-by-HP-Laptop-17-ap0xx:~$ setpci -vD -s 01:00.0 0x488.l=2000000:0x2000000
0000:01:00.0 @488 ffffffff->(02000000:02000000)->ffffffff

perhaps it means something - I have NO CLUE!

They Suggested This
"Unfortunately, the kernel won't see the audio function unless you remove the graphics function first, which temporarily breaks the console. Because of that, it works best if you write a script to do it so you don't have to SSH into the system or try to type the commands into the console blind. Obviously, you have to stop the X server first so that you can unload the NVIDIA drivers.
&#8728; For example, on my system, the GPU is at 01:00.0 and its parent PCI bridge is 00:01.0. So the script I use is:
&#8227; setpci -s 01:00.0 0x488.l=0x2000000:0x2000000
&#8227; rmmod nvidia-drm nvidia-modeset nvidia
&#8227; echo 1 > /sys/bus/pci/devices/0000:01:00.0/remove
&#8227; echo 1 > /sys/bus/pci/devices/0000:00:01.0/rescan
&#8227; modprobe nvidia-drm
&#8227; xinit -- -retro
"

but mine does not have intel Graphis but intel sound so I don't know if it is a good idea (i.e. NOT Hybrid Optimus)

Any Ideas?

---

### Post by markackerman8@gmail.com on 2018-09-17
bump - no help I suppose everyone thinks I need to wait for a more current driver, but this model has been out since February at least!!!!!!

Please help ... and the HDMI when plugged into the Home Theater Receiver, throw out ACP INT3400;0-0 Unsupported Event Error sometimes hundreds of time crippling shutdown or bootup "acpi=strict" in grub helps that .

Also the optimus option to switch to Intel is NOT THERE!

Any Suggestions Please

---

### Post by markackerman8@gmail.com on 2018-09-18
Solved!!!  :o

 Why I had no help I will not understand but here is the fix for everyone

I can confirm that kernel module, posted by Maik Freudenberg 

([https://bugs.freedesktop.org/show_bug.cgi?id=75985#c27](https://bugs.freedesktop.org/show_bug.cgi?id=75985#c27)), 

is working fine on my system. 

Thank you for the fix. The HDMI audio device now works as it should.

The steps I did to enable HDMI audio device:
1. Download and extract the file nvhda.tar.xz.
2. Run these Commands in terminal, IN THE Folder Location of the Extracted FILES! :P
 ```
$ make
$ sudo make install
$ echo nvhda | sudo tee -a /etc/initramfs-tools/modules
$ echo "options nvhda load_state=1" | sudo tee /etc/modprobe.d/nvhda.conf
$ sudo update-initramfs -u
```

3. Reboot.

WooHoo Cutting Edge Laptop is working !!!:o

---

### Post by markackerman8@gmail.com on 2018-09-20
Thanks Mark Freudenberg

Thanks a Million!:D

---

### Post by markackerman8@gmail.com on 2018-09-24
Too Late not working Again / recognised

and a reinstall does NOT help.

I am sure it is likely Kernel Related

Please help, MArk

---

### Post by markackerman8@gmail.com on 2018-09-24
OK I solved it myself ... !  :)

At least for 3 reboots - SOLVED!

I thought perhaps it had something to do with a few changed I made in the BIOS, which I thought "How can it effect, Sound?"  :confused:

But reverting them back and sound magically appears. :)

So here is what I changed from memory
Secure Boot Disabled (Why I enabled it for the re-install is beyond me - Oh Ya Ubuntu now has an option for "Secure or Fast Boot in the Startup Menu"

Disabled TPM key
and Disabled something else I can't remember,

Trying a restart to see if it persists - If it does there will be no more comments here!

Yes it PERSISTS!

Always Trying to help, Mark :P

---

### Post by markackerman8@gmail.com on 2018-09-24
Yes Persists but, ...

But If someone can help with a little ISSUE, and this may help troubleshoot the root cause TOO.

After Hibernation, the card DISAPPEARS!

---

### Post by markackerman8@gmail.com on 2018-09-27
Still Working,

but I still don't know what I changed in the BIOS! to make it stop working - So I guess it is more of an HP or Windows glitch which is what I always suspected.

SO it seems to come down to secure boot or Uefi being enabled - I can't guess why either would "HIDE" the NVIDIA-0 Sound Card !!!

---

### Post by markackerman8@gmail.com on 2018-10-01
Solved a second way  - Simply get a Current Kernel as Ubuntu's Stable/ Tested Version takes up to 9-12 months to implement!

&#8227; For Others still having issues - I was SO Disappointed by Ubuntu. But here is another workaround which ABSOLVES Ubuntu IRRESPONSIBILITY ...

&#8227; Ubuntu uses a STABLE 9 month old Tried and Tested Kernel (4-15 as of this writing)..../ FROM JANUARY of this YEAR!!!!!!!! 

&#8227; So realizing this today, I installed UKUU a Kernel Manager which allows a "Bleeding Edge Kernel" and I installed their latest ... 4.18.11

&#8728; SEPTEMBER 2018 KERNEL! And to check my dismay of Ubuntu's IRRESPONSIBILITY, for this well known 10 month issue - plaguing MANY NEWER Laptops and PC's

&#8728; The HDMI Sound is NOW WORKING as it should with the newer KERNEL!:P

Just Trying to share the good news!

---

