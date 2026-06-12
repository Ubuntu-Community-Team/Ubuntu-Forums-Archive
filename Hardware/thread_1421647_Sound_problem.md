---
title: "Sound problem"
date: 2010-03-04
forum: Hardware
---

### Post by dldeskins on 2010-03-04
I have a Toshiba Satellite U305-S7448. I have been dual booting if for awhile now (3 years?).  Recently, I tried getting Skype to work on the Ubuntu side (9.10). After fiddling with it (installed gnome-alsamixer, etc), I got it to work (I think). When I rebooted, I noticed that my volume control applet was gone and I had no sound. I opened the gnome-alsamixer and there were no volume controls. I rebooted to the Windoze side (Vista home premium) and had no sound there either. It was showing that I had bluetooth attached speakers, which is interesting since I don't even have bluetooth on this laptop.  I re-installed Windows (thinking that if it were a software problem, it would be easier corrected with the factory install). No go... still no sound.

Then I thought about the BIOS. I went through the BIOS and checked for any hardware related items that might affect the sound. When finished, I reset to the default and saved.  When I restarted Windoze, I got a "installing Realtek drivers"... it finished and asked me to reboot. When I did, I had a shutdown system sound. When I got back into windoze, I still had no sound. 

After some time of thinking that it was a hardware problem, I decided to give it another try, just in case.  I went back into the BIOS, did a default restore and restarted into windoze. When I was starting up, I raised the volume control by the sound wheel. Sure enough, the sound was restored.

When I started on the Ubuntu side, there is a start up sound, but no sound on youtube or sound files or movie player. The volume control in the Control Center won't even start now.

Any suggestions? What did I mess up?

Thanks,

Don

---

### Post by dldeskins on 2010-03-04
anyone?

---

### Post by agnes on 2010-03-06
See [this sticky ]("http://ubuntuforums.org/showthread.php?t=205449")
I'd think you should reinstall alsa (as is explained there also).

Also, doesn't 9.10 come with PulseAudio by default, and Skype in the repo using PulseAudio by default? If you used Skype with PulseAudio you have to edit the volume control, settings etc. with the program 'pavucontrol'. Not with the alsa utils.

---

### Post by dldeskins on 2010-03-07
Thanks, that did it.

---

