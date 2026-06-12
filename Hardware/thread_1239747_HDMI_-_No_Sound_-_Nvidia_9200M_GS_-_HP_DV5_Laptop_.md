---
title: "HDMI - No Sound - Nvidia 9200M GS - HP DV5 Laptop - Jaunty 64bit"
date: 2009-08-13
forum: Hardware
---

### Post by chargrims on 2009-08-13
Hi there,

I've been googling this for days so far and haven't managed to even get my HDMI sound output recognised! I can get video output fine, but no sound through the TV.

So far the most substantial changes I've made have been by following the instructions here: [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") under the section 'Having sound issues with HP dvx laptop'.

When compiling the snapshot of ALSA I also added the allcards options which I've seen suggested in other threads. I've also checked the IEC958 options are not muted.

My aplay -l output is:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm not sure with this graphics card whether I am meant to be seeing a HDMI option, or whether I should be somehow routing the SP/DIF output to the HDMI port as I've seen suggested in other threads also.

I've not yet seen a thread for this particular setup, and many threads are too old for me to know whether the fixes will work, so I hope we can solve this and provide a solution for people using this setup.

Here are my laptop's details:
Hewlett Packard DV51015EA
Nvidia 9200M GS 512mb
Nvidia Driver Version 180.44

---

### Post by snmk on 2009-12-01
[COLOR=black][FONT=Arial]Hi [/FONT][/COLOR]
[COLOR=black][FONT=Arial]I have a HP DV5 1011ea and recently upgraded to Windows 64.  In the course of the upgrade, the NVIDIA graphics drivers were updated to the latest stable release (186).  After this I lost the sound via HDMI to my TV, causing great annoyance when trying to watch Blu-Ray.  In short, for whatever reason, the HDMI sound output does not seem to work properly on this NVIDIA release, even though the volume/signal bars on the Sound control panel indicate that sound should be outputted to the TV.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]I uninstalled the driver and rolled back to a previous driver release and the sound came back.  BUT, this was at the expense of DirectX which was downgraded at the same time from 11 to 10.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]After much cursing I decided to install the latest Beta release of the NVIDIA drivers (195)[/FONT][/COLOR]
[COLOR=black][FONT=Arial]- search the download section nvidia.co.uk for Beta and Archived drivers[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Much to my delight the sound came back and DirectX stays at 11, which is good.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Just a couple of issues worth highlighting:[/FONT][/COLOR]
[COLOR=black][FONT=Arial]1. The driver is not completely compatible with the IDT control / windows sound in general - if you click on the Sound control panel you are warned that the NVIDIA HDMI driver has incompatibility issues & are questioned whether it should be disabled.  I left this alone as frankly I can live with this if sound is played when watching Blu-Ray.  I suspect that if the NVIDIA HDMI sound is disabled that no sound would come through the TV when watching BR and that the original problem would re-occur.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]2. When the HDMI lead is unplugged from laptop, the screen on the laptop remains blank rather than "recovering".  This means that the laptop needs to be put into sleep mode or shut down whilst watching the TV and then restarted when the HDMI lead is unplugged.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]I suspect that both of the above are likely to be ironed out in the next stable release, but who knows when that might be.  In the meantime, the Beta release seems a good option to me – I suggest that you try it & see what you think.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]If you are not happy, then roll back the NVIDIA driver to that featured on HP website (release dated 11 2008, 60.1 MB, “[/FONT][/COLOR][FONT=Arial][_[COLOR=#003366]7.15.11.7904 D Current[/COLOR]_]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-67044-1&lc=en&dlc=en&cc=uk&os=4063&product=3758223&lang=en")”)[/FONT][COLOR=black][FONT=Arial][/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by kronictokr on 2010-02-14
try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

---

### Post by mk13139 on 2010-05-24
I have also a HP dv5 with a 9200M GS with Ubuntu 10.04 (32-bit). I can´t get sound over HDMI working either. I also tried this

> **kronictokr said:**
> try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

but it doesn´t help.
I can select 'Digital sound (HDMI) output' in the standard soundmixer, but I get no sound. Also in the ALSA mixer I can check the IEC958 boxes, but it doesn´t help.

B.t.w. I have not as good sound quality in Ubuntu as I get in Windows. I think it´s because Ubuntu uses a Pulse audio driver (which is a universal driver?) instead my soundcard driver, IDT HDA.

Exept for this, everything works out of the box, including muting when headphones are attached!

---

### Post by farbird on 2010-05-24
try the nvidia 185 drivers....

---

### Post by dino99 on 2010-05-24
[http://forum.xbmc.org/showthread.php?t=59877](http://forum.xbmc.org/showthread.php?t=59877)

add this ppa to your synaptic repo:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by mk13139 on 2010-05-24
Thank you for your quick replies!

Reading the article above me, this might solve my problem!
I will test it as soon as I have time.

Regards

---

### Post by mschering on 2011-01-27
Did anyone ever got this fixed in Maverick? I still didn't manage to fix this. It worked in lucid.

---

### Post by mschering on 2011-01-27
I finally found the solution. Go to System -> Restricted drivers and select the older Nvidia 173 drivers. Then audio is working fine!

---

