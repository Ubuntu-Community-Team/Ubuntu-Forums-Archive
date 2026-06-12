---
title: "Can't hear sound source"
date: 2014-07-26
forum: Hardware
---

### Post by John_Bryant on 2014-07-26
Trying to record sound from an external sound source and cannot hear the source sound. There does not seem to be a 'monitor' setting in any form of Linux that I have tried. This has never been a problem in windows. Any suggestions?

---

### Post by Dennis N on 2014-07-26
What program are you using to do the recording?

---

### Post by tgalati4 on 2014-07-27
Open up a terminal and look through:

```
alsamixer
```  

Hit F4 to show Capture devices.  Post the Card and Chip that shows in the upper left corner.  Make sure the volumes are turned up and mute is disabled on all channels.

---

