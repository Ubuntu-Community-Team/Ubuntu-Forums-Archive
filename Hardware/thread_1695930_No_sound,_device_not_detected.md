---
title: "No sound, device not detected"
date: 2011-02-26
forum: Hardware
---

### Post by Robert1995 on 2011-02-26
I lost sound after restarting, I had sound, then on my reboot... No sound. I tried to google the problem and ran the common tasks of removing and re-installing "alsa-base" and "pulseaudio" using apt-get in terminal. But after trying all this I have now lost the volume control at the top right of my screen :(

I have no idea what the issue is, in System > Preferences > Sound I get nothing under Hardware, nothing under Input, "Dummy Output" under Output, and nothing special under Applications.

Here is the results of commands in terminal which I have commonly see people been asked to do:

```
sudo aplay -l

aplay: device_list:235: no soundcards found...

```

```
sudo find /lib/modules/`uname -r` | grep snd

/lib/modules/2.6.35-22-generic/updates/dkms/snd-hda-codec-idt.ko
/lib/modules/2.6.35-22-generic/updates/dkms/snd-hda-codec.ko
/lib/modules/2.6.35-22-generic/updates/dkms/snd-hda-codec-cmedia.ko
/lib/modules/2.6.35-22-generic/updates/dkms/snd-hda-codec-analog.ko
/lib/modules/2.6.35-22-generic/updates/dkms/snd-hda-codec-si3054.ko
/lib/modules/2.6.35-22-generic/updates/dkms/snd-hda-codec-hdmi.ko
/lib/modules/2.6.35-22-generic/updates/dkms/snd-hda-codec-via.ko
/lib/modules/2.6.35-22-generic/updates/dkms/snd-hda-codec-ca0110.ko
/lib/modules/2.6.35-22-generic/updates/dkms/snd-hda-intel.ko
/lib/modules/2.6.35-22-generic/updates/dkms/snd-hda-codec-realtek.ko
/lib/modules/2.6.35-22-generic/updates/dkms/snd-hda-codec-cirrus.ko
/lib/modules/2.6.35-22-generic/updates/dkms/snd-hda-codec-conexant.ko
/lib/modules/2.6.35-22-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.35-22-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.35-22-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.35-22-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.35-22-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.35-22-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.35-22-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.35-22-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/2.6.35-22-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.35-22-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.35-22-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-da7210.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-tlv320dac33.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8993.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ak4671.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ad1836.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8994.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ads117x.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm9090.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-max9877.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8904.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8961.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-spdif.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm2000.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8727.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8955.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-twl4030.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-ad193x.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-twl6040.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8974.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.35-22-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.35-22-generic/kernel/sound/pci/vx222/snd-vx222.ko
```

```
alsamixer

cannot open mixer: No such file or directory
```

```
lspci -v | less

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: Packard Bell B.V. Device a88d
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] MSI: Enable- Count=1/1 Maskable+ 64bit+
        Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
```

Also I get this strange batch of Warnings when I do the following:
```
sudo alsa force-reload

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/robert1995/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse file system /home/robert1995/ZumoDrive
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/robert1995/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse file system /home/robert1995/ZumoDrive
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-allocWARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
.
```


The only thing I think that could of triggered everything to mess up is some mods I made to to the alsa-base.conf file - What I did to it I can't remember, But I have tried to remove these two lines of code at the end of it, saved it, restarted my computer and still no audio.

Help Please :(
Oh, I am using Ubuntu 10.10 (Maverick) 64Bit
Kernel Linux 2.6.35-22-Generic
GNOME 2.32.0

---

### Post by lkjoel on 2011-02-26
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.
It should solve your problem.

---

### Post by Robert1995 on 2011-02-26
Sound is working after much toying with the CPanel tool... The sound is horrible and doesn't go up to loud, too confusing etc etc.
This is not solved.

However I would prefer to be kept on ALSA, I turned everything up in the "ossxmixer" and the sound is stupidly quiet. and the interface to adjust volume is too confusing.

Is there anyway I could remove OSS and go back to ALSA? I did not make any hardware changes or updates that caused ALSA to suddenly become incompatible... It worked just wasn't configured correctly.

Is there anyway I could somehow rollback to ALSA defaults without a fresh install of Ubuntu ?
My final solution would be freshly install Ubuntu as not having continuing to use my failure and default audio setup is a priority.

Thanks :)

---

### Post by lkjoel on 2011-02-26
> **Robert1995 said:**
> Sound is working after much toying with the CPanel tool... The sound is horrible and doesn't go up to loud, too confusing etc etc.
This is not solved.

However I would prefer to be kept on ALSA, I turned everything up in the "ossxmixer" and the sound is stupidly quiet. and the interface to adjust volume is too confusing.

Is there anyway I could remove OSS and go back to ALSA? I did not make any hardware changes or updates that caused ALSA to suddenly become incompatible... It worked just wasn't configured correctly.

Is there anyway I could somehow rollback to ALSA defaults without a fresh install of Ubuntu ?
My final solution would be freshly install Ubuntu as not having continuing to use my failure and default audio setup is a priority.

Thanks :)
Yes.
[http://ubuntuforums.org/showpost.php?p=5539687&postcount=331]("http://ubuntuforums.org/showpost.php?p=5539687&postcount=331")

---

### Post by Robert1995 on 2011-02-27
Screw it lol, I will just reinstall Ubuntu, and never touch the configuration of audio again :L

:popcorn: Now to enjoy the Ubuntu Installation menu's that bore me to tears.

---

### Post by lkjoel on 2011-02-27
> **Robert1995 said:**
> Screw it lol, I will just reinstall Ubuntu, and never touch the configuration of audio again :L

:popcorn: Now to enjoy the Ubuntu Installation menu's that bore me to tears.

Lol!

---

### Post by muckblit on 2011-07-22
I websearched to explanation of which alsa files to use to look up my card identifier and then put that in /etc/modules some file. Then every so often I have to manually sudo alsa force-reload. That ain't right.

---

### Post by muckblit on 2011-07-22
What i did to ruin audio after fresh ub natty install was to search in synaptic and install 'codec' and 'audio' and 'video' stuff.

---

