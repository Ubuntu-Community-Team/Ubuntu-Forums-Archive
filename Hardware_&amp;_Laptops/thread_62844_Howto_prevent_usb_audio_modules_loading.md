---
title: "Howto prevent usb audio modules loading?"
date: 2005-09-06
forum: Hardware &amp; Laptops
---

### Post by cd-r80 on 2005-09-06
snd_ens1371            22624  1
snd_ac97_codec         64608  1 snd_ens1371
gameport                4608  1 snd_ens1371
snd_usb_audio          60224  1
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_ens1371,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  1 snd_pcm
snd_usb_lib            11776  1 snd_usb_audio
snd_rawmidi            22944  2 snd_ens1371,snd_usb_lib
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  11 snd_ens1371,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device
soundcore               9824  2 snd
usbcore               107384  5 snd_usb_audio,snd_usb_lib,uhci_hcd,quickcam

I got other program BLOCKING soundcard problem. This started after installing web cam which works. How to prevent usb sound loading...if that helps?

---

### Post by swamytk on 2005-09-06
In /etc/hotplug directory there is a file called blacklist. Here you list your usb sound module to prevent it from loading.

---

### Post by sept00 on 2005-12-23
You could also try editing your /etc/asound.conf to reflect the order of the sound cards. Open a terminal and run "sudo cat /proc/asound/cards" and take a look at the output. Mine's like this:

```
0 [U0x46d0x8b0    ]: USB-Audio - USB Device 0x46d:0x8b0
                     USB Device 0x46d:0x8b0 at usb-0000:00:10.3-2.1, full speed
1 [V8235          ]: VIA8233 - VIA 8235
                     VIA 8235 with ALC650F at 0xe000, irq 22
```

I have a webcam as the device "0", so I edited the /etc/asound.conf to primarily talk to device "1", which is actually my on-board sound chip. This is from [http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753):

```
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 1
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}
```

The most important part is the "card 1" in line 5, enter the number of the card you want to use.

*<edit>* I haven't tried unplugging the webcam, but I could imagine running into problems with the setting once it's unplugged because the on-board sound will move up to "0". YMMV.*</edit>*

And take a look at these very helpful posts:

[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)
[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)

---

