---
title: "Getting a Creative Soundblaster Live! 24 bit to work"
date: 2005-12-03
forum: General Help
---

### Post by panocrat on 2005-12-03
Greetings all, I know that the SB Live! 24 is problematic with Ubuntu, and have been trying to get the drivers installed. I've downloaded the latest files from ALSA, but then had a problem cos GCC wasn't installed. I managed to get that working OK, but can't get GCC to actually work now as it's not recorded in the path. I've been trying to find out how to add GCC to the path, but without a lot of success...I'm another newbie. I've read that I need to edit either the .bash_profile or .bashrc, and am now looking at bash.bashsrc in /etc...if I add something like PATH=$PATH:$usr/lib/GCC to this, will Ubuntu then permanently recognise GCC and its commands?

---

### Post by mo_x on 2005-12-03
Install the package build-essential from synaptic. To compile a kernel module you also need to install the linux-headers package.

---

### Post by panocrat on 2005-12-03
m_ox, thanks for the quick reply. i've tried what you suggested and made some progress, but am now being told i have no curses library when i try to run ./configure;make;make install  (following instructions from the ALSA site)

checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

so i went to synaptic and it tells me i have libncurses5 installed. any suggestions as to what i haven't done/am doing wrong? instructions i'm following are located at 

[www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106](www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106)

---

### Post by steve.horsley on 2005-12-03
I have an SB live 24 and it worked perfectly after install except for the fact that ubuntu defaulted to using the on-motherboard sound chip instead. Go to System->Preferences->Sound and make sure the blaster is selected as the default sound device. You may also need do select the blaster in the volume control preferences. I don't think you should need to compile drivers for yourself.

---

### Post by mo_x on 2005-12-03
If you are compiling something you usualy need the -dev package, in this case libncurses5-dev.
If you are trying to compile the snd-ca0106 module I think it is already provided in Ubuntu, just try:
```
sudo modprobe snd-ca0106
```

---

### Post by panocrat on 2005-12-03
still getting nowhere. following the instructions from the ALSA site, the install of the alsa-driver seems to be succesful, but then when i chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi, i get the error message that neither /dev/sequencer nor /dev/midi directories exist.

then when i come to install the alsa-lib, all seems fine.

installing alsa-utils, there are some errors at the end:

make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.8/alsaconf'
Making install in po
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.8/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.8/alsaconf/po'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.8/alsaconf'
make: *** [install-recursive] Error 1

unsurprising, inserting the modules into the kernel goes pear-shaped:

modprobe snd-ca0106;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.12-10-386/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.12-10-386/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_seq (/lib/modules/2.6.12-10-386/kernel/sound/acore/seq/snd-seq.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_seq
WARNING: Error inserting snd_seq_midi_event (/lib/modules/2.6.12-10-386/kernel/sound/acore/seq/snd-seq-midi-event.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.12-10-386/kernel/sound/acore/seq/oss/snd-seq-oss.ko): Unknown symbol in module, or unknown parameter (see dmesg)

i was having problems with GCC before too, some comments about unrecognised GCC commands, so i installed an older version of GCC and that seemed to cure those problems...i now have GCC 3.4 and 4.0 installed. other relevant point is that in preferences/sounds, CA0106 is the only sound card detected.

---

### Post by panocrat on 2005-12-03
just saw this [http://ubuntuforums.org/showthread.php?t=9896](http://ubuntuforums.org/showthread.php?t=9896) thread which doesn't bode too well for me getting this card working. lots of other people seem to have had a problem with the card.

got it working now, despite all the error messages above. muting the SPDIF was the key.

---

