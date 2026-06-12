---
title: "HOWTO: Headphone output on Samsung M50"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by cronholio on 2007-02-24
I have been trying to enable the headphone output of my Samsung M50 (Callum) laptop for ages and now it finally works. This may also help other laptop users with the same soundcard. If you are plagued by this problem, here's what to do:

1. Download the newest sources of the ALSA drivers from [here.]("http://www.alsa-project.org/") Make sure it compiles with your kernel. Newer kernels lack config.h so 1.0.13 will not compile. I am on Feisty so I used one from [here.]("ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/")

2. Install build essentials and kernel headers: ```
sudo aptitude install build-essential linux-headers-`uname -r`
```

3. Unzip the ALSA driver sources and enter the resulting directory. Edit alsa-kernel/pci/hda/patch_analog.c and search for *static struct snd_kcontrol_new ad1986a_laptop_mixers[]*. The headphone sliders have been commented out for whatever reason, so change this. It should look like this: ```
static struct snd_kcontrol_new ad1986a_laptop_mixers[] = {
        HDA_CODEC_VOLUME("PCM Playback Volume", 0x03, 0x0, HDA_OUTPUT),
        HDA_CODEC_MUTE("PCM Playback Switch", 0x03, 0x0, HDA_OUTPUT),
        HDA_CODEC_VOLUME("Master Playback Volume", 0x1b, 0x0, HDA_OUTPUT),
        HDA_CODEC_MUTE("Master Playback Switch", 0x1b, 0x0, HDA_OUTPUT),
        HDA_CODEC_VOLUME("Headphone Playback Volume", 0x1a, 0x0, HDA_OUTPUT),
        HDA_CODEC_MUTE("Headphone Playback Switch", 0x1a, 0x0, HDA_OUTPUT),
        HDA_CODEC_VOLUME("CD Playback Volume", 0x15, 0x0, HDA_OUTPUT),
        HDA_CODEC_MUTE("CD Playback Switch", 0x15, 0x0, HDA_OUTPUT),

``` ...and so on.

Install the drivers like this: ```
./configure --with-cards=hda-intel --with-build=/usr/src/linux-headers-`uname -r`
make
make install
```
If it complains about config.h during make, see step 1.

4. Edit /etc/modprobe.d/alsa-base (as root) and add at the bottom of the file:
```
options snd-hda-intel model=laptop
```
It is reported elsewhere that the Samsung M50 needs model=laptop-eapd which is NOT true (as far as I know), so remove this if you ever added it before.

Reboot and enjoy your shiny new headphone slider in the mixer app. Enable it if it isn't already and it should work. :)

I'll report this to the ALSA project, so hopefully it will be taken care of in a new release.

---

### Post by coln_panic on 2007-03-15
just wanted to say thanks!  i have an asus a8jp laptop with intel/realtek audio running feisty - following your steps exactly (using the most recent from the suse alsa snapshot: alsa-driver-hg20070314) made it work!

now if i could just get the volume buttons to change the PCM channel instead of Master i'd be completely happy with sound on my laptop.... although that seems like a common problem with no simple solution.

jay

---

