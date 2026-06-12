---
title: "no sound devices found"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by naga123 on 2006-11-25
Hi,

  I installed xubuntu recently. My sound card is not detected by default.
So I recompiled my kernel and installed alsa. Still it says no sound devices are found
I cannot find /dev/dsp and /etc/alsa in my pc

**lscpi** gave the folowing output
[B]00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)
[/B]

when I used
**sudo modprobe snd_via82xx**
[B]FATAL: Error inserting snd_via82xx (/lib/modules/2.6.18.1-custom/kernel/sound/pci/snd-via82xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_via82xx[/B]

So I recompiled alsa and installed it.
when I used **locate snd_via82xx**
**/etc/modprobe.d/snd_via82xx** is the output

when I run **alsaconf** I got the following output:

[B]Running update-modules...
Loading driver...
/usr/sbin/alsaconf: line 915: /etc/init.d/alsa: No such file or directory
Setting default volumes...
amixer: Mixer attach default error: No such device
Saving the mixer setup used for this in /etc/asound.state.
/usr/sbin/alsactl: save_state:1254: No soundcards found...
[/B]

when I run **alsamixer**
[B]alsamixer: function snd_ctl_open failed for default: No such device
[/B]


Plz help me......plzzzzzz. I am vexed trying to solve this problem.

---

### Post by xyz on 2006-11-25
Strange...
How about this for, among other things, an overall check:
[Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")
Good luck.

---

