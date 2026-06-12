---
title: "No sound on Xubuntu Core"
date: 2015-09-25
forum: Hardware
---

### Post by Gustavo_Mota on 2015-09-25
First of all I'm new to linux, i have installed a Xubuntu Core "Vivid Vervet" 15.04 Release ISO in an old notebook of mine (from somewhere 2005-2007), and the problem is i have no sound, the volume icon is there but in the options it can't find hardware output devices. I've gone through the sound troubleshooting procedure and to my little knowledge, seems that xubuntu can recognize the soundcard. I don't know really what to do, if this is a bad soundcard problem or there is a way to make it work, so i came here to ask some more experienced users if they know how to help with this. I've attached the terminal output and one screenshot.

[ATTACH=CONFIG]264646[/ATTACH]

```
gustavoms@Mota-X51RL:~$ pacmdWelcome to PulseAudio 6.0! Use "help" for usage information.
>>> list-sinks
1 sink(s) available.
  * index: 0
    name: <auto_null>
    driver: <module-null-sink.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 1000
    volume: front-left: 65536 / 100% / 0,00 dB,   front-right: 65536 / 100% / 0,00 dB
            balance 0,00
    base volume: 65536 / 100% / 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max request: 344 KiB
    max rewind: 344 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 2000,00 ms
    module: 11
    properties:
        device.description = "Dummy Output"
        device.class = "abstract"
        device.icon_name = "audio-card"
>>> exit
gustavoms@Mota-X51RL:~$ aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
gustavoms@Mota-X51RL:~$ sudo aplay -l
[sudo] password for gustavoms: 
**** List of PLAYBACK Hardware Devices ****
Home directory not accessible: Permission denied
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
gustavoms@Mota-X51RL:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/3.19.0-15-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/3.19.0-15-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/3.19.0-15-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/3.19.0-15-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/3.19.0-15-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.19.0-15-generic/kernel/sound/usb/hiface/snd-usb-hiface.ko
/lib/modules/3.19.0-15-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/3.19.0-15-generic/kernel/sound/usb/bcd2000/snd-bcd2000.ko
/lib/modules/3.19.0-15-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/3.19.0-15-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/3.19.0-15-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/3.19.0-15-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/3.19.0-15-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/3.19.0-15-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/3.19.0-15-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/3.19.0-15-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/3.19.0-15-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/3.19.0-15-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/snd-compress.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/snd-pcm-dmaengine.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/snd.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.19.0-15-generic/kernel/sound/core/snd-timer.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-controller.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/hda/snd-hda-codec-generic.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/galaxy/snd-azt1605.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/galaxy/snd-azt2316.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/sb/snd-jazz16.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/msnd
/lib/modules/3.19.0-15-generic/kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/msnd/snd-msnd-classic.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/msnd/snd-msnd-lib.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/snd-cmi8328.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/3.19.0-15-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/3.19.0-15-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/3.19.0-15-generic/kernel/sound/firewire/bebob/snd-bebob.ko
/lib/modules/3.19.0-15-generic/kernel/sound/firewire/oxfw/snd-oxfw.ko
/lib/modules/3.19.0-15-generic/kernel/sound/firewire/snd-scs1x.ko
/lib/modules/3.19.0-15-generic/kernel/sound/firewire/fireworks/snd-fireworks.ko
/lib/modules/3.19.0-15-generic/kernel/sound/firewire/dice/snd-dice.ko
/lib/modules/3.19.0-15-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/3.19.0-15-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.19.0-15-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8962.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-hdmi-codec.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8741.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-ak4554.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-tas5086.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-ssm2602-i2c.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23-spi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-tfa9879.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-pcm1792a-codec.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-cs4271.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-ssm2602-spi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-cs42l52.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-pcm1681.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-si476x.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-cs4271-i2c.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-sigmadsp-i2c.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-ssm4567.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-ts3a227e.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-rt286.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-sn95031.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-adau1701.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-cs35l32.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-pcm512x.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-sta350.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-alc5623.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-spdif-rx.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-sigmadsp.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-max98090.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-spdif-tx.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23-i2c.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-cs42l51.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-es8328.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-pcm512x-spi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-cs4271-spi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-ak5386.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-cs42xx8.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8770.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic31xx.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-tas2552.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8737.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-cs42l51-i2c.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-cs42xx8-i2c.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-rt5670.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-sgtl5000.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-cs4265.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-rl6231.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8804.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-rt5631.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-cs42l73.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-pcm512x-i2c.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-rt5640.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/codecs/snd-soc-cs42l56.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/snd-soc-sst-baytrail-pcm.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/snd-soc-sst-byt-max98090-mach.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/snd-soc-sst-broadwell.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/snd-soc-mfld-machine.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/snd-soc-sst-byt-rt5640-mach.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/snd-soc-sst-acpi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/snd-soc-sst-bytcr-dpcm-rt5640.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/snd-soc-sst-haswell.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/snd-soc-sst-cht-bsw-rt5672.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/snd-soc-sst-dsp.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/snd-soc-sst-haswell-pcm.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/sst/snd-intel-sst-acpi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/sst/snd-intel-sst-core.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/sst/snd-intel-sst-pci.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/intel/snd-soc-sst-mfld-platform.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/generic/snd-soc-simple-card.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/atmel/snd-soc-atmel-pcm.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/fsl/snd-soc-fsl-asrc.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/fsl/snd-soc-fsl-spdif.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/fsl/snd-soc-imx-audmux.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/fsl/snd-soc-fsl-esai.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/fsl/snd-soc-fsl-sai.ko
/lib/modules/3.19.0-15-generic/kernel/sound/soc/fsl/snd-soc-fsl-ssi.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/3.19.0-15-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
gustavoms@Mota-X51RL:~$ lspci -v | grep -A7 -i "audio"
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 1339
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at febf4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel


00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB600 PCI to LPC Bridge
gustavoms@Mota-X51RL:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC410 Host Bridge (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 1
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 2
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 3
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 4
00:12.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB600 IDE
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RC410M [Mobility Radeon Xpress 200M]
02:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
08:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
08:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
08:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
08:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
gustavoms@Mota-X51RL:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfebf4000 irq 16
gustavoms@Mota-X51RL:~$ 


 
```

---

### Post by Yellow Pasque on 2015-09-25
Did this installation ever have sound?
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Gustavo_Mota on 2015-09-25
No, never had. I installed xubuntu two times just to test if it was some installation problem. There is the alsainfo link:
[http://www.alsa-project.org/db/?f=652743e1d6c3449c06cb3c7a81bbe30881b6dc68](http://www.alsa-project.org/db/?f=652743e1d6c3449c06cb3c7a81bbe30881b6dc68)

---

### Post by Yellow Pasque on 2015-09-25
Make sure it's enabled in BIOS (if BIOS has such an option). Also, you may need to disable the modem sound module: [http://ubuntuforums.org/showthread.php?t=1352620](http://ubuntuforums.org/showthread.php?t=1352620)
Or maybe blacklist its module if possible:
```
echo "blacklist snd-hda-codec-si3054" | sudo tee /etc/modprobe.d/blacklistsi3054.conf
```

---

### Post by Gustavo_Mota on 2015-09-26
Used your command to blacklist the modem sound module, also checked in bios and audio is unlocked, also put speaker volume to maximum in bios and sadly there is still no sound. Is there something more that i can try?

Does this image have something to do with it?

[IMG]http://i.imgur.com/67lD8J1.png[/IMG]

---

### Post by Yellow Pasque on 2015-09-27
> **arminmohring said:**
> Can you test the sound with another source?

That's not going to do anything. The codec is not even showing in aplay (only the modem soud device is). If you're familiar with Windows, think of it as Device Manager not even recognizing/listing the device.

The only thing I would think of to try at this point is:
1) Latest sound module: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
2) Resetting BIOS. Apparently, Asus laptops can be reset by removing AC power and battery, and then holding power button for at least 30 seconds.

---

