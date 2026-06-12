---
title: "Are my drivers still on this machine (Inspiron Mini -- Ubuntu preinstalled!)"
date: 2009-09-12
forum: Hardware
---

### Post by LeFou on 2009-09-12
Second weekend on this issue. Another thread has detail but here's a summary.
I wanted to record something.
Someone (Satan?) suggested this would be easier w/ALSA so I removed pulseaudio. This also removed "ubuntu-desktop" and caused wireless and sound not to work at all.
I reinstalled pulseaudio and ubuntu-desktop, as wireless & sound are more important than the thing I wanted to record.
No improvement.
Per the "Comprehensive Sound Problems Solutions Guide" I have
mcrouch@localhost:~$ aplay -l
aplay: device_list:205: no soundcards found...

and
mcrouch@localhost:~$ sudo lspci -v | grep  Audio
[sudo] password for mcrouch: 
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 06)

Indicating that "Ubuntu is detecting the presence of your soundcard, but the drivers are not installed/running"

Not finding the driver on [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel) , the solutions guide wants me to compile my own?!?

I don't particularly want to take this on, as sound & wireless were working perfectly before pulseaudio was removed, so I suspect the drivers really are hanging around somewhere. Any help?

UPDATE:
I found System->Administration->Hardware Drivers and "Broadcom STA wireless driver was listed, but "Enabled" was unchecked and "Not in use" was red. I checked Enabled and was prompted to restart.

I restarted and no improvement. Opening Hardware Drivers again shows this driver unchecked and "Not in Use".

Q: What, in addition to checking "Enable", does one need to do to enable a driver?

UPDATE 2:
I reinstalled jockey-gtk (the restricted drivers manager) and rebooted. I was encouraged to see "Enabling restricted drivers... OK" in the messages while booting. But still "Not in Use" and won't Enable.

Q: What does "OK" mean in this context?

---

