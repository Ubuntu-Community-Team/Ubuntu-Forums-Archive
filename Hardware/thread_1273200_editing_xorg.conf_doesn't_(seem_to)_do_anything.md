---
title: "editing xorg.conf doesn't (seem to) do anything"
date: 2009-09-23
forum: Hardware
---

### Post by n!k on 2009-09-23
I've never had trouble editing xorg.conf to keep my laptop trackpad from doubletapping before, but this go around with Jaunty I have had no luck editing the xorg.conf to do anything at all. It was almost completely empty instead of normal, and when I try to add the comment for SMHConfig it doesn't recognize it when I try to run gsynaptics. It's like the system isn't reading xorg.conf. I've double checked it and restarted xserver and edited the file a dozen times and have reached my wit's end. I can't move this trackpad without highlighting and clicking everything in sight and am going crazy!

---

### Post by beastrace91 on 2009-09-23
Lines 13-15 in the 9.04 xorg.conf ```
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
```

Sorry that it isn't exactly a solution to your problem but perhaps it will help point you in the right direction.

~Jeff

---

### Post by n!k on 2009-09-24
Thanks, Jeff. I guess I should be looking for what else controls the trackpad? I have no idea where to even begin!

---

### Post by Yellow Pasque on 2009-09-24
The new way to do things is to edit the HAL configuration file for it: [http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#Modifying_hal_configuration](http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#Modifying_hal_configuration)

Or, you could turn off the evdev/hotplugging behavior completely and try to use they synaptic driver:
[http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#I_don.27t_want_this_crap.2C_how_do_I_turn_it_off.3F](http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#I_don.27t_want_this_crap.2C_how_do_I_turn_it_off.3F)

---

### Post by n!k on 2009-09-28
Alright guys, I am begging. Using this computer is my livelihood and it is a nightmare with everything randomly selecting, moving, scrolling, and jumping back and forth in my web browser when I touch this stupid trackpad. I am desperate. I need to know how to edit whatever is doing this. I can get HAL to list the synaptics driver in some command I found but I don't know where this file is located, and it isn't where the suggestions say it should be. Only one blank *.fdi file is located there.

---

