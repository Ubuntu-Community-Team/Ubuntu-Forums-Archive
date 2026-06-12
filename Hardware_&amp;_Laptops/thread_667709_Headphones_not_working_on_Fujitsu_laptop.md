---
title: "Headphones not working on Fujitsu laptop"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by Aat on 2008-01-14
I can't get sound through the headphones on my Fujitsu laptop running Ubuntu 7.10.
I've tried adding "options snd-hda-intel model=fujitsu" to /etc/modprobe.d/alsa-base, but this doesn't fix the problem.
Any suggestions?

---

### Post by eggdeng on 2008-01-14
Could you post  your laptop model & the output of ```
lspci
``` ```
aplay -l
``` and cat ```
/proc/ asound/version
```

---

### Post by Aat on 2008-01-15
Thanks for replying so fast

laptop model = fujitsu Amilo Li 1705

the output:
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
05:01.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)

**** List of PLAYBACK Hardware Devices ****

card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).


Hope this helps...

---

### Post by Yellow Pasque on 2008-01-15
I think you were on the right track in the first post. I would try different values for 'model', like 'laptop', 'base', 'lenovo', etc.. I've seen people report that they got sound properly working by putting something completely unintuitive there, like the name of a different manufacturer. Good luck.

You might also try Method G (linux-backports) here:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by eggdeng on 2008-01-15
Check that your card is set as the default. Run
```
asoundconf list
```
to see what the card is called and
```
asoundconf set-default-card xyz
```
where xyz = the card identifier, to set it as default.
If you still have no sound, you will have to keep trying with the edits. You will find more alternatives at [http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")Take a look at, in particular the instructions about the /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt file. (Your card is VIA hda, not Intel but uses the Intel hda driver.) There are other threads about this card (some working, some not) which you can find by doing a search for VT1708.

---

### Post by Aat on 2008-01-15
I've tried a lot of different values for 'model' in the alsa-base file.
They don't work.
I found a post suggesting I should run alsamixergui.
When I do this I see a control for "input source", that is set at mute. Hoping this would solve the problem I tried putting the volume for "input source" up, but I can't do this.
Does this help in any way?

---

### Post by tribaal on 2008-02-14
I have almost the exact same laptop and the same problem...

Integrated speakers work just fine, but I cannot get the headphones to work in Ubuntu.

What's funny is that in Windows (the machine is my girlfriend's dual-boot), the problem is exactly the opposite: headphones work but speakers don't.

Here are "my outputs":

_lspci:_
```

00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
05:01.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)

```

_aplay -l:_
```

**** Liste des PLAYBACK périphériques ****
carte  0: VT82xx [HDA VIA VT82xx], périphérique 0 : VT1708 Analog [VT1708 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique: #0: subdevice #0

```

_cat /proc/asound/version:_
```
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).

```

Hope somebody has a solution, it's my girlfriend's only grief against a 100% Ubuntu laptop :)

Cheers

- Trib'

---

