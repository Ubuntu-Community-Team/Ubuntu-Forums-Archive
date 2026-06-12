---
title: "Help with HL-340 Serial to USB Adapter"
date: 2008-10-03
forum: Hardware
---

### Post by BCHurricane89 on 2008-10-03
Hello, i bought a serial to usb adapter, and on it says: HL-340. So I searched for that, and linux, and came across this site: [http://tiagovaz.wordpress.com/2008/01/04/using-a-hl-340-usb-serial-adapter-against-2623-linux-kernel/](http://tiagovaz.wordpress.com/2008/01/04/using-a-hl-340-usb-serial-adapter-against-2623-linux-kernel/)

Well, I followed the instructions, and deleted the lines in files it suggested, and ran the inst.sh

My device is still not working, or at least I don't think it mounted. Under the terminal, I typed lsusb, and found the adapter: 

Bus 001 Device 004: ID 1a86:7523 

I am using this adapter to connect a digital temperature sensor I made here: [http://www.instructables.com/id/Temperature-sensor--weatherstation/](http://www.instructables.com/id/Temperature-sensor--weatherstation/)

and I already have digitemp installed, but it doesn't seem to be able to find it. Any help would be appreciated.

---

### Post by BCHurricane89 on 2008-10-04
I have also found out, that it is not mounting, and or creating the ttyUSB0. I dont know if the drivers are not built into the kernel, or what. Any help would be appreciated.

---

### Post by kaligus on 2010-01-11
At least in my case the kernel seems to know something of the adapter as from lsmod I get:

```

bigwill:[20100111.2015]root@/etc/modprobe.d :: lsmod |grep "usb"
usbserial              36264  1 ch341
snd_usb_audio          84320  0
snd_usb_lib            16316  1 snd_usb_audio
snd_pcm                75520  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_usb_audio
snd_hwdep               7200  2 snd_hda_codec,snd_usb_audio
snd_rawmidi            22208  2 snd_usb_lib,snd_seq_midi
snd                    59204  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_usb_audio,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 38304  0
usb_storage            52640  1
bigwill:[20100111.2015]root@/etc/modprobe.d ::

```

The first one is the module listed on that webpage, and for giggles and grins I did also add the pl2303 to the blacklist as stated there.

I have not tried the compiled driver module as that seems broken to compile something that seems to be fine at the kernel level (the module is there and this is the only usb-serial adapter I have ever plugged in to my knowledge)

---

