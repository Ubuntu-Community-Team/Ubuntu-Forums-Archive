---
title: "resuming from suspend takes a really long time"
date: 2010-06-26
forum: Hardware
---

### Post by fvzwieten on 2010-06-26
My laptop is a hp probook 6540b with an ATI videocard in it. This problem used to be intermittent, but it now seem to be occurring each time. my latest /var/log/pm-suspend has a timestamp on awaken and finished. The delta is 110 seconds! All messages in between those two timestmaps report success, exept for one:

```
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:Sessions still open, not unmounting
Sessions still open, not unmounting
success.
```

Don't understand this message much. What has PulseAudio to do with (un)mounting? However, the hard disk light on my laptop is constantly on during this time, os it is doing something with the disk.

Other things worth mentioning is that I have a encrypted home (and thus also an encrypted swap). I saw some issues with it when googling around but that only seemed to be with hibernatiion.

Any ideas?

---

