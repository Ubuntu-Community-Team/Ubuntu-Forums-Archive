---
title: "Samsung 4K TV &quot;Unknown Display&quot;"
date: 2016-05-04
forum: Hardware
---

### Post by neorob22 on 2016-05-04
Hello

I have s Samsung 4K TV (I believe the model is UN50JU6500FXZA). On Ubuntu, Kubuntu, and Ubuntu gnome, the TV is is labeled as unknown display and in both a fresh install and the live CD, the max resolution is 1024x768. The TV is connected to a nvidia 980 ti. Any clue why this is happening?

---

### Post by neorob22 on 2016-05-05
Additional information: I believe the 980 ti uses an HDMI 2.0 port to connect to the TV. Does Linux have issues with HDMI 2.0?

---

### Post by SeijiSensei on 2016-05-05
Are you using the proprietary NVIDIA driver?  It appears that the most recent driver, 361, is best for your card.  However it only exists in the repositories for 16.04 and 16.10.  For earlier Ubuntu versions, you need to use a PPA as described here: [http://askubuntu.com/questions/738377/correct-way-to-get-a-gtx-980-working-in-ubuntu-15-10-x64](http://askubuntu.com/questions/738377/correct-way-to-get-a-gtx-980-working-in-ubuntu-15-10-x64)

See if that helps.

---

