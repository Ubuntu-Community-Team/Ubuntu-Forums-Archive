---
title: "no sound on toshiba satellite A100 with ubuntu 7.04"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by Sanchya on 2007-06-24
I have installed ubuntu 7.04 on Toshiba Satellite A100 .my sound is not working ....:-(

i search on net a lot .. and i found a clue from 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859)

that add a line  'Options snd-hda-intel model=auto' to  /etc/modprobe.d/alsa-base

but things are still not working ...

Kindly help.....

Thanks a ton in advance.....

output of   'lsmod | grep snd'

snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

---

### Post by rax_m on 2007-06-24
Hi 

Have you tried the following links:
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I've found that generally with Toshiba laptops (i use one) that the installation of the most recent alsa drivers works (as long as your sound card is being recognised).

---

### Post by rax_m on 2007-06-24
Probably also post the output of ```
 lspci -v 
```

---

### Post by Sanchya on 2007-06-26
> **rax_m said:**
> Hi 

Have you tried the following links:
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I've found that generally with Toshiba laptops (i use one) that the installation of the most recent alsa drivers works (as long as your sound card is being recognised).

Hiiiii,

Thanks for help !!! Yes I tried both the links ....... these links has so many options but my system's sound is still not working .. it may a smaal bug somewhere ....

---

### Post by Sanchya on 2007-06-26
> **rax_m said:**
> Probably also post the output of ```
 lspci -v 
```

[B]my lspci -v Output is 
[/B]


00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
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
        Memory behind bridge: c0100000-c01fffff
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at 8440 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8420 [size=8]
        I/O ports at 8410 [size=4]
        I/O ports at 8400 [size=16]
        Memory at c0507000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 44000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0504000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0505000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0506000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: 66MHz, medium devsel
        I/O ports at 8450 [size=16]
        Memory at c0507400 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8460 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, slow devsel, latency 64, IRQ 19
        Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: c0200000-c02fffff
        Prefetchable memory behind bridge: 40000000-43ffffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 22
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0020000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7106
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at c0100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

05:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=05, secondary=06, subordinate=06, sec-latency=176
        Memory window 0: 40000000-43fff000 (prefetchable)
        Memory window 1: 48000000-4bfff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at a000 [size=256]
        Memory at c0200000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by stchman on 2007-06-26
> **Sanchya said:**
> [B]my lspci -v Output is 
[/B]


00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
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
        Memory behind bridge: c0100000-c01fffff
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at 8440 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8420 [size=8]
        I/O ports at 8410 [size=4]
        I/O ports at 8400 [size=16]
        Memory at c0507000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 44000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0504000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0505000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0506000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: 66MHz, medium devsel
        I/O ports at 8450 [size=16]
        Memory at c0507400 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8460 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, slow devsel, latency 64, IRQ 19
        Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: c0200000-c02fffff
        Prefetchable memory behind bridge: 40000000-43ffffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 22
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0020000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7106
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at c0100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

05:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=05, secondary=06, subordinate=06, sec-latency=176
        Memory window 0: 40000000-43fff000 (prefetchable)
        Memory window 1: 48000000-4bfff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at a000 [size=256]
        Memory at c0200000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

I have a Toshiba A135-S2246 and this worked for me.  I have the same SB450 sound you have.

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

Look at the section on Toshiba laptop.

Hope this helps.

---

### Post by lisati on 2007-06-27
I had no sound on my A100 laptop after first installing Feisty. This was easily solved by installing the updates recommended by the update manager and checking the volume control.

---

### Post by Sanchya on 2007-06-28
> **stchman said:**
> I have a Toshiba A135-S2246 and this worked for me.  I have the same SB450 sound you have.

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

Look at the section on Toshiba laptop.

Hope this helps.


Ooooh!!!!!!!

I had hope with your comment but nothing worked!! :-( 

In the feisty tips site ( the link mentioned above) , i followed each step it was responding well but after rebooting no sound appear.
I checked at volume control prefrences it is showing two devices 
One is HDA ATI SB (Alsa Mixer) and other is 
Realtech ALC861-VD (OSS mixer)

I tried both options but nothing is working... I m hoping that it isn't a problem....  :confused:

I also have same problem of logoff mention in the site ....


Can anybody still help me out ????

Thanks a ton in advance

---

### Post by Sanchya on 2007-06-28
> **lisati said:**
> I had no sound on my A100 laptop after first installing Feisty. This was easily solved by installing the updates recommended by the update manager and checking the volume control.

i also update all repository and then install all the updates.......but sound is not working ... can you give me some detail .. 

Or otherwise i should reinstall feisty.. :-(

---

### Post by Sparkster185 on 2007-06-28
I have the same laptop.  Try this:

[http://ubuntuforums.org/showthread.php?t=455266&highlight=Toshiba+sound+fix](http://ubuntuforums.org/showthread.php?t=455266&highlight=Toshiba+sound+fix)

You should use "model=3stack", not "model=auto".

---

### Post by stchman on 2007-06-28
> **Sparkster185 said:**
> I have the same laptop.  Try this:

[http://ubuntuforums.org/showthread.php?t=455266&highlight=Toshiba+sound+fix](http://ubuntuforums.org/showthread.php?t=455266&highlight=Toshiba+sound+fix)

You should use "model=3stack", not "model=auto".

I had him insert this line into his /etc/modprobe.d/alsa-base file:

options snd-hda-intel probe_mask=8 model=3stack

He said it did not work.

He might need to install a new Alsa driver.

---

### Post by Sanchya on 2007-06-28
> **Sparkster185 said:**
> I have the same laptop.  Try this:

[http://ubuntuforums.org/showthread.php?t=455266&highlight=Toshiba+sound+fix](http://ubuntuforums.org/showthread.php?t=455266&highlight=Toshiba+sound+fix)

You should use "model=3stack", not "model=auto".

Yes ... i tried with both options.....but no on worked for me .... it is being hell 4  me....

Well !!! thanks 4 help ..... give me some other solution

---

### Post by lisati on 2007-06-28
> **Sanchya said:**
> i also update all repository and then install all the updates.......but sound is not working ... can you give me some detail .. 

Or otherwise i should reinstall feisty.. :-(

What I did was click on the icon for "Updates are ready for your computer" icon (an alternative is through System->Administration->Update manager), and allow the updates to install. I then restarted the computer, double-clicked on the little speaker (the volume control) and turned up the volume. No problems since.

---

### Post by Sanchya on 2007-08-17
I have re-installed my system and run update manager... after that error was removed for the sound driver but .. no sound coming up ... i have checked all volume control options... but nothing is working..

cud anybody .plzzzzzzzzz help me out.

---

### Post by c-f on 2007-08-17
I have Toshiba A100 and had the same issue.
What work for me was:
- Install the latest ALSA driver
- Add the following line in alsa-base:

sudo gedit /etc/modprobe.d/alsa-base
options snd-hda-intel probe_mask=8 model=auto

Hope this work!
:guitar:

c-f

---

