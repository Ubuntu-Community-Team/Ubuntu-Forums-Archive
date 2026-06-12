---
title: "multimedia keys"
date: 2014-12-14
forum: Hardware
---

### Post by ohernandez3 on 2014-12-14
I am running Ubuntu on a Toshiba Satellite S55T-B5233 and most everything works. The only thing that bugs me that does not have full functionality are the multimedia keys. Turning off the touchpad does not work I modified xmodmap. It was difficult to modify xmodmap because the keycodes are incorrect and are off by 8, so keycode 227 actually mapped to keycode 235. Also the keycode 235 toggled the display instead of the touchpad, before I made changes to xmodmap. Any ideas how to correct the keycodes reported by showkey, and get the multimedia keys to work correctly.

Thanks,

Xander

---

### Post by ajgreeny on 2014-12-14
This is not quite answering your question and I am not sure about any differences in this situation between Ubuntu and Xubuntu but in Xubuntu the following commands added to the keyboard shortcuts listing and using my media keyboard keys the media keys worked well for raising, lowering, and toggling mute of the volume output.

However, if the correct XFCE volume deamon is running for pulseaudio, as it should be, they are no longer needed.  For some reason after an update the deamon stopped running, and I used these commands.  Could your problem also be related to some background deamon not starting as it should?
These commands assume alsamixer is installed; amixer is the command-line control of alsamixer.

**amixer set Master playback 3dB-**
 lowered volume by 3dB.
[B]amixer set Master playback 3dB+
[/B] raised the volume by 3dB.
**amixer -D pulse set Master toggle**
 toggled the master volume on/off without affecting the underlying volume level.

I'm not certain how you set this up in Ubuntu with unity as DE, but I presume there is a simple way to do it.

---

