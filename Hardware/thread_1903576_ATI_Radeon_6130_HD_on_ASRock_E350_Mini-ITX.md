---
title: "ATI Radeon 6130 HD on ASRock E350 Mini-ITX"
date: 2012-01-02
forum: Hardware
---

### Post by HuckBerry on 2012-01-02
I recently got an ASRock E350M1/USB3 Mini-ITX motherboard. I was super excited about using the board for a HTPC given its low power consumption. 

I installed 10.04.3 LTS because I had it handy and because I prefer LTS versions. Most things worked out-of-the-box, except I can't seem to get any audio over the HDMI port.

I've been searching around the net for a few days but haven't found anything promising. I did poke around ALSA's website, but their lists seem focused only on soundcards and not graphics cards with audio over HDMI. (EDIT: also check out [this]("http://www.ubuntu.com/certification/catalog/component/pci:4383:1002-AUDIO") ubuntu.org page) I've included some information on the hardware being used:

Motherboard:
[NewEgg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157247")

lspci:
```

me@GAMMA:~$ sudo lspci -vv -n
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9802]
	Subsystem: ASRock Incorporation Device [1849:9802]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Region 1: I/O ports at f000 [size=256]
	Region 2: Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [100] Vendor Specific Information <?>

00:01.1 Audio device [0403]: ATI Technologies Inc Device [1002:1314]
	Subsystem: ASRock Incorporation Device [1849:1314]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at feb44000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [100] Vendor Specific Information <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
	Subsystem: ASRock Incorporation Device [1849:1892]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at feb40000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

lshw:
```

me@GAMMA:~$ sudo lshw -class multimedia
  *-multimedia:0          
       description: Audio device
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 1.1
       bus info: pci@0000:00:01.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:19 memory:feb44000-feb47fff
  *-multimedia:1
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 40
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=32
       resources: irq:16 memory:feb40000-feb43fff

```

modprobe:
```

me@GAMMA:~$ sudo modprobe -l | grep snd
kernel/sound/oss/msnd.ko
kernel/sound/oss/msnd_classic.ko
kernel/sound/oss/msnd_pinnacle.ko
kernel/sound/core/oss/snd-mixer-oss.ko
kernel/sound/core/oss/snd-pcm-oss.ko
kernel/sound/core/snd.ko
kernel/sound/core/snd-hwdep.ko
kernel/sound/core/snd-timer.ko
kernel/sound/core/snd-hrtimer.ko
kernel/sound/core/snd-pcm.ko
kernel/sound/core/snd-page-alloc.ko
kernel/sound/core/snd-rawmidi.ko
kernel/sound/core/seq/snd-seq.ko
kernel/sound/core/seq/snd-seq-device.ko
kernel/sound/core/seq/snd-seq-midi-event.ko
kernel/sound/core/seq/oss/snd-seq-oss.ko
kernel/sound/core/seq/snd-seq-dummy.ko
kernel/sound/core/seq/snd-seq-virmidi.ko
kernel/sound/core/seq/snd-seq-midi.ko
kernel/sound/core/seq/snd-seq-midi-emul.ko
kernel/sound/i2c/other/snd-ak4117.ko
kernel/sound/i2c/other/snd-ak4xxx-adda.ko
kernel/sound/i2c/other/snd-ak4114.ko
kernel/sound/i2c/other/snd-pt2258.ko
kernel/sound/i2c/other/snd-tea575x-tuner.ko
kernel/sound/i2c/snd-tea6330t.ko
kernel/sound/i2c/snd-i2c.ko
kernel/sound/i2c/snd-cs8427.ko
kernel/sound/drivers/snd-dummy.ko
kernel/sound/drivers/snd-virmidi.ko
kernel/sound/drivers/snd-serial-u16550.ko
kernel/sound/drivers/snd-mtpav.ko
kernel/sound/drivers/snd-mts64.ko
kernel/sound/drivers/snd-portman2x4.ko
kernel/sound/drivers/opl3/snd-opl3-lib.ko
kernel/sound/drivers/opl3/snd-opl3-synth.ko
kernel/sound/drivers/opl4/snd-opl4-lib.ko
kernel/sound/drivers/opl4/snd-opl4-synth.ko
kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
kernel/sound/drivers/mpu401/snd-mpu401.ko
kernel/sound/drivers/vx/snd-vx-lib.ko
kernel/sound/drivers/pcsp/snd-pcsp.ko
kernel/sound/isa/snd-adlib.ko
kernel/sound/isa/snd-als100.ko
kernel/sound/isa/snd-azt2320.ko
kernel/sound/isa/snd-cmi8330.ko
kernel/sound/isa/snd-dt019x.ko
kernel/sound/isa/snd-es18xx.ko
kernel/sound/isa/snd-opl3sa2.ko
kernel/sound/isa/snd-sc6000.ko
kernel/sound/isa/snd-sgalaxy.ko
kernel/sound/isa/snd-sscape.ko
kernel/sound/isa/ad1816a/snd-ad1816a.ko
kernel/sound/isa/ad1848/snd-ad1848.ko
kernel/sound/isa/cs423x/snd-cs4231.ko
kernel/sound/isa/cs423x/snd-cs4236.ko
kernel/sound/isa/es1688/snd-es1688.ko
kernel/sound/isa/es1688/snd-es1688-lib.ko
kernel/sound/isa/gus/snd-gusclassic.ko
kernel/sound/isa/gus/snd-gus-lib.ko
kernel/sound/isa/gus/snd-gusmax.ko
kernel/sound/isa/gus/snd-gusextreme.ko
kernel/sound/isa/gus/snd-interwave.ko
kernel/sound/isa/gus/snd-interwave-stb.ko
kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
kernel/sound/isa/msnd/snd-msnd-lib.ko
kernel/sound/isa/msnd/snd-msnd-classic.ko
kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
kernel/sound/isa/opti9xx/snd-opti93x.ko
kernel/sound/isa/opti9xx/snd-miro.ko
kernel/sound/isa/sb/snd-sb-common.ko
kernel/sound/isa/sb/snd-sb16-dsp.ko
kernel/sound/isa/sb/snd-sb8-dsp.ko
kernel/sound/isa/sb/snd-sb8.ko
kernel/sound/isa/sb/snd-sb16.ko
kernel/sound/isa/sb/snd-sbawe.ko
kernel/sound/isa/sb/snd-es968.ko
kernel/sound/isa/sb/snd-sb16-csp.ko
kernel/sound/isa/sb/snd-emu8000-synth.ko
kernel/sound/isa/wavefront/snd-wavefront.ko
kernel/sound/isa/wss/snd-wss-lib.ko
kernel/sound/pci/snd-ad1889.ko
kernel/sound/pci/snd-als300.ko
kernel/sound/pci/snd-als4000.ko
kernel/sound/pci/snd-atiixp.ko
kernel/sound/pci/snd-atiixp-modem.ko
kernel/sound/pci/snd-azt3328.ko
kernel/sound/pci/snd-bt87x.ko
kernel/sound/pci/snd-cmipci.ko
kernel/sound/pci/snd-cs4281.ko
kernel/sound/pci/snd-cs5530.ko
kernel/sound/pci/snd-ens1370.ko
kernel/sound/pci/snd-ens1371.ko
kernel/sound/pci/snd-es1938.ko
kernel/sound/pci/snd-es1968.ko
kernel/sound/pci/snd-fm801.ko
kernel/sound/pci/snd-intel8x0.ko
kernel/sound/pci/snd-intel8x0m.ko
kernel/sound/pci/snd-maestro3.ko
kernel/sound/pci/snd-rme32.ko
kernel/sound/pci/snd-rme96.ko
kernel/sound/pci/snd-sis7019.ko
kernel/sound/pci/snd-sonicvibes.ko
kernel/sound/pci/snd-via82xx.ko
kernel/sound/pci/snd-via82xx-modem.ko
kernel/sound/pci/ac97/snd-ac97-codec.ko
kernel/sound/pci/ali5451/snd-ali5451.ko
kernel/sound/pci/au88x0/snd-au8810.ko
kernel/sound/pci/au88x0/snd-au8820.ko
kernel/sound/pci/au88x0/snd-au8830.ko
kernel/sound/pci/aw2/snd-aw2.ko
kernel/sound/pci/ctxfi/snd-ctxfi.ko
kernel/sound/pci/ca0106/snd-ca0106.ko
kernel/sound/pci/cs46xx/snd-cs46xx.ko
kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
kernel/sound/pci/lx6464es/snd-lx6464es.ko
kernel/sound/pci/echoaudio/snd-darla20.ko
kernel/sound/pci/echoaudio/snd-gina20.ko
kernel/sound/pci/echoaudio/snd-layla20.ko
kernel/sound/pci/echoaudio/snd-darla24.ko
kernel/sound/pci/echoaudio/snd-gina24.ko
kernel/sound/pci/echoaudio/snd-layla24.ko
kernel/sound/pci/echoaudio/snd-mona.ko
kernel/sound/pci/echoaudio/snd-mia.ko
kernel/sound/pci/echoaudio/snd-echo3g.ko
kernel/sound/pci/echoaudio/snd-indigo.ko
kernel/sound/pci/echoaudio/snd-indigoio.ko
kernel/sound/pci/echoaudio/snd-indigodj.ko
kernel/sound/pci/echoaudio/snd-indigoiox.ko
kernel/sound/pci/echoaudio/snd-indigodjx.ko
kernel/sound/pci/emu10k1/snd-emu10k1.ko
kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
kernel/sound/pci/emu10k1/snd-emu10k1x.ko
kernel/sound/pci/hda/snd-hda-codec.ko
kernel/sound/pci/hda/snd-hda-codec-realtek.ko
kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
kernel/sound/pci/hda/snd-hda-codec-analog.ko
kernel/sound/pci/hda/snd-hda-codec-idt.ko
kernel/sound/pci/hda/snd-hda-codec-si3054.ko
kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
kernel/sound/pci/hda/snd-hda-codec-conexant.ko
kernel/sound/pci/hda/snd-hda-codec-via.ko
kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
kernel/sound/pci/hda/snd-hda-intel.ko
kernel/sound/pci/ice1712/snd-ice1712.ko
kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
kernel/sound/pci/ice1712/snd-ice1724.ko
kernel/sound/pci/korg1212/snd-korg1212.ko
kernel/sound/pci/mixart/snd-mixart.ko
kernel/sound/pci/nm256/snd-nm256.ko
kernel/sound/pci/oxygen/snd-oxygen-lib.ko
kernel/sound/pci/oxygen/snd-hifier.ko
kernel/sound/pci/oxygen/snd-oxygen.ko
kernel/sound/pci/oxygen/snd-virtuoso.ko
kernel/sound/pci/pcxhr/snd-pcxhr.ko
kernel/sound/pci/riptide/snd-riptide.ko
kernel/sound/pci/rme9652/snd-rme9652.ko
kernel/sound/pci/rme9652/snd-hdsp.ko
kernel/sound/pci/rme9652/snd-hdspm.ko
kernel/sound/pci/trident/snd-trident.ko
kernel/sound/pci/ymfpci/snd-ymfpci.ko
kernel/sound/pci/vx222/snd-vx222.ko
kernel/sound/synth/snd-util-mem.ko
kernel/sound/synth/emux/snd-emux-synth.ko
kernel/sound/usb/snd-usb-audio.ko
kernel/sound/usb/snd-usb-lib.ko
kernel/sound/usb/usx2y/snd-usb-usx2y.ko
kernel/sound/usb/usx2y/snd-usb-us122l.ko
kernel/sound/usb/caiaq/snd-usb-caiaq.ko
kernel/sound/pcmcia/vx/snd-vxpocket.ko
kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
kernel/sound/soc/snd-soc-core.ko
kernel/sound/soc/codecs/snd-soc-ad1836.ko
kernel/sound/soc/codecs/snd-soc-ad1938.ko
kernel/sound/soc/codecs/snd-soc-ad73311.ko
kernel/sound/soc/codecs/snd-soc-ak4104.ko
kernel/sound/soc/codecs/snd-soc-ak4535.ko
kernel/sound/soc/codecs/snd-soc-ak4642.ko
kernel/sound/soc/codecs/snd-soc-cs4270.ko
kernel/sound/soc/codecs/snd-soc-l3.ko
kernel/sound/soc/codecs/snd-soc-pcm3008.ko
kernel/sound/soc/codecs/snd-soc-spdif.ko
kernel/sound/soc/codecs/snd-soc-ssm2602.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
kernel/sound/soc/codecs/snd-soc-twl4030.ko
kernel/sound/soc/codecs/snd-soc-uda134x.ko
kernel/sound/soc/codecs/snd-soc-uda1380.ko
kernel/sound/soc/codecs/snd-soc-wm8350.ko
kernel/sound/soc/codecs/snd-soc-wm8400.ko
kernel/sound/soc/codecs/snd-soc-wm8510.ko
kernel/sound/soc/codecs/snd-soc-wm8523.ko
kernel/sound/soc/codecs/snd-soc-wm8580.ko
kernel/sound/soc/codecs/snd-soc-wm8728.ko
kernel/sound/soc/codecs/snd-soc-wm8731.ko
kernel/sound/soc/codecs/snd-soc-wm8750.ko
kernel/sound/soc/codecs/snd-soc-wm8753.ko
kernel/sound/soc/codecs/snd-soc-wm8776.ko
kernel/sound/soc/codecs/snd-soc-wm8900.ko
kernel/sound/soc/codecs/snd-soc-wm8903.ko
kernel/sound/soc/codecs/snd-soc-wm8971.ko
kernel/sound/soc/codecs/snd-soc-wm8974.ko
kernel/sound/soc/codecs/snd-soc-wm8940.ko
kernel/sound/soc/codecs/snd-soc-wm8960.ko
kernel/sound/soc/codecs/snd-soc-wm8961.ko
kernel/sound/soc/codecs/snd-soc-wm8988.ko
kernel/sound/soc/codecs/snd-soc-wm8990.ko
kernel/sound/soc/codecs/snd-soc-wm8993.ko
kernel/sound/soc/codecs/snd-soc-wm9081.ko
kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
kernel/sound/soc/codecs/snd-soc-max9877.ko

```

---

### Post by Roasted on 2012-02-24
Well dang, a month and a half later and no luck? Hate to add to the pile but I'm having literally the EXACT same issue. I used 10.04.3 because it was handy... did all of the updates, etc. I have no audio over HDMI either.

Also, did you use fglrx video drivers? I heard the open source ones were good for 1080 playback but WOW I'm having some terrible screen lag... What's worse is fglrx doesn't come up as an option in hardware drivers... I'm half tempted to reinstall to 11.10 and install fglrx...

---

### Post by gordintoronto on 2012-02-24
Try 11.10.

---

### Post by lank23 on 2012-03-14
I think you need ALSA 1.24 with ubuntu 10.04
I also had an no audio issue with my nvidia GT240 card until I added these repositories

Read this post

[http://ubuntuforums.org/showthread.php?t=1819115](http://ubuntuforums.org/showthread.php?t=1819115)
 
Add these repositories from here

[https://launchpad.net/~team-iquik/+archive/alsa](https://launchpad.net/~team-iquik/+archive/alsa)

and here

[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)

then update

lank23

---

