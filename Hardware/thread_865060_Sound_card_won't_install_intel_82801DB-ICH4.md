---
title: "Sound card won't install intel 82801DB-ICH4"
date: 2008-07-20
forum: Hardware
---

### Post by angloscot on 2008-07-20
Hi there, I've got a fresh install of Ubuntu on an IBM X31 laptop (Installed via Wubi, and dual booting with windows XP). The problem I have is that I can't get any sound. So far I've tried:

1. reinstalling Ubuntu completely, 

2. following the sound instructions from [the general sound troubleshooting page]("https://help.ubuntu.com/community/SoundTroubleshooting#General%20Help"), 

3. and the intel and alsa websites. 

I've got through the troubleshooting page and done these things none with any success:

3.1 in a shell typing aplay -l 
3.1.1 which gets "no soundcard found2
3.2 in a shell typing lspci -v
3.2.1 which gets

[I]graeme@graeme-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
	Subsystem: IBM Thinkpad T40 series
	Flags: bus master, fast devsel, latency 0
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 96
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: e0000000-e7ffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: IBM ThinkPad
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: IBM ThinkPad
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: IBM ThinkPad
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1840 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: IBM ThinkPad
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at c0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=08, sec-latency=64
	I/O behind bridge: 00004000-00008fff
	Memory behind bridge: c0200000-cfffffff
	Prefetchable memory behind bridge: e8000000-efffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: IBM ThinkPad
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1860 [size=16]
	Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
	Subsystem: IBM ThinkPad
	Flags: medium devsel, IRQ 11
	I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: IBM Unknown device 0534
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at c0000c00 (32-bit, non-prefetchable) [size=512]
	Memory at c0000800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
	Subsystem: IBM ThinkPad T41
	Flags: medium devsel, IRQ 11
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA controller])
	Subsystem: IBM Unknown device 052f
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 3000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
	Subsystem: IBM Unknown device 0532
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at b0000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: e8000000-ebfff000 (prefetchable)
	Memory window 1: c4000000-c7fff000
	I/O window 0: 00004000-000040ff
	I/O window 1: 00004400-000044ff
	16-bit legacy interface ports at 0001

02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
	Subsystem: IBM Unknown device 0532
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at b1000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=07, subordinate=07, sec-latency=176
	Memory window 0: ec000000-effff000 (prefetchable)
	Memory window 1: c8000000-cbfff000
	I/O window 0: 00004800-000048ff
	I/O window 1: 00004c00-00004cff
	16-bit legacy interface ports at 0001

02:00.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 02) (prog-if 10 [OHCI])
	Subsystem: IBM Unknown device 0533
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at c0205000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
	Subsystem: AIRONET Wireless Communications Unknown device 5000
	Flags: bus master, fast devsel, latency 64, IRQ 11
	I/O ports at 8000 [size=256]
	Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
	Memory at c0400000 (32-bit, non-prefetchable) [size=4M]
	[virtual] Expansion ROM at c0800000 [disabled] [size=2M]
	Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
	Subsystem: IBM ThinkPad R40
	Flags: bus master, medium devsel, latency 66, IRQ 11
	Memory at c0204000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 8400 [size=64]
	Capabilities: <access denied>[/I]

from which I assumed that I have an intel 82801DB-ICH chip in there.

3.3 so I found the driver which was intel8x0 and installed it.
3.4 I ran sudo modprobe snd-intel8x0
3.4.1 At which point the terminal hung/crashed.


3.5 So I moved on to the fresh kernal approach typing
3.5.1     *

      Remove these packages sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
    *

      Reinstall those same packages sudo apt-get install linux-sound-base alsa-base alsa-utils 
3.5.2 and rebooted, and then had to reinstall gdm ubuntu-desktop
3.5.3 ran sudo modprobe snd-intel8x0
3.5.4 At which point the terminal hung/crashed.

3.6 So I tried to install it from alsa-source doing:
#

Type sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
#

Type sudo dpkg-reconfigure alsa-source

3.6.1 which worked perfectly, and the install line showed that it had been installed after I'd typed:
sudo module-assistant a-i alsa-source
3.6.2 ran sudo modprobe snd-intel8x0
3.5.4 At which point the terminal hung/crashed.

So here's the problem I can't find a way to either: get aplay -l to find anything, or to get sudo modprobe to do anything other than hang or crash. I've spent two days on it already and it's sending me crazy. I love Ubuntu and use it on my other box without any problems but here it's just not clicking (and as XP on this machine gets sound fine I know it's software/driver side problem rather than soundcard problem).

If anyone could help I'd be eternally grateful. (Failing that if anyone knows a distro that does work on a x31 thinkpad I'd be in pretty much the same situation)
:confused:

---

### Post by rudolfo_caruso on 2008-07-24
Hi, i also tried to install Xubuntu tom my good old X31. 
I also had no sound. I checked the CD of Xubuntu 7.10 and here everything worked fine.
Dont know which is the best Linux for X31 at the moment. I checked several actual distributions and **none** worked out of the box.
Mandriva One 2008.1 had no network, actual Xubuntu had no sound and booted very slow also with splash screen disabled. 
At the moment im installing Mandriva One 2008.0 wich also seems to work out of the box. Dont want to use Xubuntu 7. I will check back xubuntu in a few months to see if it works then.
As im a Linux Newbie i need something that runs out of the box. 
So for the X31 Xubuntu 7.10 or Ubuntu 7.10 should work fine. Or Mandriva One 2008.0 (from last year). Also Zenwalk Linux is not to bad but i dont like the package manager there.
Hope this was helpful to you.

---

### Post by angloscot on 2008-07-24
Ahh, I switched over to Ubuntu 8.04.1 and while that seemed to take care of everything else for some reason the sound still is dead, I think it must be a recognition thing. I tried openSuse but that didn't seem to make any different.

Funnily enough I noticed something odd about the splash screen two, it does take an age to load and frequently switches over to text and then back to the splash screen. When I've got more time to fiddle I'll try a more fiddles, and look around for another kludge, if I come up with anything I'll let you know.

cheers.

---

### Post by rudolfo_caruso on 2008-08-04
Hi, did you find a solution yet ?  
I would love to switch back to ubuntu.
Cheers

---

### Post by angloscot on 2008-08-04
No, and what's worse I broke the ethernet port on it so I've been trying to install a pcmcia card as well without any success. It's such a drag because its so much more stable than windows on this ati graphics card.

---

### Post by goldfish654 on 2008-08-04
I've got this problem too, but I don't want to be swapping distros.  

Here's some more relevant info
```

kernel:  2.6.24-19-generic 


lspci output:
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LYh

lsmod | grep snd output

snd_intel8x0           35376  1 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm


asound output
 naxxtor@jackson:~$ cat /proc/asound/cards 
--- no soundcards ---

 asoundconf list
Names of available sound cards:


```

I've also tried installing alsa modules from source with m-a, to no avail.  

When I try to rrmmod snd_intel8x0, it says it's in use.  Even when I rmmod -f it.  When I try to modprobe it, it hangs.. strace show that it's stuck in a loop doing this:
```

open("/proc/modules", O_RDONLY)         = 4
fstat64(4, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f31000
read(4, "nfsd 228848 13 - Live 0xf8fbd000"..., 1024) = 1024
read(4, "0 - Live 0xf8bb4000\nsbshc 7680 1"..., 1024) = 1024
nanosleep({0, 100000000}, NULL)         = 0
close(4)                                = 0
munmap(0xb7f31000, 4096)                = 0

```
Which leads me to think that it's waiting for a resource to become unbusy. Hmm... not sure where the nfsd reference is coming from mind ...

---

### Post by goldfish654 on 2008-08-04
Oh, also alsactl doesn't seem to work right either:
```

$ sudo alsactl names
alsactl: for_each_card:51: No soundcards found...
alsactl: generate_names:525: probe 0 failed: No such device
alsactl: for_each_card:51: No soundcards found...
alsactl: generate_names:525: probe 1 failed: No such device
alsactl: for_each_card:51: No soundcards found...
alsactl: generate_names:525: probe 2 failed: No such device

```

Hmmm...

---

### Post by goldfish654 on 2008-08-04
I've been talking to people in #alsa, and its looking like the sound card isn't on the IRQ it's supposed to be.  i.e.
```

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

```
Indiciates it's on IRQ 5, except cat /proc/inturrupts says
```

           CPU0       
  0:     206946    XT-PIC-XT        timer
  1:       1676    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:          1    XT-PIC-XT      
  4:          4    XT-PIC-XT      
  5:          0    XT-PIC-XT        yenta
  7:          0    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
  9:          2    XT-PIC-XT      
 10:          2    XT-PIC-XT      
 11:       5437    XT-PIC-XT        uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, ehci_hcd:usb4, ohci1394, yenta, eth1, radeon@pci:0000:01:00.0
 12:      12974    XT-PIC-XT        i8042
 14:      23893    XT-PIC-XT        libata
 15:          0    XT-PIC-XT        libata
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0


```

And it's not there.  On a known working laptop with a similar configuraiton, you can see:
```

 5:   11289771          XT-PIC  uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, ehci_hcd:usb4, ohci1394, Intel 82801DB-ICH4, Intel 82801DB-ICH4 Modem, yenta, yenta, wifi0, eth1, radeon@pci:0000:01:00.0

```

I'm thinking this might be a BIOS issue.  Strange, since the card worked fine under Windows ... as far as I know.

---

### Post by goldfish654 on 2008-08-05
Okay, got some news.

Installed debian etch - sound and wireless works out of the box.  
This is what I get with cat/proc/interrupts

```

           CPU0       
  0:     872318          XT-PIC  timer
  1:       4163          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:     192423          XT-PIC  uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, ehci_hcd:usb4, ohci1394, yenta, yenta, Intel ICH4, Intel 82801DB-ICH4 Modem, eth1, radeon@pci:0000:01:00.0
  6:          5          XT-PIC  floppy
  7:          3          XT-PIC  parport0
  8:          1          XT-PIC  rtc
  9:       2755          XT-PIC  acpi
 12:      53543          XT-PIC  i8042
 14:      65602          XT-PIC  ide0
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

```

This shows my sound card hanging off IRQ5 as it should be.  

So, I'm guessing it's a problem with the ubuntu kernel build, though I don't really know enough about the kernel to know where.

I think it's time to file a bug report.

---

### Post by angloscot on 2008-08-05
Ahh, if you've got it through Debian, then presumably at some point it will get incorporated. I looked at my output string before and it gave me the same string you put in the post two above, so I think mine must be on the wrong IRQ as well. Mm, I'll have to think about Debian I suppose, if it's going to work out of the box, other than that, yup a bug report seems to be the most likely thing to help that along a bit.

---

### Post by goldfish654 on 2008-08-06
I've made the bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254975](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254975)

I'm building the kernel from the git repos, see if the issue has already been solved somewhere.  If not I'll make an attempt to track down what exactly is causing it.

---

### Post by goldfish654 on 2008-08-07
Argh.  Nothing.

Since modprobe hangs, I thought I'd try to insmod it manually:
```

naxxtor@jackson:~$ sudo insmod /lib/modules/2.6.24-19-generic/kernel/sound/pci/snd-intel8x0.ko 
insmod: error inserting '/lib/modules/2.6.24-19-generic/kernel/sound/pci/snd-intel8x0.ko': -1 Unknown symbol in module

```

This may well be telling.  Bearing in mind this is compiled from the alsa-sources package, and now not the binary that shipped with Hardy.  

And some dmesg output from the attempted insmod:
```

[  275.913368] snd_intel8x0: Unknown symbol snd_ac97_pcm_close
[  275.914022] snd_intel8x0: Unknown symbol snd_ac97_resume
[  275.914228] snd_intel8x0: disagrees about version of symbol snd_pcm_new
[  275.914235] snd_intel8x0: Unknown symbol snd_pcm_new
[  275.914519] snd_intel8x0: disagrees about version of symbol snd_pcm_limit_hw_rates
[  275.914526] snd_intel8x0: Unknown symbol snd_pcm_limit_hw_rates
[  275.915233] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  275.915241] snd_intel8x0: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  275.915819] snd_intel8x0: Unknown symbol snd_ac97_pcm_open
[  275.916363] snd_intel8x0: Unknown symbol snd_ac97_set_rate
[  275.916634] snd_intel8x0: Unknown symbol snd_ac97_update_bits
[  275.916925] snd_intel8x0: Unknown symbol snd_ac97_mixer
[  275.917309] snd_intel8x0: Unknown symbol snd_ac97_bus
[  275.918330] snd_intel8x0: Unknown symbol snd_ac97_pcm_double_rate_rules
[  275.918643] snd_intel8x0: Unknown symbol snd_ac97_update_power
[  275.919143] snd_intel8x0: Unknown symbol snd_ac97_suspend
[  275.919611] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  275.919618] snd_intel8x0: Unknown symbol snd_pcm_lib_malloc_pages
[  275.919823] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_ioctl
[  275.919829] snd_intel8x0: Unknown symbol snd_pcm_lib_ioctl
[  275.920063] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_free_pages
[  275.920070] snd_intel8x0: Unknown symbol snd_pcm_lib_free_pages
[  275.920372] snd_intel8x0: disagrees about version of symbol snd_pcm_set_ops
[  275.920379] snd_intel8x0: Unknown symbol snd_pcm_set_ops
[  275.920629] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_list
[  275.920636] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_list
[  275.921453] snd_intel8x0: Unknown symbol snd_ac97_get_short_name
[  275.921671] snd_intel8x0: disagrees about version of symbol snd_pcm_suspend_all
[  275.921678] snd_intel8x0: Unknown symbol snd_pcm_suspend_all
[  275.922184] snd_intel8x0: Unknown symbol snd_ac97_pcm_assign
[  275.922392] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  275.922399] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_integer
[  275.922900] snd_intel8x0: disagrees about version of symbol snd_pci_quirk_lookup
[  275.922907] snd_intel8x0: Unknown symbol snd_pci_quirk_lookup
[  275.923209] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_msbits
[  275.923217] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_msbits
[  275.923650] snd_intel8x0: disagrees about version of symbol snd_pcm_period_elapsed
[  275.923657] snd_intel8x0: Unknown symbol snd_pcm_period_elapsed
[  275.923940] snd_intel8x0: Unknown symbol snd_ac97_tune_hardware

```

Oooh .... I wonder what this means.  Now, checking syslog:
```

Aug  7 18:11:43 jackson NetworkManager: <debug> [1218129103.429227] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Aug  7 18:11:43 jackson NetworkManager: <debug> [1218129103.476748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Aug  7 18:11:43 jackson NetworkManager: <debug> [1218129103.564006] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Aug  7 18:11:43 jackson NetworkManager: <debug> [1218129103.611707] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 

```

Errr, what?  What is NetworkManager doing with the sound device? Hmmm..... something fishy is going on.

---

### Post by angloscot on 2008-08-08
OK, that's way above my level of understanding! Do you think it's a problem with modprobe on the x31 then? I'd always assumed that the problem was further up, and that modprobe was just hanging because there was something wrong earlier in the chain. I think your bug report is exactly what I'm getting though, so hopefully someone will crack it.

---

### Post by goldfish654 on 2008-08-08
Okay, well, bascically, it's a problem with snd-intel8x0.  modprobe is just struggling because it can't insert the module properly.  The version of snd-intel8x0 is incompatible with the rest of the snd-* modules, for some strange reason - and compiling alsa from scratch doesn't help - which is even more bemusing.  

Interestingly, modprobe also hangs on boot for about a minute.  Possibly another module that's broken!  

But yeah, it's a problem with snd-intel8x0, not modprobe.

---

### Post by goldfish654 on 2008-08-08
Right, I'm getting closer to cracking this.

I managed to get sound working in the previous kernel version 2.6.24.18-386, by using the alsa-project sources and adding a line to the following file:
/etc/modprobe.d/alsa-base
```

options snd-snd-intel8x0 buggy_semaphore=1

```

I've yet to get it working with 2.6.24-19-generic though.  

(i've just noticed there was a typo in that file, so I'm not sure any more >_<)

---

### Post by dandielionous on 2012-12-17
I have been struggling along without sound on my Thinkpad T30 for several months.  The past couple of days I have said "Okay, let's get serious and fix this.

I use Zenwalk 7.  Okay, okay let me do this right. :)

Zenwalk 7
Thinkpad T30
I32801CA-ICH3

I have been trying to determine if it's the OS, Notebook, or the card.

Your's is some of the most intelligent discussion of this sound problem I have seen beyond the simple, first step things.

So I have included my output from cat/proc/interrupts.

root[asound]# cat /proc/interrupts
           CPU0       
  0:    7113015    XT-PIC-XT-PIC    timer
  1:      12032    XT-PIC-XT-PIC    i8042
  2:          0    XT-PIC-XT-PIC    cascade
  3:          4    XT-PIC-XT-PIC  
  4:          3    XT-PIC-XT-PIC  
  5:          3    XT-PIC-XT-PIC  
  6:          3    XT-PIC-XT-PIC    floppy
  7:          0    XT-PIC-XT-PIC    parport0
  9:       5921    XT-PIC-XT-PIC    acpi
 10:          3    XT-PIC-XT-PIC  
 11:      22802    XT-PIC-XT-PIC    uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, Intel 82801CA-ICH3, yenta, yenta, radeon@pci:0000:01:00.0, eth0, eth1
 12:     776061    XT-PIC-XT-PIC    i8042
 14:      53288    XT-PIC-XT-PIC    ata_piix
 15:      33478    XT-PIC-XT-PIC    ata_piix
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
IWI:          0   IRQ work interrupts
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
ERR:          0
MIS:          0
root[asound]#

As you can see my last two items are ERR: and MIS:. 

If that means anything I don't know.

Anyway good discussion.  At least I feel I can put my mind to ease for the night and stop fighting this sound issue.

I hate to migrate away from Zenwalk.  I've used it for years off and on.

dandielionous

---

