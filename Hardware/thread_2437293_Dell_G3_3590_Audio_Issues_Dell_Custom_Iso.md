---
title: "Dell G3 3590 Audio Issues Dell Custom Iso"
date: 2020-02-21
forum: Hardware
---

### Post by tiagodfer on 2020-02-21
Hello,
I have a Dell G3 3590 with Ubuntu pre-installed. I noticed that it has some custom settings made specially for this model, is there any way to check what exactly are those changes? One that catches my attention is "oem-fix-audio-intel-dmic", I can't find anything about it online, and this change makes my notebook audio works flawlessly, fixing two annoying issues: 
- correctly identify the internal laptop microphone, without this fix, it isn't detected;
- without this fix, when I plug in a headphone in the headphone jack (it's a duplex jack), I have to manually switch to duplex analog audio in pavucontrol, otherwise, no sound comes through the headphones.

I want to understand this changes so I'm able to replicate this fix when installing another Ubuntu based distro.
I've tried, with no success the inserting "options snd-hda-intel model=dell-headset-multi" into /etc/modprobe.d/alsa-base.conf, and options snd_hda_intel dmic_detect=0 into /etc/modprobe.d/hda_fix.conf.

Using Synaptic I found the files that this package uses the following files:
```

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/oem-fix-audio-intel-dmic
/usr/share/doc/oem-fix-audio-intel-dmic/changelog.gz
/usr/share/doc/oem-fix-audio-intel-dmic/copyright
/usr/share/oem-fix-audio-intel-dmic
/usr/share/oem-fix-audio-intel-dmic/HiFi
/usr/share/oem-fix-audio-intel-dmic/blacklist-intel-hdaudio.conf
/usr/share/oem-fix-audio-intel-dmic/firmware
/usr/share/oem-fix-audio-intel-dmic/firmware/LICENCE.sof
/usr/share/oem-fix-audio-intel-dmic/firmware/WHENCE
/usr/share/oem-fix-audio-intel-dmic/firmware/intel
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/apl
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/apl/intel
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/apl/intel/sof-apl-v1.3.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/bdw
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/bdw/sof-bdw-v1.3.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/byt
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/byt/sof-byt-v1.3.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/cht
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/cht/sof-cht-v1.3.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/cnl
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/cnl/intel
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/cnl/intel/sof-cnl-prod.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/icl
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/icl/intel
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/icl/intel/sof-icl-v1.3.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/sof-apl.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/sof-bdw.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/sof-byt.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/sof-cht.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/sof-cml.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/sof-cnl.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/sof-glk.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/sof-icl.ri
/usr/share/oem-fix-audio-intel-dmic/firmware/intel/sof/sof-whl.ri
/usr/share/oem-fix-audio-intel-dmic/sof-skl_hda_card.conf
```

---

### Post by tiagodfer on 2020-02-23
**SOLVED**: to solve the  issue, I just added options "snd-hda-intel model=laptop-dmic" to  "/etc/modprobe.d/alsa-base.conf". Now the internal mic and the  headphones work like a charm.

---

