---
title: "After hibernation no sound but hardware detected correctly"
date: 2011-11-09
forum: Hardware
---

### Post by rbaleksandar on 2011-11-09
Hi, guys!

  I had a bad surprise a couple of minutes ago, when I started my laptop and discovered there was no sound coming from neither speakers or the headphones. All I did was hibernate my Ubuntu 10.04 this morning after reading a couple of news feeds, while having a breakfast. Haven't manually installed any new software (especially drivers' updates) in for more than a week and today it was still working before the hibernation. It's been a couple of days since the last updates came through the Update Manager and even so it makes no sense that the system worked (running AND hibernating without any glitches (at least none that I've noticed :P)) a couple of days after the updates and suddenly stopped functioning properly.

  I did look at the sound troubleshooting (not the first time because of 1)lovely T@shiba and 2)lovely S@ny. Here are the results:

[LIST=1]
[*]Is your volume turned all the way down, or is your speaker muted?
  Most certainly not.
[*]Can you play a sound that is known to always play correctly?
  No.
[*]Can another user play one of these "known-good" sounds?
  No.
[*]s the system recognizing your sound card?
  Yes.
```

card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
[*]Do you have the sound modules installed?
  Yes.
```

 find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8974.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-twl4030.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-max9877.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-ad1938.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8993.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-spdif.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-ad1836.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8961.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/snd-hrtimer.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/snd.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/oss/msnd.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/msnd
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/msnd/snd-msnd-classic.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/msnd/snd-msnd-lib.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.32-35-generic-pae/kernel/sound/usb/snd-usb-lib.ko

```

[*]Is the sound card physically installed and recognized by your hardware?
  Yes.

```

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f5e00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

[*]Is my sound card supported by the Ubuntu sound system?
  Yes. It was working this morning before hibernation!

[*]Manually starting the audio driver
```
sudo modprobe snd-hda-intel

```
  Didn't work.
[/LIST]

 I'll edit the **/etc/modules** by adding **snd-hda-intel** to this empty file (there is only one comment there describing what the file contains and a loop (lp)), but still I'm really surprised to what happened. Did 2-3 restarts, changed to a Guest-session (played a couple of WAVs there) but still no positive results. :confused: Later on I'll reinstall the sound modules etc.


I'll really appreciate it, if someone can perhaps tell me why this happened (not interested only in the solution, because this might happen again and understanding why it does will help me A LOT),
rba



EDIT:
I did
```

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
but still no sound. :(:(:(
  Forgot to mention that under Windows 7 sound is fine. So this excludes a faulty hardware.
  One more thing - I have been using ALSA from here:
[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu)
Because after a fresh install of Ubuntu a month ago my Vaio doesn't play any sounds. My current version of ALSA is
```

linux-alsa-driver-modules-2.6.32-34-generic-pae

```

---

### Post by rbaleksandar on 2011-11-09
I read a couple of threads, where people were asked to look up in the System monitor for the **pulseaudio**-process. Well, I have it. And it's priority (Niceness) is set to the incredible -11. I supposed the sound has to have such a hight priority (or I'm wrong?). Still, killing it did nothing but to put it back in the process tree with the same priority.

Still hoping for some help on this one...


EDIT: Ok, I just remembered that yesterday the new kernel update came and I installed it: 2.6.32-35
Now I switched to 2.6.32-34 and - yahoo! - there is sound. But the question about the problem still remains because this might be occur in the kernel's versions after 2.6.32-35.

---

