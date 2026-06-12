---
title: "Realtek ALC861 troubleshooting"
date: 2009-01-21
forum: Hardware
---

### Post by konradpiskorz on 2009-01-21
I have a toshiba tecra A6.  It contains a Realtek ALC861 based soundcard.

I have two major problems with this card.  First off, no software mixers actually properly control it.  Secondly, the output is far far too quiet.  Its at the point that any speakers I plug in have to be cranked to max volume just so I can listen as quiet listening levels.

And the output of ```
sudo /etc/init.d/alsa-utils restart
``` results in

```
 * Shutting down ALSA...                                                         * warning: 'alsactl store' failed with error message 'alsactl: get_control:209: Cannot read control info '2,0,0,Master Playback Volume,0': No such file or directory'...                                                                       amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
                                                                         [fail]
 * Setting up ALSA...                                                            * warning: 'alsactl restore' failed with error message 'alsactl: set_control:981: warning: numid mismatch (7/8) for control #7
alsactl: set_control:983: warning: iface mismatch (2/2) for control #7
alsactl: set_control:985: warning: device mismatch (0/0) for control #7
alsactl: set_control:987: warning: subdevice mismatch (0/0) for control #7
alsactl: set_control:989: warning: name mismatch (Off-hook Switch/Off-hook Switch) for control #7
alsactl: set_control:991: warning: index mismatch (0/0) for control #7
alsactl: set_control:989: warning: name mismatch (Caller ID Switch/Off-hook Switch) for control #8
alsactl: set_control:991: warning: index mismatch (0/0) for control #8
alsactl: set_control:993: failed to obtain info for control #8 (Operation not permitted)'...                                                                    amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory

```

I have added 'options snd-hda-intel model=auto' to '/etc/modprobe.d/alsa-base' which fixed some errors.  model=toshiba results in even quieter sound.

If anyone has a realtek alc861 soundcard and worked through similar problems, your experiences would be wonderful.

uname -a output
Linux konrad-laptop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

Any ideas?

---

