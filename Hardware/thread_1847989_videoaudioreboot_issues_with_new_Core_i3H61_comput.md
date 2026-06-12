---
title: "video/audio/reboot issues with new Core i3/H61 computer"
date: 2011-09-21
forum: Hardware
---

### Post by blauser on 2011-09-21
I recently bought a Gateway [SX2855-UB22P]("http://us.gateway.com/gw/en/US/content/model/PT.GCFP2.003") and immediately installed ubuntu 11.04 64bit. Most things work great, but I've noticed some minor annoyances. I hope this is the right place to look for answers.

First, when connected to my monitor via VGA and my TV via HDMI the screen goes blank while trying to boot. If I unplug the HDMI cable from the pc, boot into ubuntu, and reconnect it, then things work. Well, almost. I've got a 720p TV and when set to that resolution, the edges aren't shown on the TV. That is, they are cut off.

Second, when I am trying to watch something on the TV I have to switch the audio device manually from the analog stereo out to digital HDMI stereo and back again when I'm done. Also, when I plug in headphones (in the front headphone jack) I get audio from both the speakers and the headphones. I can't find away to switch it to just the headphones.

Finally, whenever I've restarted (after the initial install & restart-requiring updates), the computer doesn't go all the way. The screen blanks, the mouse light goes off, but I have to do a hard reset. The computer shuts down just find, though.

Thanks for your time and help.

---

### Post by .... on 2011-09-22
> **blauser said:**
> I
Second, when I am trying to watch something on the TV I have to switch the audio device manually from the analog stereo out to digital HDMI stereo and back again when I'm done..
I think this is expected behavior because you're switching between audio devices.

> Also, when I plug in headphones (in the front headphone jack) I get audio from both the speakers and the headphones.
Please run alsa-info.sh [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

### Post by blauser on 2011-09-22
> **.... said:**
> I think this is expected behavior because you're switching between audio devices.

I was hoping there would be away to assign precedence. When HDMI is connected that's the preferred audio output. Either that or just pump the audio out to both devices.

The results of alsa-info.sh are here [http://db.tt/aUajqOFi]("http://db.tt/aUajqOFi")

---

