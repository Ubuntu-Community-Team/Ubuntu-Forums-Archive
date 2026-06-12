---
title: "Alsa not recognizing sound card on HP laptop!"
date: 2009-09-10
forum: Hardware
---

### Post by Tyorik on 2009-09-10
So apparently my sound card is somewhat recognized, but not. Oddly, my Alsa driver version is different than the lib, too, but may be unrelated. In anycase, I have no sound from either my headphone jack or my internal speakers. This can explain it better than I can:

!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP Pavilion dv4 Notebook PC


!!Kernel Information
!!------------------

Kernel release:    2.6.28-15-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.19
Library version:    1.0.20
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
    Subsystem: 103c:30f7


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-pcsp: index=-2
snd-hda-intel: model=laptop
snd-hda-intel: xxx...enable_msi=1....


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  1 Sep 11 09:54 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Sep 11 09:54 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:223: no soundcards found...

ARECORD

arecord: device_list:223: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_iso8859_1
nls_cp437
vfat
fat
i915
drm
binfmt_misc
ppdev
bridge
stp
bnep
input_polldev
lp
parport
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq
snd_timer
snd_seq_device
uvcvideo
compat_ioctl32
snd
psmouse
videodev
mmc_block
joydev
serio_raw
v4l1_compat
soundcore
iTCO_wdt
iTCO_vendor_support
sdhci_pci
sdhci
leds_hp_disk
led_class
snd_page_alloc
intel_agp
agpgart
lis3lv02d
video
output
usbhid
r8169
mii
fbcon
tileblit
font
bitblit
softcursor


!!ALSA/HDA dmesg
!!------------------

[   34.630023] USB Video Class driver (v0.1.0)
[   34.738977] snd_hda_intel: Unknown parameter `xxx...enable_msi'
[   34.822972] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume

---

### Post by Fafler on 2009-09-11
The snd-hda-intel module should work. Try uncommenting the options in /etc/modules and reboot

```
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-pcsp: index=-2
#snd-hda-intel: model=laptop
#snd-hda-intel: xxx...enable_msi=1....
```

---

### Post by Tyorik on 2009-09-11
Edit: Did it... Didn't work. :(

I can't figure out why this thing isn't recognizing my sound card at all. Some things recognize it, but the important ones don't.

[quote=]petsche@Optimus:~$ hwinfo --sound
28: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_8086_293e
  Unique ID: u1Nb.sgM5+Zagk53
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801I (ICH9 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293e "82801I (ICH9 Family) HD Audio Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30f7 
  Revision: 0x03
  Memory Range: 0xdc500000-0xdc503fff (rw,non-prefetchable)
  IRQ: 11 (no events)
  Module Alias: "pci:v00008086d0000293Esv0000103Csd000030F7bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is not active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown[/quote]

---

### Post by novistahere on 2009-09-11
you can try the following commond. 

gksudo gedit /etc/modprobe.d/alsa-base

add the following line to the end.

options snd-hda-intel enable_msi=1

---

### Post by tau88 on 2009-10-04
I had a similar problem when updated the kernel, had no soundcards detected

try upgrading ALSA as described here:

[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

and post your results

---

### Post by MasterOfTheHat on 2009-10-06
Well, I had the same issue: HP dv4-1435dx running Jaunty 64-bit. Upgraded to 2.6.28-15-generic on Friday and lost my sound. ALSA wasn't finding the sound card at all, ("aplay -l" said that no devices were detected). I could reboot the machine into 2.6.28-14-generic and everything was good. I had already upgraded ALSA to 1.0.21 to resolve issues I was having, (see [post here]("http://ubuntuforums.org/showpost.php?p=7940747&postcount=14")).

Just for the heck of it, I reinstalled ALSA 1.0.21, and now everything works.

[ALSA install]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/")

---

