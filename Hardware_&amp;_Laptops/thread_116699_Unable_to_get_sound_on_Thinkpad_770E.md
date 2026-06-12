---
title: "Unable to get sound on Thinkpad 770E"
date: 2006-01-13
forum: Hardware &amp; Laptops
---

### Post by Demask on 2006-01-13
I have installed Ubuntu 5.10 on an old IBM Thinkpad 770E Type 9548 and I just can't get any sound. I do however hear the pc-speaker (whateveryou call it) sound when there's an errormessage. But normal sound doesn't work. 

This is the output from lspci:
```
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
0000:00:02.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)
0000:00:03.0 VGA compatible controller: Trident Microsystems Cyber 9397 (rev f3)
0000:00:05.0 Multimedia controller: IBM 3780IDSP [MWave]
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 01)

```

Any help at all would be appreciated since I seem to be stuck with this problem, no linuxdistro I've tried has gotten the sound to work. And please explain carefully, It's been a while since I last used Ubuntu, or any linuxdistro as a matter of fact.

---

### Post by FarEast on 2006-01-15
Hi Demask,

The information may help;) .

[http://lists.debian.org/debian-laptop/2002/02/msg00116.html](http://lists.debian.org/debian-laptop/2002/02/msg00116.html)

To apply it to Breezy, what you have to do is the following:

1. Describe 'options cs4232 io=0x530 irq=5 dma=1 dma2=0 mpuio=0x330 mpuirq=9' in the file /etc/modprobe.d/sound .
2. Add an entry 'cs4232' in /etc/modules
3. Execute 'sudo update-modules' then 'sudo modprobe cs4232' .

I hope this helps.

---

### Post by Demask on 2006-01-15
First of all, thanks for helping. I did however not get the sound running. First, there was no "sound" in "/etc/modprobe.d". So I added it with gedit and copy/pasted what you described in the first step. Then I performed the second step, no problem there. Running "sudo update-modules", no trouble, but when i come to the second part of the third step i encounter the following problem: I try to run "sudo modprobe cs4232" and get the following error message:

```
Error inserting cs4232 (/lib/modules/2.6.12-9-386/kernel/sound/oss/cs4232 .ko): No such device
```

Note that I only followed the steps you described and restarted the computer. If I missed something, please point it out so I can try again. At this time I have no sound. When I try to open "Recording level" or "Volume meter" I get an errormessage that says: "Cannot connect to sound daemon. Please run "esd" at a command prompt". When doing what it tells me to this comes up:

```
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
```

I don't know if the esd-output is any help at all, I just added it to show what happens when i try to run an application related to the soundcard.'

Thankfull for any help at all, thanks so far FarEast.

---

