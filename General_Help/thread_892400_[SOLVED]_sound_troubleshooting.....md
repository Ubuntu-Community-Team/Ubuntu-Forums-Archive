---
title: "[SOLVED] sound troubleshooting...."
date: 2008-08-17
forum: General Help
---

### Post by roshanjose on 2008-08-17
i have been trying 4 long since i installed hardy to get my sound working..

i typed alsamixer...nd i made master, pcm, front to 100....

i tried to ubuntu's sound troubleshooting [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)             i'll paste some of the results

root@roshan-desktop:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


root@roshan-desktop:~# lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: Intel Corporation Unknown device 4c43
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation Unknown device 4c43
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 50100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 20e0 [size=8]
	Memory at 40000000 (32-bit, prefetchable) [size=256M]
	Memory at 50180000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Intel Corporation Unknown device 0204
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 501c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gammagraphx, Inc. Unknown device 0000
	Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gammagraphx, Inc. Unknown device 0000
	Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gammagraphx, Inc. Unknown device 0000
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 4c43
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 2080 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 4c43
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 2060 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 4c43
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 2040 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 4c43
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 2020 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Unknown device 4c43
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 501c4000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 50000000-500fffff
	Capabilities: [50] Subsystem: Intel Corporation Unknown device 4c43

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: Intel Corporation Unknown device 4c43
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Unknown device 4c43
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 20b0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Intel Corporation Unknown device 4c43
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 20c8 [size=8]
	I/O ports at 20ec [size=4]
	I/O ports at 20c0 [size=8]
	I/O ports at 20e8 [size=4]
	I/O ports at 20a0 [size=16]
	Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Intel Corporation Unknown device 4c43
	Flags: medium devsel, IRQ 11
	I/O ports at 2000 [size=32]

04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
	Subsystem: Intel Corporation Unknown device 0001
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at 50000000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1000 [size=64]
	Capabilities: [dc] Power Management version 2


the next step listed is that i have 2 search 4 the driver nd download it...i presumed my driver 2 be snd-hda-intel...

i dont know how 2 proceed from sudo modprobe snd-[NAME OF YOUR SOUNDCARD'S DRIVER]

i tried typing my driver name within the brackets...but i couldnt get any help....plzz help me

---

### Post by drboontu on 2008-08-17
Hi,

Sound info

post back what is returned when you type these in a terminal:

$ lspci | grep -i audio

$ cat /proc/asound/modules

$ cat /proc/asound/devices

$ lsmod | grep snd

Also take a look at dmesg, this will tell you a great deal about your system

$ dmesg

Cheers!

---

### Post by roshanjose on 2008-08-17
root@roshan-desktop:~# dmesg
[ 1751.298063] sr 0:0:1:0: [sr0] Add. Sense: Unrecovered read error
[ 1751.298070] end_request: I/O error, dev sr0, sector 6715464
[ 1751.991032] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1751.991042] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
[ 1751.991049] Info fld=0x199e13
[ 1751.991051] sr 0:0:1:0: [sr0] Add. Sense: Unrecovered read error
[ 1751.991057] end_request: I/O error, dev sr0, sector 6715468
[ 1752.726971] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1752.726983] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
[ 1752.726990] Info fld=0x199e14
[ 1752.726992] sr 0:0:1:0: [sr0] Add. Sense: Unrecovered read error
[ 1752.726998] end_request: I/O error, dev sr0, sector 6715472
[ 1752.727002] printk: 5 messages suppressed.
[ 1752.727006] Buffer I/O error on device sr0, logical block 1678868
[ 1753.461407] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1753.461419] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
[ 1753.461429] Info fld=0x199e15
[ 1753.461431] sr 0:0:1:0: [sr0] Add. Sense: Unrecovered read error
[ 1753.461439] end_request: I/O error, dev sr0, sector 6715476
[ 1754.196872] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1754.196884] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
[ 1754.196895] Info fld=0x199e16
[ 1754.196897] sr 0:0:1:0: [sr0] Add. Sense: Unrecovered read error
[ 1754.196904] end_request: I/O error, dev sr0, sector 6715480
[ 1754.889619] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1754.889628] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
[ 1754.889635] Info fld=0x199e17
[ 1754.889637] sr 0:0:1:0: [sr0] Add. Sense: Unrecovered read error
[ 1754.889643] end_request: I/O error, dev sr0, sector 6715484
[ 1755.614806] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1755.614816] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
[ 1755.614823] Info fld=0x199e0c
[ 1755.614825] sr 0:0:1:0: [sr0] Add. Sense: Unrecovered read error
[ 1755.614831] end_request: I/O error, dev sr0, sector 6715440

root@roshan-desktop:~# lsmod | grep snd
snd_hda_intel         495844  5 
snd_hwdep              13064  1 snd_hda_intel
snd_seq_dummy           6020  0 
snd_seq_oss            39424  0 
snd_pcm_oss            55840  0 
snd_mixer_oss          20864  1 snd_pcm_oss
snd_seq_midi           10944  0 
snd_pcm               100232  3 snd_hda_intel,snd_pcm_oss
snd_rawmidi            30112  1 snd_seq_midi
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
snd_seq                67456  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29448  2 snd_pcm,snd_seq
snd_seq_device         10900  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78824  21 snd_hda_intel,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         13968  2 snd_hda_intel,snd_pcm
soundcore              10400  1 snd

root@roshan-desktop:~# lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

root@roshan-desktop:~# cat /proc/asound/modules
 0 snd_hda_intel

root@roshan-desktop:~# cat /proc/asound/devices
  0: [ 0]   : control
  1:        : sequencer
  6: [ 0- 2]: hardware dependent
 16: [ 0- 0]: digital audio playback
 24: [ 0- 0]: digital audio capture
 33:        : timer

---

### Post by roshanjose on 2008-08-17
root@roshan-desktop:~# lsmod | grep snd
snd_hda_intel         495844  5 
snd_hwdep              13064  1 snd_hda_intel
snd_seq_dummy           6020  0 
snd_seq_oss            39424  0 
snd_pcm_oss            55840  0 
snd_mixer_oss          20864  1 snd_pcm_oss
snd_seq_midi           10944  0 
snd_pcm               100232  3 snd_hda_intel,snd_pcm_oss
snd_rawmidi            30112  1 snd_seq_midi
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
snd_seq                67456  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29448  2 snd_pcm,snd_seq
snd_seq_device         10900  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78824  21 snd_hda_intel,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         13968  2 snd_hda_intel,snd_pcm
soundcore              10400  1 snd

---

### Post by drboontu on 2008-08-17
Hi,

I have searched the forum for:

82801G (ICH7 Family) High Definition Audio Controller (rev 01)

and it found some interesting results, "have a try yourself".

We need more info about your computer....

This is one result that looks interesting.

$ sudo killall pulseaudio

and restart any apps that need audio.

Also:
Open /etc/modprobe.d/alsa-base up in a text editor with superuser permissions, such as by running 'gksu gedit /etc/modprobe.d/alsa-base' in a run box (Alt+F2). Then you add a line to the bottom of that file as below, replacing the <model> part with a model that was listed as available to your chipset.
Code:
options snd-hda-intel model=<model>

Do the search yourself and see if it helps.
post back more info about your computer.

Edit:
The dmesg results are strange, I'm not sure why?

Cheers,

---

### Post by roshanjose on 2008-08-18
root@roshan-desktop:~# gedit /etc/modprobe.d/alsa-base

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel enable=1 index=0 model=basic
options snd-hda-intel model=82801G    {i added this line as per ur   instruction}

---

### Post by Inane_Asylum on 2008-08-20
I am working on getting my sound up and running on my laptop, too, and have made some progress.  My sound is **working**, but it is extremely quiet.  I can only really hear anything with headphones and the sound cranked all the way.

See if this works for you, as this is an entirely different problem than the sound not working at all...I had no idea for hours that it was actually working, but really really quiet.

---

### Post by xeth_delta on 2008-08-20
I believe that the model argument in /etc/modprobe.d/alsa-base is specific to the computer model itself, and of course the codec it uses for the soundcard.

Please run
```
cat /proc/asound/card0/codec#0 | grep -i codec
```
That would be the codec on your sound card. Please post the output.

In the (now not so often) cases where the sound does not work, you can find these parameters in the following way:

```

cp /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz ~
gunzip ~/ALSA-Configuration.txt.gz
gedit ALSA-Configuration.txt

```
Look for your laptop model and codec. some parameter options will be shown in there.

Make a back-up of /etc/modprobe.d/alsa-base.
After making changes to /etc/modprobe.d/alsa-base with administrative rights, restart the sound system:
```
sudo /etc/init.d/alsa-utils restart
``` or reboot.

Let us know if you need further help.

---

### Post by Uchiha_madara on 2008-08-20
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

May this help you

---

### Post by Uchiha_madara on 2008-08-20
Inane_Asylum your signature is Make me laugh 

I have the same problem

---

### Post by roshanjose on 2008-08-21
hey plzz consider my issue...i m not getting any sounds.....i have posted various results above this reply...

---

### Post by xeth_delta on 2008-08-21
> **roshanjose said:**
> hey plzz consider my issue...i m not getting any sounds.....i have posted various results above this reply...

Have you given my suggestion in post #8 a try? What brand and model is your computer?

---

### Post by Inane_Asylum on 2008-08-21
Also post the results of this command:

grep Codec /proc/asound/card0/codec#*

That should give us an idea of what you may need to add into alsa-base

---

### Post by xeth_delta on 2008-08-21
> **Inane_Asylum said:**
> Also post the results of this command:

grep Codec /proc/asound/card0/codec#*

That should give us an idea of what you may need to add into alsa-base

Indeed. To the OP, in order to help you we need more information from your side. As could be said, help us help you. ;)

---

### Post by roshanjose on 2008-08-23
Reply for post 8

root@roshan-desktop:~# grep Codec /proc/asound/card0/codec#*
Codec: SigmaTel STAC9221 A1
root@roshan-desktop:~# 
root@roshan-desktop:~# cat /proc/asound/card0/codec#0 | grep -i codec
cat: /proc/asound/card0/codec#0: No such file or directory
root@roshan-desktop:~# cp /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz ~
root@roshan-desktop:~# cp /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz ~
root@roshan-desktop:~# gunzip ~/ALSA-Configuration.txt.gz
gzip: /root/ALSA-Configuration.txt already exists; do you wish to overwrite (y or n)? y


mine is not a laptop..it's a desktop PC

---

### Post by Inane_Asylum on 2008-08-24
Are you using a sound card, or the onboard sound?

Try adding this line at the end of /etc/modprobe.d/alsa-base:

options snd-hda-intel model=auto

---

