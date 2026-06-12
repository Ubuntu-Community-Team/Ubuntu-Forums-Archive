---
title: "No Sound From M Audio Delta 66"
date: 2015-02-04
forum: Hardware
---

### Post by Curbside Jimmy on 2015-02-04
This device is used with Audacity.

It shows up as if drivers are installed both in the program as well as in the ALSA mixer.

The Computer is a 64 bit Dell Optiplex 755.
The attachments show that the Delta 66 is recognized.

[ATTACH=CONFIG]259718[/ATTACH][ATTACH=CONFIG]259719[/ATTACH][ATTACH=CONFIG]259720[/ATTACH]

---

### Post by tgalati4 on 2015-02-04
Did you bring up *mudita24* and make your audio patches?  No patches, no sound.

---

### Post by Curbside Jimmy on 2015-02-05
> **tgalati4 said:**
> Did you bring up *mudita24* and make your audio patches?  No patches, no sound. I         know almost nothing about working with linux. I would love to try that. I do not know what an audio patch is Nor do I know what muditi is, what it is for or how to bring it up. 

I can follow a proceedure if you can explain how to do those things.

---

### Post by Curbside Jimmy on 2015-02-05
There is no output device showing up on the sound setting. Is there a way to get something to show up. I just reloaded ALSA and it still doesn't show up, after restarting.

[ATTACH=CONFIG]259735[/ATTACH]

---

### Post by tgalati4 on 2015-02-06
Open a terminal:

```
sudo apt-get install mudita24
```

Run *mudita24* and go to the Patches tab.  Start pushing buttons until you get sound.  Then go the the Profiles tab and save a profile.

---

### Post by Curbside Jimmy on 2015-02-15
We can close this one. It is working now. Thanks.

---

### Post by Yellow Pasque on 2015-02-16
> **Curbside Jimmy said:**
> We can close this one. It is working now. Thanks.

Threads are not closed/locked just because they're solved. You can mark the thread solved by choosing that option under the thread tools menu (right above the first post).

---

