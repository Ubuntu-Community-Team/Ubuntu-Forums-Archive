---
title: "Unable to get sound working with Toshiba A135-S4527"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by Yoshidude on 2007-11-11
I've found many walkthroughs and so forth that posted fixes for the same exact laptop model, or similar ones, but I haven't had any luck. I've tried various modprobe edits, installing the ALSA drivers/libraries/utilities, and all types of other things that I've seen, and none have worked for me. Some specifics:

I'm on Ubuntu Gutsy.

When I type,

```
sudo modprobe snd-hda-intel
```
I get 
```
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
I have checked to make sure that the .ko file exists, and it does. I can't view its contents, but it exists.

For my lspci, the detected audio device is Intel Corporation 82801G  (ICH7 Family)

The current line that I have at the end of the alsa-base file (I have seen *many* different versions of what should be put there) is
```
options snd-hda-intel position_fix=1 model=3stack
```


If there's any other information that is needed, let me know and I'll get it. Thanks for any help, this is the only thing not working for me in the otherwise awesome Ubuntu 7.10.

EDIT: Nevermind. For anybody else who sees this and has the same problem I did, the main issue was with the modprobe command. Solution was at [http://ubuntuforums.org/showthread.php?p=3563848](http://ubuntuforums.org/showthread.php?p=3563848)

---

### Post by Yoshidude on 2007-11-11
Er, bump?

---

