---
title: "Master volume doesn't work."
date: 2008-10-26
forum: General Help
---

### Post by robert shearer on 2008-10-26
After an update sounds started to misbehave with the Master volume unable to adjust both channels at once nor stay where it was set.
In addition, as it was moved, there was no sound in one channel and a sharp buzzing.

I tried the Pulseaudio fix here...
[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)
but with no improvement apparent.

Tried another soundcard (both Ensoniq 1370) but the fault was still the same.
Removed the soundcard altogether and enabled the onboard audio.( Intel 82801BA-ICH2)
This removed the buzzing and setting difficulties but now the master volume control won't work at all.
Neither the Gnome panel volume control nor the Master volume control in the 'Volume control' window work at all.They move but do not adjust the sound.

The Headphone control in the'Volume control' window now seems to act as the master control but ,of course, I have to open this window every time I want to change volume settings.

How can I make the Panel volume control work as master again??

---

### Post by Tamlynmac on 2008-10-27
Right click on the volume control in panel and select preferences. Then select master - What does the upper window show? 
IE: VIA 8237 (Alsa Mixer)

Check that against your system/preferences/sound/devices tab/Default Mixer Tracks/Device

---

### Post by robert shearer on 2008-10-27
> **Tamlynmac said:**
> Right click on the volume control in panel and select preferences. Then select master - What does the upper window show? 
IE: VIA 8237 (Alsa Mixer)

Check that against your system/preferences/sound/devices tab/Default Mixer Tracks/Device

a) Intel 82801BA-ICH2(alsa mixer)

b) Yes they are the same.

---

### Post by robert shearer on 2008-10-28
bump?

---

