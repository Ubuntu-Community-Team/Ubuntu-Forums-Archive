---
title: "built-in mic not working"
date: 2010-11-12
forum: Hardware
---

### Post by mkdigital on 2010-11-12
hi!

i just installed  ubuntu (10.4) on my sony vaio NS11 M/W, everything seems to work fine, except the built-in mic. audio output works fine.

i tried to enable every audio input source via alsamixer. i dont know whether it is correctly installed or not, where can i check this?

 alsamixer says the only audiodevice (/proc/asound/cards) is hda intel.

thanks in advance

---

### Post by mkdigital on 2010-11-12
just tried audio input with line in which works fine. its just the built-in mic

---

### Post by lidex on 2010-11-12
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Dale61 on 2010-11-14
I thought I had a non-working inbuilt microphone, but I googled 'Skype on Ubuntu' and got to the actual Skype page, then the troubleshooting page showed how to get the mic working.  It took me some time to actual work out what screen to be in at what time, but after several attempts, my mic now works.

Apparently, the reason given is that the mic is mono, and the default settings are for stereo and cancel out the mic.  You have to enable the as mono, then it works.

---

