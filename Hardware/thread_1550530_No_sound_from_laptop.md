---
title: "No sound from laptop"
date: 2010-08-11
forum: Hardware
---

### Post by GlideKensington on 2010-08-11
I've searched through the forums and tried the solutions given but couldn't get my sound to work

I have a HP pavilion dv7 laptop and I'm running Lucid Lynx.

I get the following output when I run the alsa-info bash script found in another thread:

> 

ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'utils_alsa-info.sh --help' for command line options.

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1502: No soundcards found...
cat: /tmp/alsa-info.zCcbNqM6qE/alsactl.tmp: No such file or directory


Any help would be appreciated.  FYI, I'm a linux noob :/

---

