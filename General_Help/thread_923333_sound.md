---
title: "sound"
date: 2008-09-18
forum: General Help
---

### Post by Whisper45 on 2008-09-18
A few days ago my audio worked fine, I could listen to music, watch films, etc, but just a few days ago it stopped working, and whenever I click the speaker (which has a little x next to it) it says:
> 
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

If I right click and press 'Open Volume Control' it says: > No volumce control GStreamer plugins and/or devices found.


How can I fix this? Thanks.
Edit:
I do have an onboard soundcard, SoundMax or something.

---

### Post by mempman on 2008-09-18
You can fix this by going in SYNAPTIC package manager, selecting all GStream and the assosiated drivers for your hardware, and then completely reinstalling everything.

---

