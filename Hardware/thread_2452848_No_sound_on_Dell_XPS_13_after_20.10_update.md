---
title: "No sound on Dell XPS 13 after 20.10 update"
date: 2020-10-29
forum: Hardware
---

### Post by timjh3 on 2020-10-29
Since upgrading to Ubuntu 20.10 my Dell XPS has lost sound.  If I go to the settings then choose output device there are no options listed.

It looks like the audio device is found: -

```
tim@tim-xps:~$ sudo lspci
[sudo] password for tim: 
00:00.0 Host bridge: Intel Corporation Coffee Lake HOST and DRAM Controller (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (Whiskey Lake) (rev 02)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 0c)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Point-LP Thermal Controller (rev 30)
00:14.0 USB controller: Intel Corporation Cannon Point-LP USB 3.1 xHCI Controller (rev 30)
00:14.2 RAM memory: Intel Corporation Cannon Point-LP Shared SRAM (rev 30)
00:15.0 Serial bus controller [0c80]: Intel Corporation Cannon Point-LP Serial IO I2C Controller #0 (rev 30)
00:15.1 Serial bus controller [0c80]: Intel Corporation Cannon Point-LP Serial IO I2C Controller #1 (rev 30)
00:16.0 Communication controller: Intel Corporation Cannon Point-LP MEI Controller #1 (rev 30)
00:1c.0 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #5 (rev f0)
00:1c.6 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #7 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #9 (rev f0)
00:1d.4 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #13 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Cannon Point-LP LPC Controller (rev 30)
00:1f.3 Audio device: Intel Corporation Cannon Point-LP High Definition Audio Controller (rev 30)
00:1f.4 SMBus: Intel Corporation Cannon Point-LP SMBus Controller (rev 30)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Point-LP SPI Controller (rev 30)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
02:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
03:00.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
04:00.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
04:01.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
04:02.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
04:04.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
05:00.0 System peripheral: Intel Corporation JHL6540 Thunderbolt 3 NHI (C step) [Alpine Ridge 4C 2016] (rev 02)
39:00.0 USB controller: Intel Corporation JHL6540 Thunderbolt 3 USB Controller (C step) [Alpine Ridge 4C 2016] (rev 02)
6e:00.0 Non-Volatile memory controller: Toshiba Corporation Device 011a
```

The verbose output for the audio device is: -
```

00:1f.3 Audio device: Intel Corporation Cannon Point-LP High Definition Audio Controller (rev 30) (prog-if 80)
    DeviceName: Onboard - Sound
    Subsystem: Dell Cannon Point-LP High Definition Audio Controller
    Flags: bus master, fast devsel, latency 32, IRQ 161
    Memory at dc518000 (64-bit, non-prefetchable) [size=16K]
    Memory at dc200000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] Vendor Specific Information: Len=14 <?>
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_sof_pci


```

I've tried various suggestions, like reloading alsa...

```

tim@tim-xps:~$ sudo alsa force-reload
Unloading ALSA sound driver modules: snd-hda-codec-hdmi snd-sof-pci snd-sof-intel-byt snd-sof-intel-ipc snd-sof-intel-hda-common snd-soc-hdac-hda snd-sof-xtensa-dsp snd-sof-intel-hda snd-sof snd-hda-codec-realtek snd-hda-ext-core snd-hda-codec-generic snd-soc-acpi-intel-match snd-soc-acpi snd-soc-core snd-compress snd-pcm-dmaengine snd-hda-intel snd-intel-dspcfg snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-codec-generic snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-hdmi snd-sof-pci snd-sof-intel-byt snd-sof-intel-ipc snd-sof-intel-hda-common snd-soc-hdac-hda snd-sof-xtensa-dsp snd-sof-intel-hda snd-sof snd-hda-codec-realtek snd-hda-ext-core snd-hda-codec-generic snd-soc-acpi-intel-match snd-soc-acpi snd-soc-core snd-compress snd-pcm-dmaengine snd-hda-intel snd-intel-dspcfg snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.
tim@tim-xps:~$ 


```

I also tried: -
1) moving the `.config/pluse` to a back up directory then restarting.
2) `sudo apt-get update && sudo apt-get upgrade`
3) `alsactl restore`
4) `sudo alsa reload`


One thing I have found is if I run `pulseaudio --start` then the output device "Speakers - Built-in Audio" appears.  I can also hear the the alert sounds "bark" "drip" etc, and I can see the mic is working.  However, when I click "test" then "Front left" or "Front right" then there is no sound. Plugging in my headset has the same effect.  The headset is recognized, but no test sounds are played just the alert sounds.

Any ideas greatly appreciated!

---

