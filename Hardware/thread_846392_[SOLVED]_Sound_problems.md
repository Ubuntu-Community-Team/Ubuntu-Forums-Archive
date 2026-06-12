---
title: "[SOLVED] Sound problems"
date: 2008-07-01
forum: Hardware
---

### Post by spastas on 2008-07-01
Hi everybody,

I am completely new at Linux/Ubuntu. I have just installed the latest version of ubuntu on my laptop. The model is gateway 4530 gz. Everything seems to be working fine except for the sound. I've looked around and found no answer. It's unmuted but the sound still does not work.

Thanks a lot for any help

Spasta

---

### Post by zalberico on 2008-07-01
Welcome to gnulinux!

My sound didn't work until I double clicked on the little speaker in the top gnome panel toward the right, went to the tab called switches and checked the box that said speaker.

For some reason it was unchecked initially

It used to be that alsa (the advanced linux sound architecture) was muted by default, I don't know if this is still the case but opening up the terminal and typing alsamixer and checking that out may be it.

Goodluck!
z

---

### Post by balaknair on 2008-07-01
HI
In order to help you better, it'd be useful to know what hardware you're using(what make of soundcard). Linux generally has some issues with certain models(usually newer ones) like Creative XFi and Soundblaster series and Intel ICH8 family cards, because the manufacturers have not released Linux drivers and/or have not disclosed the specifications to enable the Linux community developers to write their own drivers. Workarounds exist for most problems though.
Of course it may something as simple as what zman14321 has noted above.

In case that doesn't work for you, it would be easier for others to better understand the issue and suggest a solution if you could provide some information:
Open a terminal(Applications menu> Accessories> Terminal) and copy paste the following commands, and post the output you get in this thread. It'll display your hardware specifications.
aplay -l
lspci -v

This will make it easier for others to figure out what is wrong.

---

### Post by balaknair on 2008-07-01
OK, I think I found in an old Ubuntuforums post something simple that ought to work, specific to the 4530gz laptop
([http://ubuntuforums.org/showthread.php?t=601516](http://ubuntuforums.org/showthread.php?t=601516))
The gist of it is given below
[I]Right click on the volume icon in the top panel. Choose &#8220;Open Volume Control.&#8221;

In the Volume Control,  select VIA 8237 if it&#8217;s not selected.

Select  Edit/Preferences in the menu, and on the dialog that pops up, checkmark &#8220;External Amplifier.&#8221;

Now Volume Control should have a third tab, &#8220;Switches.&#8221; The only setting on that tab is &#8220;External Amplifier,&#8221; a checkbox.  Uncheck the checkbox.[/I]



PS: If this helps or if you are able to get sound working some other way, please share that with us here(it might help someone else with similar issues, maybe even me :-P), and mark the thread as 'solved' so that others can find it easily.

All the best.

---

### Post by White Star on 2008-07-02
Hi I have the same problem and I did what you asked of spastas. When I typed "aplay -l" i got the following result:

> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Then when I typed "lspci -v" I got the following result
> 
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0000000-c00fffff
	Prefetchable memory behind bridge: d0000000-dfffffff
	Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
	Memory behind bridge: 40000000-400fffff
	Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
	Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 8440 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8420 [size=8]
	I/O ports at 8410 [size=4]
	I/O ports at 8400 [size=16]
	Memory at c0507000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 40100000 [disabled] [size=512K]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0504000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0505000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0506000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: 66MHz, medium devsel
	I/O ports at 8450 [size=16]
	Memory at c0507400 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8460 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f0200000-f02fffff
	Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 21
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0020000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 1361
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at 40000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

08:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at c0200000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

08:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at c0200800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:07.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: medium devsel, IRQ 15
	Memory at c0200c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:07.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff) (prog-if ff)
	!!! Unknown header type 7f

08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Hewlett-Packard Company Unknown device 30ba
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at a000 [size=256]
	Memory at c0201400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

I am a complete novice and I have absolutely no idea what I am doing on the terminal window. Could you advice me as to what needs to be done to get my sound working?

---

### Post by Akash Singhal on 2008-07-02
type "alsamixer" and set the volume levels...it worked for me.
sometimes double-clicking the volume icon at the right top of the screen and adjusting the volume levels also helps.

---

### Post by spastas on 2008-07-02
Hey guys,

thanks a lot. I tried what balknair told me to do and it worked. I have sound now!!!
Thanks for all the help guys!

Spastas

---

### Post by balaknair on 2008-07-02
@Spastas: Glad to be able to help. Hope you enjoy the Ubuntu experience.

@White Star: Sorry for the delay in replying. I was at work, and could log onto Ubuntuforums just now.
Your sound card uses the snd-hda-intel ALSA module.
If you're using Ubuntu Hardy, I'm not too certain about the issues you have, since I'm still on Gutsy Gibbon, but since Hardy uses ALSA 1.0.15 by default, the following steps should fix your sound.

---

### Post by balaknair on 2008-07-02
open a terminal and enter the following commands

```
cat /proc/asound/card0/codec#* | grep Codec
```

this will tell you what codec your sound card type needs
for eg my card returned "Codec: Analog Devices AD1986A"
so the card I use is AD1986A. In your case I believe it will show ALC260, but I'm not 100% certain about that, so that's why I included this step.
If it's something other than ALC260 find your card configuration by checking the following link
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

in that page find your card model and check the details given.
eg

```
ALC260
797		  hp		HP machines
798		  hp-3013	HP machines (3013-variant)
799		  fujitsu	Fujitsu S7020
800		  acer		Acer TravelMate
801		  will		Will laptops (PB V7900)
802		  replacer	Replacer 672V
803		  basic		fixed pin assignment (old default model)
804		  test		for testing/debugging purpose, almost all controls can
805				adjusted.  Appearing only when compiled with
806				$CONFIG_SND_DEBUG=y
807		  auto		auto-config reading BIOS (default)

```

select the description that best matches your system(it ought to be either hp or hp-3013 since I'm assuming your PC is an HP).

then go back to the terminal and type

```
sudo gedit /etc/modprobe.d/alsa-base
```

*Note: When using a sudo command it will ask for your password. When you type in your password, the password field will remain blank and you will see just the cursor- ie, you won't see ****** symbols, that's normal, just type the passwrod in and press enter.*

This will open a file in Gedit(a text editor).
Paste this into the last line of the file

```
options snd-hda-intel model=MODEL
```

replace MODEL with your model(hp or hp-3013)
Save and exit
Reboot.

After restart you should have sound(remember you might have to unmute sound, since it's muted by default, by right-clicking on the speaker icon in the upper right corner).

If this doesn't work, just post a reply here and we'll try some more advanced stuff. If it works, enjoy your Ubuntu experience:) and post a reply here so that this might be helpful to someone else in the future.
Either way, feedback is appreciated.

All the best.

---

### Post by Cape Cairo on 2008-10-29
Hi there i'm also one of the Ubuntu newbies, i've just installed ubuntu hardy but cant get any sound. 

here's what i get on the terminal(aply -l)

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Can you help please.

---

