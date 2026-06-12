---
title: "Commandline: perform same actions as System &gt; Preferences &gt; Sound?"
date: 2008-07-25
forum: General Help
---

### Post by ceb on 2008-07-25
Hi,

I'd like to follow the instructions for "PulseAudio Removal" given at [https://wiki.ubuntu.com/PulseAudio:](https://wiki.ubuntu.com/PulseAudio:)

"""
PulseAudio Removal

...

To disable pulseaudio in hardy you need to select alsa for for all options in /system/preferences/sound 
"""

I use the OpenBox window manager, and don't seem to have any 'system/preferences' entry in my menu.

Is it possible to perform actions equivalent to those of the GUI sound preferences utility? I couldn't find anything on the web (although I'm not sure what I'm really looking for).

Alternatively, is it possible to install something to give me the same menu as is available in the standard Ubuntu? This option is probably not as good for me, because the machine is pretty old and will struggle with the GUI utility.

Thanks for your help,
Chris

(I'm using Ubuntu 8.04.)

---

### Post by pauper on 2008-07-25
> I use the OpenBox window manager, and don't seem to have any 'system/preferences'
entry in my menu.

It comes with gnome-control-center package.

```
sudo apt-get install gnome-control-center
```

See these manuals as well:

```
man alsamixer
man alsactl
```

---

### Post by ceb on 2008-07-26
[QUOTE=pauper;5457665]It comes with gnome-control-center package.

```
sudo apt-get install gnome-control-center
```

That does actually run ok on my machine, so I used it - thanks.

Unfortunately the list of devices there is completely empty, so I must have a bigger problem. I'll start a new thread for help with that.

Thanks,
Chris

---

