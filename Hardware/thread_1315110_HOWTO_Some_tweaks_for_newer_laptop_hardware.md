---
title: "HOWTO: Some tweaks for newer laptop hardware"
date: 2009-11-05
forum: Hardware
---

### Post by darkshadow on 2009-11-05
I just purchased a new "Acer Aspire 8940G-6683" which is a new laptop released Oct 30 and I wanted to share some tweaks I have used to make the laptop work better. Even if you don't have this exact laptop they may still help since all this info was found by researching recent similar laptops. Due to the fact company's use a lot of the same hardware.



Video: Installed proprietary drivers version 190.42 which are to new to be in the repositories but needed to support the "Geforce GTS 250M"

	Don't use the ones from nvidia.com since I tried and they worked for most stuff but not everything I got the best results by adding "ppa:thefirstm/ppa" to the software sources and installing them since they are bundled for Karmic specifically and I added myself to the "video" group which let me boot more 3d games.

	url for more info on the ppa: [https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)




Card Reader: I had to add "pciehp.pciehp_force=1" to the end of the line loading the kernel in the Grub config file. This allows the card reader to work anytime instead of only when the laptop was booted with a card in it. I have a feeling this is needed for firewire to but I have not got around to testing it yet. I am assuming it is needed for fire wire since it does not show up in lspci unless the card reader is working.




Sound card: I added "options snd-hda-intel model=acer-aspire-8930g" to /etc/modprobe.d/options to enable surround sound output and the built in microphone. You also have to change the hardware tab in "sound preferences"

For more model's you can use for other laptops run the following command in a terminal since alsa using a few basic defaults if it can't figure out exactly what you have.
zcat /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz |less

***Note I just realized that the ppa in used for the video drivers also upgraded my Alsa version to the newest when I ran update-manager and the model I used is new to said Alsa version.




Keyboard: I set the keyboard layout to "acer laptop" and it enabled the multimedia keys to work. (play, pause, track forward/back)
This is another case of most people leave it on generic 105 without knowing then just assume extra media keys don't work.

I will post more as I keep working through the hardware trying to make it all work. My next project is hdmi audio, hopefully I can get it to work.

---

