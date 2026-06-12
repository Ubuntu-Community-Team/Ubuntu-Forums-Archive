---
title: "laptop speaker issues"
date: 2009-05-22
forum: Hardware
---

### Post by kristin956 on 2009-05-22
I recently purchased a new HP pavilion dv4-1275 laptop and promptly installed ubuntu 9.04 on it. Everything works beautifully on it with ubuntu EXCEPT for the built in Altec-Lansing speakers. I do have a sound card because headphones work on it, but there is no sound coming from the speakers.. They did work during the short time Vista was running on it. Any ideas on how to get them to work or do I have to wait for ALSA to be updated?

---

### Post by Ayuthia on 2009-05-22
You can first try going into the Terminal and run alsamixer.  Check and see if the volume is set and it is not muted (that speaker will be listed as MM).  If it is muted, press m when that speaker option is selected and it will turn off the mute.

If that does not work, please read the Card and Chip information in the upper left hand corner of the alsamixer screen and post that information here.  It will help us identify your sound card and possibly supply an option to get your card to work.

---

