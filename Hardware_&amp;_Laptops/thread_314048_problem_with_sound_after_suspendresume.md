---
title: "problem with sound after suspend/resume"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by svurg on 2006-12-06
I posted this first over in the sound forum, but I thought I should try here as well.

I'm having a heck of a time diagnosing a sound problem, and am hoping that someone here has run into something similar and can help.

I've got an ASUS K8V SE motherboard (VIA chipset, latest BIOS), Athlon-64 3200, Audigy 2 ZS, and am running Edgy 64 bit.

The system recognizes the sound card, and it works just fine in stereo mode after bootup (I haven't tried to deal yet with 5.1).

The trouble starts after I suspend (which I do to save power) and later resume. From that point until I reboot, if I put any kind of load on the system, sound drops out and all I get is a continuous tone.

The same behavior occurs on Windows XP (which I have dual-booting on this system) -- fine on initial boot, useless after resume. I've tried using different PCI slots -- same result. I've also confirmed that the slot I have it in now (one from the bottom) is not shared with any other devices.

My searches have indicated that the issue may be PCI bus latency -- when I start pushing data from the hard drive across the bus, the sound card gets starved and can't maintain its sound data stream. While there are some suggestions regarding changing some BIOS settings, nothing so far has worked for me.

Needless to say, I'm pretty frustrated. If anybody has any ideas how I can resolve the issue, I'd be greatly appreciative. Yeah, I could just shut down and reboot instead of suspend/resume, but I'd hate to give up the convenience.

Stumped,

Warren Madden

---

### Post by xemvip on 2006-12-07
I wonder if I have the same problem...  I have an IBM Thinkpad T22.  The soundcard works fine after booting from power-off, but does not work when resuming from suspend state.

alsamixer runs as expected and indicates no muted channels.

An attempt to play an mp3 file with mplayer results with the following:

[FONT="Courier New"][B]Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
alsa-init: using device default
alsa: 22050 Hz/2 channels/4 bpf/32768 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 22050Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 272.0 (04:32.0) ??,?%[/B][/FONT]

mplayer never returns an error, but never plays the song.  I left it for five minutes and finally did a CTRL-C to break out of it.

If I open an mp3 with XMMS it also stays at 0:00 and never plays or reports any error.

I've been looking at dmesg, and I don't see anything that looks suspicious to me except this part of the sleep message:

[FONT="Courier New"]**ACPI: PCI interrupt for device 0000:00:05.0 disabled**[/FONT]

If I understand correctly, this is my sound card.  I deduced this from the output of `lspci -v` :

[FONT="Courier New"][B]00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
        Subsystem: IBM Unknown device 0153
        Flags: bus master, slow devsel, latency 64, IRQ 11[/B][/FONT]

I see the message that the system is disabling the interrupt for device 0:05, but there is no message that (to me) seems to indicate that it wakes the card back up after sleep mode.

I see plenty of messages about resuming device 0:06, which is my ethernet card, but nothing about 0:05.

Does this give anyone any ideas?

---

### Post by svurg on 2006-12-07
I don't think this is the same problem, but perhaps someone more knowledgeable than me in this area will shed some light on things.

I've seen several postings here about sound not working at all after suspend/resume, but in my case it seems to want to work, but somehow the data stream is getting corrupted and all that comes out is a high-pitched (and very annoying, I might add) tone.

Once I reboot, everything is fine.

Again, I get the same behavior in Windows, so the problem seems to be down at the hardware/BIOS level, as opposed to the ALSA or Windows driver level.  I know it's a long shot, but I'm hoping that somebody will have some ideas on how I can resolve the issue.

Warren Madden

---

