---
title: "Intel HD audio not working"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by mtwalther on 2007-05-02
Okay.... I have gotten my card to work previously. I had to reinstall Feisty for certain reasons and attempted to find the thread that helped me fix it the first time. Problem is I couldn't find that thread and found another one which had me do...

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop ubuntu-minimal
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
sudo gedit /etc/modprobe.d/alsa-base
and add "options snd-hda-intel probe_mask=8 model=auto" to the end of the file

I did this and now everything went to sh**., when I open up a terminal, and start something with gedit these multiple alsa errors pop up. If anybody has any suggestions please help me out. Worst case scenario I can just reinstall feisty, I have /home as well as /etc and /usr on seperate partitions, but I really don't want to waste my time doing that.

Heres the output when I try to edit anything in Geidt...

- using device default
- using device default
ALSA lib conf.c:1587:(snd_config_load1) _toplevel_:25:0:Unexpected char
ALSA lib conf.c:2848:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075:(snd_config_update_r) hooks failed, removing configuration

This happens about 5 or 6 times in a row.


When I get into the GUI preferences menu and open up sound, I have no sound devices listed on the bottom drop down menu. 

modinfo soundcore displays..

mtwalther@Laptop:~$ modinfo soundcore
filename:       /lib/modules/2.6.20-15-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     45750F13477CBA5B6F36F46
depends:        
vermagic:       2.6.20-15-generic SMP mod_unload 586

Another terminal display..

mtwalther@Laptop:~$ aplay --list-devices
aplay: device_list:222: no soundcards found...

Someone help me out, don't post many 'help me out' threads, lets see what we get outta it though.

Thanks...

---

