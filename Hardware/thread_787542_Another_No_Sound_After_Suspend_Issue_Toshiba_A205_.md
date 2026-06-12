---
title: "Another No Sound After Suspend Issue: Toshiba A205 Laptop"
date: 2008-05-09
forum: Hardware
---

### Post by Leontius on 2008-05-09
I installed Ubuntu Hardy to my new laptop, a Toshiba A205 series. Most of the things work properly except that there is no sound after suspend (sleep). However, it works flawlessly after a reboot. I searched across this forum and the internet, and I have tried these solutions but none works so far:

1. killall esd: no process killed...
2. Restarting the sound module (modprobe -r snd_hda_intel && modprobe snd_hda_intel): FATAL: module snd_hda_intel in use. Even after I killed the sound mixer applet.
3. Editing /etc/default/acpi-support and setting lots of things: MODULES='snd_hda_intel', ACPI_SLEEP_MODE=standby, SAVE_VBE_STATE = false

For the modem, I used a winmodem driver from Linuxant which comes with a custom ALSA driver. Is it the one causing the problem? Or perhaps the modem driver uses snd_hda_intel (I think the modem driver does use it) so I can't remove the module? I've tried modprobe -r snd_hda_intel without the modem attached but it won't work (module snd_hda_intel still in use). How can I restart snd_hda_intel?

Thanks for the time.

---

