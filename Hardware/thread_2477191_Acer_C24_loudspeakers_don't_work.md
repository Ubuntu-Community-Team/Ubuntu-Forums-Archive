---
title: "Acer C24 loudspeakers don't work"
date: 2022-07-17
forum: Hardware
---

### Post by giuseppevenditti on 2022-07-17
Hi all,
I bought an Acer C24, installed Ubuntu 22.04; the system recognise the audio card

```
giuseppe@Aspire-C24-1650:~$ lspci -nnk | grep -i audio -A2 && aplay -l
00:1f.3 Multimedia audio controller [0401]: Intel Corporation Tiger  Lake-LP Smart Sound Technology Audio Controller [8086:a0c8] (rev 20)
    Subsystem: Acer Incorporated [ALI] Tiger Lake-LP Smart Sound Technology Audio Controller [1025:1475]
    Kernel driver in use: sof-audio-pci-intel-tgl
    Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl
00:1f.4 SMBus [0c05]: Intel Corporation Tiger Lake-LP SMBus Controller [8086:a0a3] (rev 20) 
``` 

but the internal microphone and loudspeakers don't work; external bluetooth loudspeakers instead work perfectly; I saw this

[https://askubuntu.com/questions/1243369/sound-card-not-detected-ubuntu-20-04-sof-audio-pci](https://askubuntu.com/questions/1243369/sound-card-not-detected-ubuntu-20-04-sof-audio-pci)

but my system recognises the card, there the card where not recognised. Note that the hardware is OK, it works with Windows.

Any idea?

Many thanks

---

### Post by #&amp;thj^% on 2022-07-17
You possibly misunderstood that link,** the card *was* found,** they just switched the driver from "sof-audio-pci" to "snd_hda_intel"  via grub.
So you appear to be using both "snd_hda_intel, && snd_sof_pci_intel_tgl"
You''l have to decide if the internal mic is really a necessity at this time.
Please clarify your  loudspeakers how are they connected?

---

### Post by giuseppevenditti on 2022-07-17
Thanks 1fallen, now I begin to understand something; 
when I connect external loudspeakers with bluetooth, they work; but internal loudspeakers and microphone don't work; note that with alsa I see the leads moving bot for mic than loudspeakers; 
it should be fine if all internal mic and loudspeaker work;
what I can try?
many thanks

---

### Post by #&amp;thj^% on 2022-07-17
Well to start with I need to repeat this>> your internal mic possibly will not work with my suggestions.
That said, use this to make the parameter load:
```
sudo nano /etc/default/grub
```
Add this to "GRUB_CMDLINE_LINUX_DEFAULT=" like this:
```
snd_intel_dspcfg.dsp_driver=1
```
so it should look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash snd_hda_intel.dmic_detect=1"
```
I'm trying this to see if we can get the internal mic to work as well
save and exit.
Now we have to tell grub of the new change, so run this:
```
sudo update-grub
```
Now reboot, any better now?

---

### Post by giuseppevenditti on 2022-07-17
these are some lines in grub
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash snd_hda_intel.dmic_detect=1"
GRUB_CMDLINE_LINUX=""
```

no difference in internal loudspeakers and mic; however, the mic works with an usb external mic, doesn'ìt work with earphone, and still external bluetooth loudspeakers work; 
so, the matter to make video conferences is solved, but should be fine working with embedded stuff;
in any case, many thanks

---

