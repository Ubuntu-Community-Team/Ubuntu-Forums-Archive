---
title: "wrong bitrate for Creative Creative VF0470 Live Cam"
date: 2010-08-29
forum: Hardware
---

### Post by jqdennis on 2010-08-29
[https://patchwork.kernel.org/patch/83173/](https://patchwork.kernel.org/patch/83173/)

Creative VF0470 Live Cam reports 16 kHz while actually sampling at 8 kHz.  This causes playback to sound like the Chipmonks.

Is there a patch like the link above for Ubuntu?

Thanks

---

### Post by jqdennis on 2010-09-02
Found guvcview (Synaptic).  It allows settings camera and audio settings.  The Input bitrate could be set from Default to 16000, which is what it reports to Linux anyway.

---

### Post by jqdennis on 2011-01-06
well, 10.10 broke it, and guvcview doesn't fix it

---

