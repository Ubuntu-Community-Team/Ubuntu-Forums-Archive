---
title: "Sound stutters - occasional kernel panic"
date: 2009-12-09
forum: Hardware
---

### Post by hidinginthemountains on 2009-12-09
I recently upgraded from Intrepid to Jaunty. I now have problems with my sound stuttering a bit (ie: while playing music in Rhythmbox, watching/listening to streams in Firefox, watching movies in VLC...etc). Though the problem seems worse at some times then others, I believe that the computer doing "other things" (like a torrent client writing to the disc for example) while I'm listening is what causes it to manifest.

Additionally, at least twice in the last week my laptop has suffered what I assume is a kernel panic (completely locks up, CAPS LOCK blinks). I think this *may* be related.

I'm not sure exactly what information to provide so that folks can help me with this, so to start with I'll throw in the output from [FONT="Courier New"]aplay -l[/FONT]

> :~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

TIA for any help. Let me know what other info I can provide.

---

Adding a little more info. Let me know if there are any particular log entries that might be useful.

> :~$ lspci -v | grep -i audio
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

---

### Post by hidinginthemountains on 2009-12-09
not really "solved", but I figured this was in the wrong place so I'm directing to the post in General Help now.

[http://ubuntuforums.org/showthread.php?t=1350192](http://ubuntuforums.org/showthread.php?t=1350192)

---

