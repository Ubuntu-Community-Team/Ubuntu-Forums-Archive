---
title: "Kubuntu: Intel HDA (ICH7) - no sound"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by santeria on 2007-04-08
i get no sound. i have alsa chosen as my audio device. i'm using kubuntu 6.10
my info:
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

i tried ALSA, but my knowledge is limited and i don't know if i tried everything.

i've only been using linux for a few months. i'd appreciate any help. thanks.

i've tried following [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and a few others, but still nothing.

---

### Post by drunkndog5 on 2007-04-09
I had a similar problem, and went through the steps on the page you linked, I found that opening alsa mixer, and turning on the sound for surround worked for me, and has been mentioned to work elsewhere.  Hope this helps

---

### Post by santeria on 2007-04-09
i get an error trying to open:
alsamixergui - alsamixer: function_snd_ctl_open failed for Default: No such device
and
aconnectgui - Error opening sequencer

i'm going to uninstall and reinstall alsa lib, oss, tools, etc.

before i do that, i saw something about adding "linux acpi=off" to the menu.list. i don't know what it does, sorry i'm new a newbie, but i'll try anything to get some sound.

any other ideas? links? guides?
i appreciate the reply/s. thanks.

---

### Post by eggdeng on 2007-04-09
[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

---

### Post by santeria on 2007-04-10
still no sound!
can't get alsa to work with a combo of models 3, 5, 6, laptop, auto, etc.
i get an error trying to open alsa mixer.

i tried connexant.com, which has linux drivers for my device...(my audio device is conexant hda - intel hda ich7). instaled that and followed the directions, no use. when it was installing it gave warning: snd_hda_intel was in use, which i think is a good sign that alsa is working? idk. i'm a newbie.
wish somebody who has experience would help me out from scratch with alsa and the kernel which i know nothing about, because i know there's people, via the forums, who have working audio with the same device.

my specs:
Toshiba Satellite P100-?
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) - in vista it's Connexant HD Audio
Dual boot, Vista & Kubuntu

btw, i'm trying to get kubuntu to be my main OS, but so far not so good.
my printer also is not supported. thanks for the help.

---

### Post by santeria on 2007-04-11
update: alsa is working fine i think....still no sound! i'm not giving up!!! it's getting better though.

my info:
```
aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
alsamixer
```
AlsaMixer v1.0.14rc2 (Press Escape to quit)
Card: HDA Intel
Chip: Conexant CX20549 (Venice)
View: [Playback] Capture  All
Item: Master

-Listed are:
Master, PCM, IEC958, Ext Mic, Int Mic
...none are muted, though IEC958 does not have a volume bar, but it is enabled in KMix

```
lspci -v
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0000000-d1ffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cff00000
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 58
        Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: 8a000000-8a0fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 50
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 50
        Memory at d2404000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d2000000-d20fffff
        Prefetchable memory behind bridge: 0000000088000000-0000000089f00000
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 233
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 18b0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: medium devsel, IRQ 11
        I/O ports at 18c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0398 (rev a1) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at 8a000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

0a:04.0 CardBus bridge: Texas Instruments Unknown device 8039
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 168, IRQ 177
        Memory at d2004000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
        Memory window 0: 88000000-89fff000 (prefetchable)
        Memory window 1: 8c000000-8dfff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

0a:04.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at d2007000 (32-bit, non-prefetchable) [size=2K]
        Memory at d2000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

0a:04.2 Mass storage controller: Texas Instruments Unknown device 803b
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at d2005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

0a:04.3 Class 0805: Texas Instruments Unknown device 803c (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at d2007800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

0a:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 66
        Memory at d2006000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 3000 [size=64]
        Capabilities: <access denied>
- i don't know if it means anything, i don't know anything, but some of them including the audio say "access denied"

i've also followed these guides as well: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel)

i don't know if it's just the options snd-hda-intel model=? code that isn't working for me or what?
i've tried laptop-eapd, 3stack, auto, ref, etc.
i'd appreciate any hep. thanks again!

---

### Post by eggdeng on 2007-04-12
You could try ```
options snd-hda-intel model=toshiba
``` Remember you will need to reboot for changes to take effect. It does sound like you are just one step away from getting this working but there are a lot of possible options. I have even seen a thread where one poster got his Toshiba working with model=fujitsu. 

Valid options should be listed in a zip file on your system which you can unzip by typing 
```
gunzip /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz.
```
Open it with ```
gedit /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt
``` and do a search for 82801G, which is how lspci identifies your chip and you might be able to narrow down the field.

Another fix I see being suggested for the Toshiba P100 series is to disable ACPI by adding ```
acpi=off
``` to /boot/grub/menu.lst & rebooting although it sounds like a desperate remedy to me. In any case, keep hacking away, you'll get there.

---

### Post by gene6482 on 2007-04-14
im having the same exact issue with my card on a toshiba laptop, so any help would definitely be appreciated

---

### Post by gene6482 on 2007-04-14
im having the same exact issue with my card on a toshiba laptop, so any help would definitely be appreciated

---

### Post by gene6482 on 2007-04-15
I finally got it working using the instructions on this page

[http://forums.gentoo.org/viewtopic-p-3774561.html#3774561](http://forums.gentoo.org/viewtopic-p-3774561.html#3774561)

---

### Post by Felipe Butcher on 2007-05-09
Hello Santeria.

I was having the same problem. 

I have a dv2000 series (dv2120la). with the same sound card.

I tried this link too: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I dont know if is the same yours but, when i was trying to make the alsa-driver, i got errors.

The link tell you to make the rc1 driver, so i try with the rc4 for driver, lib and tools, and now it works!


Thanks.

---

### Post by santeria on 2007-05-23
ALSA is installed. RC4. Mixer's volume is up. Laptop volume dial is up.
Sound test in System Settings yields no sound.
I've tried adding a few options to snd_hda_intel model=""

Should I turn acpi off. If so, how do I do it?

This problem's been bothering the **** out of me.It's so bad I've started liking Vista.

I'll post any info necessary if it'll help. Thanks.

Previous post: Kubuntu: Intel HDA (ICH7) - no sound

---

### Post by cptcrunch on 2007-05-24
this thread may be of some help also.

[http://ubuntuforums.org/showthread.php?t=349491](http://ubuntuforums.org/showthread.php?t=349491)

you can try a custom DSDT from

[http://acpi.sourceforge.net/dsdt/view.php](http://acpi.sourceforge.net/dsdt/view.php)

My model is Toshiba P100 PSPA3C-SD300E. I read that the Toshiba Satellite P100-JR100E DSDT works. I have not tried it yet because I can't afford to have any downtime right now.

I could not find a custom DSDT for your model though. Let me know if you are successful.


Update: I now have audio, with ACPI on, thanks to the BIOS update and the custom DSDT file mentioned above.

---

### Post by cptcrunch on 2007-05-24
^ bump...

---

### Post by lexarrow on 2007-05-26
maybe [this]("http://ubuntuforums.org/showthread.php?t=455147") could help

---

### Post by oldmars on 2007-05-26
**[SIZE="5"]YES, acpi=off [/SIZE]** is the solution to solve my Toshiba P105-S6014 with Intel HDA (ICH7) - no sound problem!!!

Choice your favorite text editor to modify **/boot/grub/menu.lst**

in my menu.lst : add **[SIZE="4"]acpi=off noacpi [/SIZE]**as follow:

# linux installation on /dev/sda10.
title        Kubuntu, kernel 2.6.17-10-generic (on /dev/sda10)
root        (hd0,9)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sda10 ro quiet splash **acpi=off noacpi**
initrd        /boot/initrd.img-2.6.17-10-generic

then re-boot the computer

Then I get sound work!!:D

---

### Post by cptcrunch on 2007-05-27
> **oldmars said:**
> **[SIZE="5"]YES, acpi=off [/SIZE]** is the solution to solve my Toshiba P105-S6014 with Intel HDA (ICH7) - no sound problem!!!

Choice your favorite text editor to modify **/boot/grub/menu.lst**

in my menu.lst : add **[SIZE="4"]acpi=off noacpi [/SIZE]**as follow:

# linux installation on /dev/sda10.
title        Kubuntu, kernel 2.6.17-10-generic (on /dev/sda10)
root        (hd0,9)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sda10 ro quiet splash **acpi=off noacpi**
initrd        /boot/initrd.img-2.6.17-10-generic

then re-boot the computer

Then I get sound work!!:D

Yes that's fine, but did you try a BIOS upgrade and a custom DSDT file?

Turning ACPI off is kinda hacky and I don't recommend that you do that.

---

### Post by stchman on 2007-05-31
This worked for me!!!!

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Try it.

---

