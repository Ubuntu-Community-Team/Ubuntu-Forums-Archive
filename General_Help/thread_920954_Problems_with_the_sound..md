---
title: "Problems with the sound."
date: 2008-09-15
forum: General Help
---

### Post by Aeghaynn on 2008-09-15
I've been running Ubuntu hardy for a while now and most of the time has been spent trying to get the sound to work and I've completely run out of options except the forums. The guide I mainly followed was the following guide.

------------------------------
 I got sound to work by doing two things. The first might not have been necessary so try step #2 first and see if that alone works. I know 

1.  Install the newest alsa driver by compiling it from scratch.  This page shows how to do that pretty well.  [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Still no sound so I did step 2...

2.  Edit the file /etc/modprobe.d/alsa-base to add a line at the end that reads options snd-hda-intel model=mbp3

I think that means that the kernel sets up the audio chip the same way the mac book pro does. After that, sounds works but the headphones don't.

I plan to test other model options such as arima, targa, asus-a7j, asus-a7m, macpro, imac24, w2jc, auto  to see if I can get the headphones to work.  imac24 looks interesting because that's supposed to have jack detection.  I'll post back after testing.

------------------------------------------------

I would appreciate it if anyone here could help me.
My laptops model is and Area-51 m15x.

---

### Post by mali2297 on 2008-09-17
In a terminal, run the following commands (copy/paste)
```

uname -a
cat /etc/issue
aplay -l
lspci -v | grep -A 5 [Aa]udio

```
Post the output.

---

### Post by JohnParker on 2008-09-17
johnny@ubuntujohnnyscomputer:~$ uname -a
Linux ubuntujohnnyscomputer 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
johnny@ubuntujohnnyscomputer:~$ cat /etc/issue
Ubuntu 8.04.1 \n \l

johnny@ubuntujohnnyscomputer:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
johnny@ubuntujohnnyscomputer:~$ lspci -v | grep -A 5 [Aa]udio
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 820f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at bfffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

I have no sound at all too :(

---

### Post by mali2297 on 2008-09-17
> **JohnParker said:**
> johnny@ubuntujohnnyscomputer:~$ uname -a
Linux ubuntujohnnyscomputer 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
johnny@ubuntujohnnyscomputer:~$ cat /etc/issue
Ubuntu 8.04.1 \n \l

johnny@ubuntujohnnyscomputer:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
johnny@ubuntujohnnyscomputer:~$ lspci -v | grep -A 5 [Aa]udio
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 820f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at bfffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

I have no sound at all too :(

Try
```

aplay /usr/share/sounds/login.wav

```
Do you hear anything? Does it look like it's playing the file? Any error message?

---

### Post by JohnParker on 2008-09-17
johnny@ubuntujohnnyscomputer:~$ aplay /usr/share/sounds/login.wav
ALSA lib confmisc.c:768:(parse_card) cannot find card 'VT8zxx'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:546: audio open error: No such device
johnny@ubuntujohnnyscomputer:~$ 
johnny@ubuntujohnnyscomputer:~$ 

Still no sound.

---

### Post by Aeghaynn on 2008-09-18
miguel@miguel-laptop:~$ lspci -v | grep -A 5 [Aa]udiouname -a
miguel@miguel-laptop:~$ cat /etc/issue
Ubuntu 8.04.1 \n \l

miguel@miguel-laptop:~$ aplay -l
aplay: device_list:205: no soundcards found...
miguel@miguel-laptop:~$ lspci -v | grep -A 5 [Aa]udio
 Any idea?

---

### Post by mali2297 on 2008-09-18
> **Aeghaynn said:**
> miguel@miguel-laptop:~$ lspci -v | grep -A 5 [Aa]udiouname -a
miguel@miguel-laptop:~$ cat /etc/issue
Ubuntu 8.04.1 \n \l

miguel@miguel-laptop:~$ aplay -l
aplay: device_list:205: no soundcards found...
miguel@miguel-laptop:~$ lspci -v | grep -A 5 [Aa]udio
 Any idea?

Try just
```

lspci -v

```
Can't you see your sound card listed? 

Can you rule out a hardware problem? If you have another OS (like Windows) on the same computer, does the sound work with that?

---

### Post by Doc Catfish on 2008-09-20
I, a true noob, am also having extreme difficulty in obtaining sound.  I too have an ALC 662 chip set manufactured by Realtec.  I fear the problem may lie with the chip.  Realtec is *not* listed as a supported vendor.  *Please* tell me I'm wrong and there is a fix.

---

### Post by Aeghaynn on 2008-09-26
I know it's not a hardware problem because I have sound on windows. Also what I got from the command line was:



miguel@miguel-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f0604800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: c2000000-c20fffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Memory behind bridge: c2100000-c21fffff
	Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: c2200000-c22fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at f0604c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Memory behind bridge: f0500000-f05fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 217
	I/O ports at 18d8 [size=8]
	I/O ports at 18cc [size=4]
	I/O ports at 18d0 [size=8]
	I/O ports at 18c8 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f0604000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: medium devsel, IRQ 10
	Memory at c2300000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8700M GT (rev a1) (prog-if 00 [VGA controller])
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

05:00.0 FireWire (IEEE 1394): Agere Systems Unknown device 5901 (rev 06) (prog-if 10 [OHCI])
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at c2000000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
	Subsystem: Intel Corporation Unknown device 1100
	Flags: bus master, fast devsel, latency 0, IRQ 215
	Memory at c2100000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, fast devsel, latency 0, IRQ 216
	Memory at c2200000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>

0a:09.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at f0500800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0a:09.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, medium devsel, latency 32
	Memory at f0500c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0a:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, medium devsel, latency 32
	Memory at f0501000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0a:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, medium devsel, latency 32
	Memory at f0501400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

---

### Post by jockben on 2008-09-26
Hi this is jockben.Problems with the sound is caused deaf and bp,heart problem also accured so it is dangerous to helth.
********************************************
jockben
[Job Openings ]("http://jobs.gov-auctions.org")

---

### Post by mali2297 on 2008-09-27
> **Aeghaynn said:**
> 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


There's your sound card.

A quick search for "82801h" lead me here:
[http://ubuntuforums.org/showthread.php?t=747054](http://ubuntuforums.org/showthread.php?t=747054)

Perhaps it can help you.

---

### Post by Buntuyang on 2008-09-27
This worked for me

"Helpful post, though in 8.04 you need to double click on the volume control, click on Edit/Preferences, then check External amplifier to be visible. The switches tab then appears. Uncheck External amplifier in that tab. Worked for me anyway."


[http://www.seopher.com/articles/how_to_fix_the_no_sound_in_ubuntu_7_10_on_a_laptop_or_notebook](http://www.seopher.com/articles/how_to_fix_the_no_sound_in_ubuntu_7_10_on_a_laptop_or_notebook)

---

### Post by Aeghaynn on 2008-10-07
> **mali2297 said:**
> There's your sound card.

A quick search for "82801h" lead me here:
[http://ubuntuforums.org/showthread.php?t=747054](http://ubuntuforums.org/showthread.php?t=747054)

Perhaps it can help you.

Thanks for the help but it didn't work. I've been searching and trying different solutions but none of them work. What does the capabilities<access denied> mean? Thanks for the help. The second solution didn't work either.

---

