---
title: "No Audio after April update (10.04 - The Lucid Lynx)"
date: 2010-06-09
forum: Hardware
---

### Post by SilentPirate007 on 2010-06-09
Hello,

After updating ubuntu with the April updates, I have no audio any more:

**Hardware:**
Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)

In terminal, [COLOR="Blue"]aplay -l[/COLOR] returns "no soundcards found"

[COLOR="blue"]lspci -v[/COLOR] does return information on my soundcard:

```

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8290
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f9df8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

[COLOR="blue"]sudo modprobe snd-[tab][/COLOR] returns 212 possibilties:

```

snd-ac97-codec           snd-echo3g               snd-hdspm                snd-opl3sa2              snd-seq-oss              snd-soc-wm8940
snd-ad1816a              snd-emu10k1              snd-hifier               snd-opl3-synth           snd-seq-virmidi          snd-soc-wm8960
snd-ad1848               snd-emu10k1-synth        snd-hrtimer              snd-opl4-lib             snd-serial-u16550        snd-soc-wm8961
snd-ad1889               snd-emu10k1x             snd-hwdep                snd-opl4-synth           snd-sgalaxy              snd-soc-wm8971
snd-adlib                snd-emu8000-synth        snd-i2c                  snd-opti92x-ad1848       snd-sis7019              snd-soc-wm8974
snd-ak4114               snd-emux-synth           snd-ice1712              snd-opti92x-cs4231       snd-soc-ad1836           snd-soc-wm8988
snd-ak4117               snd-ens1370              snd-ice1724              snd-opti93x              snd-soc-ad1938           snd-soc-wm8990
snd-ak4xxx-adda          snd-ens1371              snd-ice17xx-ak4xxx                   snd-oxygen               snd-soc-ad73311          snd-soc-wm8993
snd-ali5451              snd-es1688               snd-indigo               snd-oxygen-lib           snd-soc-ak4104           snd-soc-wm9081
snd-als100               snd-es1688-lib           snd-indigodj             snd-page-alloc           snd-soc-ak4535           snd-soc-wm-hubs
snd-als300               snd-es18xx               snd-indigodjx            snd-pcm                  snd-soc-ak4642           snd-sonicvibes
snd-als4000              snd-es1938               snd-indigoio             snd-pcm-oss              snd-soc-core             snd-sscape
snd-atiixp               snd-es1968               snd-indigoiox            snd-pcsp                 snd-soc-cs4270           snd-tea575x-tuner
snd-atiixp-modem         snd-es968                snd-intel8x0             snd-pcxhr                snd-soc-l3               snd-tea6330t
snd-au8810               snd-fm801                snd-intel8x0m            snd-pdaudiocf            snd-soc-max9877          snd-timer
snd-au8820               snd-gina20               snd-interwave            snd-portman2x4           snd-soc-pcm3008          snd-trident
snd-au8830               snd-gina24               snd-interwave-stb                      snd-pt2258               snd-soc-spdif            snd-usb-audio
snd-aw2                  snd-gusclassic           snd-korg1212             snd-rawmidi              snd-soc-ssm2602          snd-usb-caiaq
snd-azt2320              snd-gusextreme           snd-layla20              snd-riptide              snd-soc-tlv320aic23      snd-usb-lib
snd-azt3328              snd-gus-lib              snd-layla24              snd-rme32                snd-soc-tlv320aic26      snd-usb-us122l
snd-bt87x                snd-gusmax               snd-lx6464es             snd-rme96                snd-soc-tlv320aic3x      snd-usb-usx2y
snd-ca0106               snd-hda-codec            snd-maestro3             snd-rme9652              snd-soc-twl4030          snd-util-mem
snd-cmi8330              snd-hda-codec-analog     snd-mia                  snd-sb16                 snd-soc-uda134x          snd-via82xx
snd-cmipci               snd-hda-codec-atihdmi    snd-miro                 snd-sb16-csp             snd-soc-uda1380          snd-via82xx-modem
snd-cs4231               snd-hda-codec-ca0110     snd-mixart               snd-sb16-dsp             snd-soc-wm8350           snd-virmidi
snd-cs4236               snd-hda-codec-cirrus     snd-mixer-oss            snd-sb8                  snd-soc-wm8400           snd-virtuoso
snd-cs4281               snd-hda-codec-cmedia     snd-mona                 snd-sb8-dsp              snd-soc-wm8510           snd-vx222
snd-cs46xx               snd-hda-codec-conexant   snd-mpu401               snd-sbawe                snd-soc-wm8523           snd-vx-lib
snd-cs5530               snd-hda-codec-idt        snd-mpu401-uart          snd-sb-common            snd-soc-wm8580           snd-vxpocket
snd-cs5535audio          snd-hda-codec-intelhdmi  snd-msnd-classic                  snd-sc6000               snd-soc-wm8728           snd-wavefront
snd-cs8427               snd-hda-codec-nvhdmi     snd-msnd-lib             snd-seq                  snd-soc-wm8731           snd-wss-lib
snd-ctxfi                snd-hda-codec-realtek    snd-msnd-pinnacle                 snd-seq-device           snd-soc-wm8750           snd-ymfpci
snd-darla20              snd-hda-codec-si3054     snd-mtpav                snd-seq-dummy            snd-soc-wm8753           
snd-darla24              snd-hda-codec-via        snd-mts64                snd-seq-midi             snd-soc-wm8776           
snd-dt019x               snd-hda-intel            snd-nm256                snd-seq-midi-emul        snd-soc-wm8900           
snd-dummy                snd-hdsp                 snd-opl3-lib             snd-seq-midi-event       snd-soc-wm8903

```

Any help with this would be great!
Thanks

---

### Post by jazzgossen on 2010-06-09
No much help perhaps, but try looking at the System/Settings/Sound under the Hardware tab, and see if there's anything strange there.

---

### Post by SilentPirate007 on 2010-06-09
> **jazzgossen said:**
> No much help perhaps, but try looking at the System/Settings/Sound under the Hardware tab, and see if there's anything strange there.

There is no information in the hardware tab...

---

### Post by lidex on 2010-06-09
Try this. ```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

### Post by jazzgossen on 2010-06-13
I just realized that a similar thing happened to me after a recent update. My sound card was still listed in the sound preferences, but I could just not get any audio output. 

Deleting the ~/.pulse directory (actually, moving it to ~/.pulse.bak) and restarting pulseaudio (killall pulseaudio), got my sound back.

---

