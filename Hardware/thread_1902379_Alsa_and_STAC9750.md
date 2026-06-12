---
title: "Alsa and STAC9750"
date: 2011-12-30
forum: Hardware
---

### Post by andypag on 2011-12-30
Hello.

I&#7743; a newby. 

I have a Panasonic Toughbook CF29, and installed a few different distros to learn about linux, and get the most out of this older machine. At the moment it&#347; Xubuntu, but the problem has been the same with Puppy, Lubuntu, ...

But I cant get any sound out of it whatever distro I try. At best I get VERY quiet audio from the headphones only.

Ive read about alsamixer, and cranking the volumes up to max. Ive also read about adding a line to alsa-base.conf with model=... but I can find any reference anywhere for the chipset SigmaTel STAC9750,51 (on irq9)

The card is Intel 82801DB-ICH4.

Ive come to the conclusion that this card isnt supported by ALSA and so there is nothing I can do. 

I hope someone out there can tell me this is wrong.

Next post includes some details I hope are relevant.

Thanks for your help. 4 days working on this, I&#7743; ready to reach for the WinXP cd.

Andy

---

### Post by andypag on 2011-12-30
andypag@Toughbook:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)
02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)
02:01.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by andypag on 2011-12-30
He&#341;e&#347; the content of alsa-base.conf

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS &&  { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe  --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ;  /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

---

### Post by lidex on 2011-12-31
Sorry, I don't have the energy to sift through all the info on this ancient hardware, but have a go:
[https://www.google.com/search?q=sigmatel+stac9750&sitesearch=ubuntuforums.org](https://www.google.com/search?q=sigmatel+stac9750&sitesearch=ubuntuforums.org)

---

### Post by andypag on 2011-12-31
Thanks. I'm a newby on linux, but I had heard of this google website. 

I've spent 4 days looking for solutions online and was posting here in the hope that someone with some experience of this sound card or a better understanding of the alsa driver than me could guide me to a solution.

---

### Post by MoreOrLess on 2011-12-31
Someone claims to have solved it with a bios update: [http://ubuntuforums.org/showthread.php?t=1511765](http://ubuntuforums.org/showthread.php?t=1511765)

Apparently lidex forgot about that thread :P

---

### Post by andypag on 2011-12-31
Thanks Moreorless.

Id seen that post. Mine is a mark3, which uses a different bios update to the mk2 in that post. I already have the latest bios installed.

---

### Post by MoreOrLess on 2011-12-31
Then the the only other option is trying ac97 options/quirks in your /etc/modprobe.d/alsa-base.conf (model= is "high def" audio, which your chip is not.)
Edit your alsa-base.conf with this command:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

Below is the the documentation. I'm thinking that this is the first line you should try:
```
options snd-intel8x0 ac97_quirk=inv_eapd
```
Each time you make a change, you can test the configuration with this command:
```
sudo /sbin/alsa force-reload
```

```
Module snd-intel8x0
  -------------------

    Module for AC'97 motherboards from Intel and compatibles.
			* Intel i810/810E, i815, i820, i830, i84x, MX440
				ICH4, ICH5, ICH6, ICH7, 6300ESB, ESB2
			* SiS 7012 (SiS 735)
			* NVidia NForce, NForce2, NForce3, MCP04, CK804
				 CK8, CK8S, MCP501
			* AMD AMD768, AMD8111
			* ALi m5455

    ac97_clock	  - AC'97 codec clock base (0 = auto-detect)
    ac97_quirk    - AC'97 workaround for strange hardware
		    See "AC97 Quirk Option" section below.
    buggy_irq     - Enable workaround for buggy interrupts on some
                    motherboards (default yes on nForce chips,
		    otherwise off)
    buggy_semaphore - Enable workaround for hardwares with buggy
		    semaphores (e.g. on some ASUS laptops)
		    (default off)
    spdif_aclink  - Use S/PDIF over AC-link instead of direct connection
		    from the controller chip
		    (0 = off, 1 = on, -1 = default)

    This module supports one chip and autoprobe.

    Note: the latest driver supports auto-detection of chip clock.
    if you still encounter too fast playback, specify the clock
    explicitly via the module option "ac97_clock=41194".

    Joystick/MIDI ports are not supported by this driver.  If your
    motherboard has these devices, use the ns558 or snd-mpu401
    modules, respectively.

    The power-management is supported.

AC97 Quirk Option
=================

The ac97_quirk option is used to enable/override the workaround for
specific devices on drivers for on-board AC'97 controllers like
snd-intel8x0.  Some hardware have swapped output pins between Master
and Headphone, or Surround (thanks to confusion of AC'97
specifications from version to version :-)

The driver provides the auto-detection of known problematic devices,
but some might be unknown or wrongly detected.  In such a case, pass
the proper value with this option.

The following strings are accepted:
    - default	Don't override the default setting
    - none	Disable the quirk
    - hp_only	Bind Master and Headphone controls as a single control
    - swap_hp	Swap headphone and master controls
    - swap_surround  Swap master and surround controls
    - ad_sharing  For AD1985, turn on OMS bit and use headphone
    - alc_jack	For ALC65x, turn on the jack sense mode
    - inv_eapd	Inverted EAPD implementation
    - mute_led	Bind EAPD bit for turning on/off mute LED

For backward compatibility, the corresponding integer value -1, 0,
... are  accepted, too.

For example, if "Master" volume control has no effect on your device
but only "Headphone" does, pass ac97_quirk=hp_only module option.

```

Good luck..

---

### Post by lidex on 2011-12-31
> Below is the the documentation. I'm thinking that this is the first line you should try:

```
options snd-intel8x0 ac97_quirk=inv_eapd
```



Or this:
```
options snd-intel8x0 index=0 ac97_quirk=3 enable=1
```

---

### Post by andypag on 2011-12-31
Thanks, Working on NYE. Dedicated. Happy new year.

Will try this now.

---

### Post by andypag on 2011-12-31
Really disappointed. Tried all sorts of alternatives from those listed and nothing changes. Just really faint audio through headphones.

What&#347; EAPD out of curiousity?

I&#7743; giving up. Think this must be something physical. Might be the headphone jack wedged open and shorting? Doubt it, but tried everything else.:confused:

Thanks again for your help.

---

### Post by MoreOrLess on 2012-01-01
> What&#347; EAPD out of curiousity?
External Amp Power-Down
> Thanks again for your help.
You're welcome, although I wish we could have solved it.

Did you try the buggy_irq and/or buggy_semaphore options?

---

### Post by MoreOrLess on 2012-01-01
One other thought, perhaps disabling power management will help:
```
options snd-intel8x0 power_save=0
```

---

### Post by lidex on 2012-01-01
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by geordanbrown on 2012-02-03
Has anyone gotten the touchscreen of the CF-29 working with Ubuntu 11.10?

I cant seem to get it figured out...

Thanks,
Geordan

---

