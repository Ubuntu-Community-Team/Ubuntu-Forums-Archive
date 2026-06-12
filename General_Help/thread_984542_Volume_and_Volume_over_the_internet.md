---
title: "Volume and Volume over the internet"
date: 2008-11-16
forum: General Help
---

### Post by Proxima_Centauri on 2008-11-16
On my Desktop which I am using Intrepid 8.10 I have the volume icon but lately it has not been controlling the volume on my computer. When I open players such as totem and lindvd there volume controls work as they should but if I even go and mute the icon on the tool bar on the desktop it does nothing. And I get no streaming audio from the Internet at all. I think it might have something to do with the audio mixer maybe please help this is becoming a nightmare.

---

### Post by Th3Professor on 2008-11-16
What are the preferences set to (from right-clicking on the "speaker" icon in the icon tray (in a gnome panel))?

---

### Post by Proxima_Centauri on 2008-11-17
it is set as HDA Intel (Alsa Mixer)

---

### Post by Th3Professor on 2008-11-18
> **Proxima_Centauri said:**
> it is set as HDA Intel (Alsa Mixer)

Which option is highlighted below that?

Right-click on speaker icon.
Click on preferences.
Below your "HDA Intel (Alsa mixer)" is a list.

The HDA-etc. is your device.
The list is your "track to control" with volume control.
If you select a different option in the list, the volume control will alter the volume for that option rather than the one it is currently set at.

---

