---
title: "E-MU 1616m PCIe in linux"
date: 2010-01-11
forum: Hardware
---

### Post by maksymov on 2010-01-11
Hi! How about this sound card in ubuntu? Does anybody have it?

---

### Post by delysid on 2010-07-13
Just got one and was wondering the same thing.
Can't seem to get lucid to recognize it :(

Anyone able to get this working?

---

### Post by mcdebugger on 2011-06-30
Any news? I just bought 1616m pci-e card and it's not working. Microdock LEDs just randomly lights on each on/off. :(
Epic fail

---

### Post by mcdebugger on 2011-07-01
I applied patch from this bug: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5250](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5250)
and at least card is recognized by ALSA. I'll try to power on dock when I'll be home (I'm on my work now).

---

### Post by slipped_on_blade on 2011-07-01
Hi, did it work? I've got 1616m pci-e and I wonder if I can make it with ALSA. Otherwise I would have to exchange it to pci version.

---

### Post by mcdebugger on 2011-07-04
> **slipped_on_blade said:**
> Hi, did it work? I've got 1616m pci-e and I wonder if I can make it with ALSA. Otherwise I would have to exchange it to pci version.

Yep, works fine!
Apply patch from this bug: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5250](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5250)
You will also need to install emu firmware (try to find it in distro repo, I have gentoo on machine with E-MU card) into /lib/firmware and maybe even compile it into kernel)

[QUOTE=kev009]
05:04.0 Multimedia audio controller [0401]: Creative Labs SB0400 Audigy2 Value [1102:0008]

I applied the patch.

On boot I get:
EMU10K1_Audigy 0000:05:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
emu1010: Special config.
emu1010: EMU_HANA_ID = 0x3f
emu1010: filename emu/emu1010b.fw testing

a long delay and then

firmware: emu/emu1010b.fw not found. Err = -2
emu1010: Loading Firmware file emu/emu1010b.fw failed
EMU10K1_Audigy 0000:05:04.0: PCI INT A disabled
EMU10K1_Audigy: probe of 0000:05:04.0 failed with error -2

Seems to exist. Do I need to add udev rules or something?

kev-ws-aurora ~ # ls /lib/firmware/emu/
audio_dock.fw emu0404.fw emu1010b.fw emu1010_notebook.fw hana.fw micro_dock.fw
[/QUOTE]

[QUOTE=mcdebugger]
kev009, check CONFIG_EXTRA_FIRMWARE_DIR setting im kernel config.
Also you can try to build firmware into the kernel (set space-separated list of firmware files in CONFIG_EXTRA_FIRWMARE variable).

My example:

CONFIG_FIRMWARE_IN_KERNEL=y
CONFIG_EXTRA_FIRMWARE="radeon/R600_rlc.bin emu/emu1010b.fw emu/micro_dock.fw emu/hana.fw"
CONFIG_EXTRA_FIRMWARE_DIR="/lib/firmware"

radeon is for my radeon card so you may have something different.
[/QUOTE]

If you need JACK, don't forget to set capture device to hw:0,2, playback device to hw:0,3, input channels: 16, output channels: 16, set period to something like 64 or 128.
I'd recommend you also to use emutrix for managing EMU's mixer connections and settings.
If U experience fast playback issue, change clock rate to 44100 Hz (needed for example to work with PulseAudio or with ALSA device on hw:0,0).
P.S. PCI version is deprecated. I asked one shop on eBay does they have PCI version and there's PCI-E only. But it works just fine after applying this trivial patch that allows ALSA to recognize card by pci id that's different on PCI and PCI-E versions.
Good luck!

---

### Post by slipped_on_blade on 2011-07-04
So I applied this patch, but alsa still doesn't see my card.
dmesg:
> [  191.946142] snd_emu10k1 0000:06:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  191.946155] ALSA emu10k1_main.c:1781 vendor = 0x1102, device = 0x8, subsystem_vendor_id = 0x40071102, subsystem_id = 0x4007
[  191.946162] ALSA emu10k1_main.c:1817 Sound card name = SB Audigy 2 Value [Unknown], vendor = 0x1102, device = 0x8, subsystem = 0x40071102.
[  191.952827] ALSA emu10k1_main.c:226 Audigy2 value: Special config.
[  192.970809] snd_emu10k1 0000:06:04.0: PCI INT A disabled
[  192.970820] snd_emu10k1: probe of 0000:06:04.0 failed with error -5


It doesn't even say anything about firmware. Just fails.

---

### Post by mcdebugger on 2011-07-06
> **slipped_on_blade said:**
> So I applied this patch, but alsa still doesn't see my card.
dmesg:


It doesn't even say anything about firmware. Just fails.

It's strange cause your PCI ID is similar to one used in this patch. Did you compile this driver as module?
Please make sure that you loaded proper module into kernel or if it's built in-kernel, that you have proper kernel installed and booted.
Also you may try to temporarily disable an integrated sound card (if present) but in my case it works well with both.
P.S. please post somewhere your resulting emu10k1_main.c file. Thanks.

---

### Post by slipped_on_blade on 2011-07-06
I compiled driver using [this]("http://ubuntuforums.org/showthread.php?t=1681577") script, that compiles sources from /opt.

Here is my /opt/Alsa-1.0.24/alsa-driver-1.0.24/pci/emu10k1/emu10k1_main.c: [http://pastebin.com/AB2V5LMu]("http://pastebin.com/AB2V5LMu")

---

### Post by slipped_on_blade on 2011-07-14
Yes. I did it. So, that's what I did in my ubuntu:

First I downloaded, compiled and installed alsa drivers, firmwares and so on using this script [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577).

Then I downloaded kernel sources:
```
cd ~
mkdir ./linuxsrc
cd ./linuxsrc
sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)
```You can read more [here]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild") and [here]("https://help.ubuntu.com/community/Kernel/Compile").

Then I applied [this]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5250") patch to emu10k1_main.c:
```
patch ~/linuxsrc/linux-2.6.38/sound/pci/emu10k1/emu10k1_main.c /path/to/patch.patch
```Then I copied /lib/firmware/emu to ~/linuxsrc/firmware

Then I copied installed kernel config:
```
cp /boot/config-`uname -r` ~/linuxsrc/linux.kernel.folder./.config
```and added necessary lines, provided by mcdebugger:
```
CONFIG_FIRMWARE_IN_KERNEL=y
CONFIG_EXTRA_FIRMWARE="emu/emu1010b.fw emu/micro_dock.fw emu/hana.fw"
CONFIG_EXTRA_FIRMWARE_DIR="/lib/firmware"
```Then I compiled the kernel:
```
make-kpkg clean
CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```And then installed image and keaders .deb files, that compiled into ~/linuxsrc.

Rebooted, turned off onboard motherboard intel soundcard and configured card using emutrix and qjackctl.

That's it.

---

### Post by Abanom on 2012-01-20
Getting an error when I try to apply the Patch

Hunk #1 FAILED at 1415.
1 out of 1 hunk FAILED -- saving rejects to file

Not sure why.  Does anyone know how I can apply this patch?

---

### Post by tilt12345678 on 2012-02-15
I have m1616 PCIe on Linux 3.2.4 ALSA 1.0.25 (git).

[FONT=Courier New][SIZE=1]   lspci -v:
[/SIZE][/FONT][FONT=Courier New][SIZE=1]   03:04.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
           Subsystem: Creative Labs Device 4007

   /proc/asound/cards:
    0 [EMU1010        ]: Audigy2 - E-mu 1010 PCIe
                         E-mu 1010 PCIe (rev.0, serial:0x40071102) at 0xd800, irq 16[/SIZE][/FONT]

I manually applied the patch (just put the entry somewhere in the list in emu10k1_main.c). If you compile ALSA yourself, turning debug to 'full' makes the log a bit more informative.

What works: I tested with 48kHz up to 6 analog inputs (including preamps) as well as outputs. I/O attenuation works. Bass/Treble works. Sound can be very good if mixer levels are carefully adjusted.

What doesn't work (here): Routing anything to Phones L/R (which quite sad, working on it); instead, phones always play whats on Dock DAC 1L/R. Couldn't get the wavetable synth to play (personally, I don't miss it). Output numbering is really not correct and very much depends on which of the devices / subdevices one actually is using. AFAIK the developer coded this off the datasheets, so there could be some addressing bugs on driver level. JACKv1 makes trouble here (FIFO read errors), JACKv2 not so much (tested for up to 12 hours without problems, but had rare, pretty fatal screwups).

**UPDATE**: I could **not** get MIDI I/O via UART 1 & 2 to  work. Could be my bleeding edge installations from source; will repeat  the tests when I am on packages / proper dependencies again. Had to  upgrade alsa-lib and jack from source. Also added "snd-emu10k1  seq_ports=0" module option to remove the 32 (!) unneccessary MIDI  wavetable synth devices.

What I haven't tested yet: S/PDIF.

What I can't test: ADAT.

I would be very happy if other 1010B / 1616m users could tell me if only I have the afformentioned problems.

---

### Post by Abanom on 2012-02-18
Thanks for the info. I'll load mine up tonight, run some tests and let you know what happens.

---

### Post by tilt12345678 on 2012-02-21
I am now on


[LIST]
[*]linux kernel 3.2.4 with shipped ALSA 1.0.25
[*]installed  alsa-firmware 1.0.25
[*]manually applied patch to emu10k1_main.c
[/LIST]

and system works as described above.

GIT version of ALSA actually caused massive problems with libasound & all tools that use it (pretty much everything). :-D
Dock ADC capture levels are very low (using it with a "line level" synthesizer outputs, disabled 14dB input padding), I wonder if this is intentional.
Still unable to explicitly route anything to Phones L/R! :-?

Otherwise - hey it works, let's use it! :-)

---

### Post by Abanom on 2012-02-24
After a couple weeks of banging my head in the wall I finally got it.  From a clean ubuntu 11 x64 install i just had to install the new 1.0.25 ALSA drivers and thats it.  No patching or compiling was necessary. Looks like the issues have been addressed in the latest ALSA release. Everything works including the headphones.  Havn't tested the midi yet so i'll update later.

---

### Post by tilt12345678 on 2012-02-25
The card should appear as three devices:

   device 0: emu10k1 [ADC Capture/Standard PCM Playback]
   device 2: emu10k1 efx [Multichannel Capture/PT Playback]
   device 3: emu10k1 [Multichannel Playback]

Suppose your card is "hw:0"; for having more than 2 capture channels,  use "hw:0,2"; for more than 2 playback channels, use "hw:0,3".

Important: when I leave those devices on for a longer time, the dock gets *really* hot (and I mean *hot*). When I only use 2/2 it only gets slightly warm.

---

### Post by Abanom on 2012-03-12
> **Abanom said:**
> After a couple weeks of banging my head in the wall I finally got it.  From a clean ubuntu 11 x64 install i just had to install the new 1.0.25 ALSA drivers and thats it.  No patching or compiling was necessary. Looks like the issues have been addressed in the latest ALSA release. Everything works including the headphones.  Havn't tested the midi yet so i'll update later.

Correction, headphones are not working properly. Only able to route Doc1 to them.  I'm also not able to record higher then a 48000 sample rate. Havn't tried the midi yet.

---

### Post by M4st0d0n on 2012-08-06
Hello all,

Links to the patch in this thread are down but it still can be found here :

[http://mailman.alsa-project.org/pipermail/alsa-devel/2012-February/048602.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2012-February/048602.html)

And here's the patch renamed with .txt extension.

The card is partially working as described before, on Ubuntu TangoStudio (kernel 2.6.32-41-lowlatency).

---

### Post by mcdebugger on 2012-10-17
Patch appears to be applied as in [http://mailman.alsa-project.org/pipermail/alsa-devel/2012-October/056307.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2012-October/056307.html)

I hope it will reduce headache caused by configuring this card to work with ALSA for someone who not so familiar with kernel patching soon.
It'll be enough to install and configure alsa firmware for e-mu card to work with Linux.

Regards

---

### Post by Clockmender on 2012-10-26
Most of the frustration and head-banging-against-a-wall can be cured with these sound cards by opening alasmixer - type [COLOR="Purple"]alsamixer[/COLOR] in a terminal, select your sound card and set the clock rate to 44100 to playback music, then set it to 48000 if you want your midi device to work! (Left/Right arrow keys to get to the clock rate, Up/Down arrow keys to change it) Bear in mind that with clock rate set to 48000, music playback will be too high pitched and at 44100 midi input will not be keystrokes but probably programme/patch changes. Also Fedora recognises and installs all E-MU cards out of the box and automatically - no patches to kernel, no head-banging-on-a-wall, etc. (see my post here [http://ubuntuforums.org/showthread.php?p=12318995#post12318995](http://ubuntuforums.org/showthread.php?p=12318995#post12318995))

Just trying to help!

PS two of my three machines run Bunty 12.04 - as of September 2012, my music PC will go back to Bunty as soon as the E-MU card issue is resolved, i.e. it installs automatically from the LiveCD!

**D'oh of the year!**

Set Internal Clock rate to ADAT and both playback of music and Midi input work properly! I have set sample rate in Jack Audio Connection Kit Setup to 48000 as well, this may be relevant.

---

