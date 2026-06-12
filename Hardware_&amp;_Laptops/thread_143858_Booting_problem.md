---
title: "Booting problem"
date: 2006-03-13
forum: Hardware &amp; Laptops
---

### Post by aNiMe_FrEaK on 2006-03-13
Hi

I was using ubuntu since Warty on my Dell Latitude C600, now I'm using Breezy and I never had a problem, but recently a weird think is happening, my laptop is a PIII 850MHz, 265 ram, ESS Maestro sound, well one day when I start booting my system this problem happened, after a lot of restars, I use the Warty livecd and this is what it shows:

* version 2.85 booting...
* Creating initial device nodes...
Running Linux Kernel 2.6.7.
Processor 0 is Pentium III (Coppermine) 852MHz, 256 KB Cache
ACPI Bios found, activating modules: ac battery button fan processor thermal
USB found, managed by hotplug.
Firewire found, managed by hotplug.
Autoconfiguring devices... Done.
Mouse is Generic PS/2 Wheel Mouse at /dev/psaux
Soundcard: driver=ALSA(autodetect)
Video is Rage Mobility M3 AGP 2x, using XFree86(ati) Server
Monitor is Generic Monitor, H:28.0-96.0kHz, V:50.0-75.0Hz
Using Modes "1024x768" "800x600" "640x480"
Preparing modules for alsa...
Building card database...
Configuring maestro3...
Skipping update-modules...
Creating snddevices...
Loading driver...
divide error: 0000 [#1]
Modules linked in: snd_maestro3 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_timer snd soundcore 3c59x parport_pc parport 8250 serial_core ohci1394 ieee1394 ohci_hcd usbcore thermal processor fan button battery ac ide_scsi rtc cloop a100u2w megaraid atp870u aha152x ide_cd
CPU: 0
EIP: 0060:[] Not tainted
EFLAGS: 00000202 (2.6.7)
EIP is at acpi_processor_idle+0xeb/0x1f0 [processor]
eax: 00fd0d1e ebx: 00000808 ecx: 00000808 edx: 00000808
esi: d7e92ab0 edi: c03c72e0 ebp: d7e92a00 esp: c039bfc8
ds: 007b es: 007b ss: 0068
Process swapper (pid: 0, threadinfo=c039a000 task=c0311a80)
Stack: c039a000 00099100 c03c72e0 00418007 c01040db 00000002 c01000359
c039c5d8 c0311a80 00000000 00017fdb c03c7300 c010019f
Call Trace:
[] cpu_idle+0x2b/0x40
[] rest_init+0x19/0x20
[] start_kernel+0x188/0x190

Code: 73 18 f6 05 d1 07 3e c0 01 75 0e 05 ff ff ff 00 29 c8 25 ff
Kernel panic: Attempted to kill the idle task!
In idle task - no syncing

I don't know exactly what is the problem, the driver of my sound card or my sound card, but in my windows partition it works good, or another thing. I'm sad cause I love my laptop with ubuntu, I hope you can help me a bit.

Thanks.

P.D.: Forget my English :P

---

