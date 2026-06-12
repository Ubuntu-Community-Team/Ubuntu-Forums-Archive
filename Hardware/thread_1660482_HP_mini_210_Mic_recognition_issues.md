---
title: "HP mini 210 Mic recognition issues"
date: 2011-01-05
forum: Hardware
---

### Post by betoqp on 2011-01-05
I have an HP mini 210 series with the Ubuntu Unity (aka. netbook edition) installed. I recently downloaded Skype and tried to configure my microphone, but the system doesn't seem to recognize it. So I tried to do some voice recording with the system's app Voice Recoreder and nothing either. Neither program detected the microphone. Anyone knows how to fix this? Thanks!

---

### Post by betoqp on 2011-01-07
Any help?

---

### Post by betoqp on 2011-01-07
Any help?

---

### Post by betoqp on 2011-01-07
Any help?

---

### Post by kostkon on 2011-01-07
Your mic should work fine. Just open your sound prefs and make sure that it isn't muted.

Also, in Skype's options, select the *Sound Devices* tab and disable the *Allow Skype to automatically adjust my mixer levels* option.

---

### Post by Haggis McHaggis on 2011-01-07
I just had the same problem with HP pavilion dvd6 in Netbook interface - but was fine in Desktop.  

In netbook went Applications>Sound [preferences]>Input   ... the input volume was muted (as suggested by above post.

Unchecked the box then tested with Applications>Sound Recorder and found that the microphone had to be tuned down to about 35 %.

---

### Post by betoqp on 2011-01-20
turns out I just had to install some ALSA packages but thanks!

---

