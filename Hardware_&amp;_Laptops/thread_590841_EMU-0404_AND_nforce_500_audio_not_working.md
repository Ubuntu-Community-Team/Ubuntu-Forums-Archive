---
title: "EMU-0404 AND nforce 500 audio not working"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by Jsewill on 2007-10-25
The issue is with sound.  I have an EMU-0404 PCI and the onboard sound chipset, but neither of them work.

I am currently running Ubuntu 7.10 Gutsy Gibbon.  I have an nForce 500 chipset.  On a fresh install with only a few updates, no other changes, this is what dmesg gives me:

[   37.889962] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   37.889973] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   37.892187] Audigy2 value: Special config.
[   38.232951] usbcore: registered new interface driver snd-usb-audio
[   38.905036] AC'97 0 does not respond - RESET
[   38.905043] AC'97 0 access is not valid [0x0], removing mixer.
[   38.905828] ACPI: PCI interrupt for device 0000:01:06.0 disabled
[   38.905839] EMU10K1_Audigy: probe of 0000:01:06.0 failed with error -5

alsamixer give me this when invoked:  "alsamixer: function snd_ctl_open failed for default: No such device".  Now the gnome volume control applet gives me sliders and some oddly named and catagorized channels/inputs/outputs/options for my onboard audio controller, but it thinks it is a "pnp audio device", which I guess is true, but not what I was looking for.  Still no sound.

Prior to this fresh install I had installed 7.10 fresh, then installed alsa 1.0.15 from source, then I tried moving some modules around, then I tried alsaconf which called my card an "Audigy SB0400", I also tried manually loading modules through modprobe, then I tried installing esound, and several other things which I don't remember.  My onboard audio controller is enabled in BIOS, as well as the plug and play OS option.

Also, both audio devices work in windows xp home, which I have installed on another partition and am very eager to get rid of.  How do I go about fixing both sound devices?

---

### Post by fidoboy on 2007-10-31
I've also an Emu 0404 PCI, i've installed alsa 1.0.15 but it doesn't work... can anybody help??

thanks,

---

### Post by DJArty on 2008-01-04
OK I've also an Emu 0404 PCI :)   on VIA KT400 Ubuntu 7.10   ( 8.04Alfa2 also dont working from LiveCD and alsa 0.15 in it), compilled  alsa 0.15   - not working
EMU10K1_Audigy: probe of 0000:01:06.0 failed with error -5
alsamixer: function snd_ctl_open failed for default: No such device
Hellp me please too  :)

---

### Post by kurjake on 2008-01-09
I also have an EMU 0404 PCI.

The same errors are present.

I have upgraded to Hardy Heron Alpha 2, without improvement.

I also saw that installing the card in a windows system would upgrade the firmware & this would help. I tried it, again without success.

I've installed:
Alsa 1.0.15 Driver, Utils, Firmware.

The one thing I have not done is patch the alsa-source as suggested in this post:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3496]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3496")

---

