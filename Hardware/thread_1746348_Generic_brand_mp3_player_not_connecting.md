---
title: "Generic brand mp3 player not connecting"
date: 2011-05-01
forum: Hardware
---

### Post by daltore on 2011-05-01
I just finished getting Natty working almost the way I want it to, but there are still a couple more bugs I have to work out.  One of them is that it's acting rather strangely with my mp3 player.  It's basically just a 4 GB flash drive with media playing capability and a microSD card reader, so I would assume it uses MSC.

    Here's the process.  I plug it in, the player turns on.  Sometimes it goes to the "charging" screen first, and other times it goes directly to the "USB" screen.  Either way, it usually shows up on my computer as a RockChip USB mass storage device, and a RockChip SD reader.  However, if I attempt to open either one, nothing happens.  After a bit, those disappear and the computer refuses to believe the player is connected, and the player just goes to its main screen, just like it's only plugged into a charger.  lsusb and mount (when trying to manually mount one of the corresponding devices) both crash while the mp3 player is plugged in at all, even after the devices disappear from the "Computer" screen in the file manager.

    Flash drives, dedicated microSD card readers, and external hard drives work normally.  The mp3 player has no setting for USB mode, so whether it's MSC or MTP, it's stuck that way, although it's so generic and simplified I would assume it's just MSC.  It worked perfectly in Maverick.

    Does anyone have any idea what might be causing this or how to fix it?

---

