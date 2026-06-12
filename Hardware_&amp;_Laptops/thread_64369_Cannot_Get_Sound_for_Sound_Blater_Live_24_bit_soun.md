---
title: "Cannot Get Sound for Sound Blater Live 24 bit sound card"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by Third Thoughts on 2005-09-10
I just recently purchased a Sound Blaster Live 24 bit card for my system. I saw in the Unbuntu wiki that this sound card was supported if I downloaded and installed the latest alsa drivers. (Here's the wiki page [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards?highlight=%28card%29%7C%28Sound%29](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards?highlight=%28card%29%7C%28Sound%29))
I followed the link on the wiki page and downloaded the tar package. I followed the install instructions and ran the following commands in the folder I untarred to:
$ ./configure --with-cards=ca0106 --with-sequencer=yes
$ make
$ sudo make install
$ ./snddevices
Every thing went well up until here. Then I tried 
$ sudo modprobe snd-ca0106
Here's the output:
```
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.10-5-386/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.10-5-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.10-5-386/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.10-5-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ca0106 (/lib/modules/2.6.10-5-386/kernel/sound/pci/ca0106/snd-ca0106.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_ca0106
``` 

I've tried messing around with the --with-kernel and --with-build options at the ./configure step, specifying different directories etc., but it either doesn't work at all (breaking before make install) or gives me the same eventual problem. Anyone got any suggestions? Thanks for any help you can offer.

~Andrew S.

---

### Post by Third Thoughts on 2005-09-10
Nevermind. All it took was a simple reboot. Sorry to waste your time folks  :) 
~Andrew S.

---

