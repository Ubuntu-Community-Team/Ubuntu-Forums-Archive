---
title: "Issue with HD Intel Sound after updating"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by KCorp on 2008-02-13
Hey Guys,

I had the sound working a few days ago, followed some tutorials on getting the new ALAS etc.. Everything worked fine without problems.

There was an update (think its an kernal update) and sound driver seems to be not working again, get the same error message as before:

"No volume control GStreamer plugins and/or devices found."

Any help would be appreciated

---

### Post by Yellow Pasque on 2008-02-13
Try the suggestion in this thread, about adding model=3-stack into alsa-base (or whatever model= might be applicable to your codec. [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

Also, this thread has a user complaining of the same issue, which he fixed by going into alsamixer and muting/unmuting everything a few times.
[http://ubuntuforums.org/showthread.php?t=694038](http://ubuntuforums.org/showthread.php?t=694038)

---

