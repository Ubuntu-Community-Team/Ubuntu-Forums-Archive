---
title: "ASUS P5N7A-M Motherboard"
date: 2008-11-02
forum: Hardware
---

### Post by kotter71 on 2008-11-02
It's time once again to upgrade my HTPC.  I am really digging these new boards featuring the NVIDIA GeForce 9300/9400 integrated graphics processor.  See here:

[http://www.anandtech.com/mb/showdoc.aspx?i=3432](http://www.anandtech.com/mb/showdoc.aspx?i=3432)

One of the first boards on the market is the ASUS P5N7A-VM.  See here:

[http://www.asus.com/products.aspx?modelmenu=1&model=2579&l1=3&l2=11&l3=812&l4=0](http://www.asus.com/products.aspx?modelmenu=1&model=2579&l1=3&l2=11&l3=812&l4=0)

I was surprised to see that the downloads section includes a bundled set of Linux drivers (Audio, VGA, but nothing about LAN or RAID).  Does anyone here have any experience with this board and 8.10?

---

### Post by Alajjana on 2008-12-02
*bump*

---

### Post by scottac on 2009-01-18
I ordered one last week for a frontend. I will let you know how it goes...

---

### Post by stdPikachu on 2009-01-19
Just bought one for an HTPC myself... but not managed to get the video working in 8.04 yet...! IIRC it requires the 177 or 180 version of the nVidia driver, which aren't yet supported in Hardy.

---

### Post by king minger on 2009-01-20
I'm trying to get this board running myself. have an issue with the SATA controller:
[http://ubuntuforums.org/showthread.php?t=1044804](http://ubuntuforums.org/showthread.php?t=1044804)
talking to people on XBMC forums, this seems like a unique problem to me

---

### Post by stdPikachu on 2009-01-20
As per [this thread]("http://ubuntuforums.org/showthread.php?t=1044723") I've successfully got this board working with an existing install of 8.04, and performance is pretty damned spiffy, enough to run milkdrop at 1360x768 which was my gripe with my preceding nV 6150.

Not really any gotchas to report, although I've not tried installing onto this thing fresh (reinstalling onto new hardware is for lesser OS's with crappy hardware detection ;)), even suspend works well, at least so far. SpeedStep was turned off by default in the 0404 BIOS but seemed to be enabled in 0407 and happily clocks my E7300 down to 1.6GHz. AHCI works without issue, at least on the nV SATA controller.

The onboard sound is problematic however - the ALC1200 is detected by ALSA as an ALC888, and is crackly at times. Didn't matter to me as I use an Audigy and it's probably fixed in 8.10 (it's a known issue on the forums IIRC). lm_sensors works fine with the coretemp and w83627ehf modules.

Bit concerned about the temperature of the chipset heatsink, as it's stupidly hot to touch and it's in a [case with only the PSU fan to cool it](http://www.silverstonetek.com/products/p_spec.php?pno=sg02-f&area=usa), but the magic smoke hasn't got out yet and sensor temps are in the 30C's.

Only using DVI, not tried audio over HDMI/DisplayPort.

Next stop... an SSD!

Anyone know if it's worth activating the ACPI 2.0 in the BIOS?

---

### Post by Quantumstate on 2009-01-25
stdPikachu be advised that that chipset will burn out soon if you don't do something about it.  I replaced the stock heatsink with a Thermalright HR05-IFX heatsink & Arctic Cooling PWM 40mm fan.

Also that temp you're reading is mobo, not chipset.  Try installing the nVidia driver and run nvidia-settings and you'll be shocked by the temp.

Myself, I can't get xorg.conf right.  It will not set my projector to 1280x720, even with all overrides.

Also can't use VGA and HDMI at the same time, because VGA takes precedence if plugged.

But VDPAU in Intrepid rules!  I wish I knew though, if VDPAU works in Hardy.

---

