---
title: "software center and update manager crash"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by Pete Kingston on 2009-11-09
After upgrading to Ubuntu 9.10                -

If I run the Ubuntu Software Center it flashes and then disappears, and when I run the update manager it get this message:

W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF

any ideas?

---

### Post by michy99 on 2009-11-09
```
gpg --keyserver subkeys.pgp.net --recv 46D7E7CF
gpg --export --armor 46D7E7CF | sudo apt-key add -
```

---

### Post by Pete Kingston on 2009-11-09
Cool. that fixed my update manager, but no change on the software center. it starts, flashes the beginning screen and disappears...

---

### Post by michy99 on 2009-11-09
Try starting it from a terminal and see what error message you get.```
software-center
```

---

### Post by Pete Kingston on 2009-11-10
desktop:~$ software-center
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml

(software-center:11942): GStreamer-WARNING **: adding type GstFourcc multiple times

(software-center:11942): GStreamer-WARNING **: adding type GstIntRange multiple times

(software-center:11942): GStreamer-WARNING **: adding type GstDoubleRange multiple times

(software-center:11942): GStreamer-WARNING **: adding type GstFractionRange multiple times

(software-center:11942): GStreamer-WARNING **: adding type GstValueList multiple times

(software-center:11942): GStreamer-WARNING **: adding type GstValueArray multiple times

(software-center:11942): GStreamer-WARNING **: adding type GstFraction multiple times

(software-center:11942): GStreamer-WARNING **: adding type gdouble multiple times

(software-center:11942): GStreamer-WARNING **: adding type gfloat multiple times

(software-center:11942): GStreamer-WARNING **: adding type gchararray multiple times

(software-center:11942): GStreamer-WARNING **: adding type gboolean multiple times

(software-center:11942): GStreamer-WARNING **: adding type GEnum multiple times

(software-center:11942): GStreamer-WARNING **: adding type GFlags multiple times

(software-center:11942): GStreamer-WARNING **: adding type gint multiple times

(software-center:11942): GStreamer-WARNING **: adding type gint64 multiple times

(software-center:11942): GStreamer-WARNING **: adding type glong multiple times

(software-center:11942): GStreamer-WARNING **: adding type guint multiple times

(software-center:11942): GStreamer-WARNING **: adding type guint64 multiple times

(software-center:11942): GStreamer-WARNING **: adding type gulong multiple times
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

### Post by Pete Kingston on 2009-11-10
I reinstalled GStreamer and now it works... thanks for the help! :-)

---

### Post by Dave.Watkins on 2009-11-13
I am getting the same problem with Software Center. It flashes up and then closes. If I open with a terminal - I get the same list of errors with Gstreamer as listed above. I have reinstalled everything that I can see involved with Gstreamer using Synaptic but am still getting the same erros as below. Can anyone help?

dai@dai-laptop:~$ software-center

(software-center:3016): GStreamer-WARNING **: adding type GstFourcc multiple times

(software-center:3016): GStreamer-WARNING **: adding type GstIntRange multiple times

(software-center:3016): GStreamer-WARNING **: adding type GstDoubleRange multiple times

(software-center:3016): GStreamer-WARNING **: adding type GstFractionRange multiple times

(software-center:3016): GStreamer-WARNING **: adding type GstValueList multiple times

(software-center:3016): GStreamer-WARNING **: adding type GstValueArray multiple times

(software-center:3016): GStreamer-WARNING **: adding type GstFraction multiple times

(software-center:3016): GStreamer-WARNING **: adding type gdouble multiple times

---

### Post by Dave.Watkins on 2009-11-14
Software_center is now working again. I ran Computer Janitor and acccepted its recommendations. After that Software_Center is fine.

In hindsight it stopped working after installing LiVES video editor.:D

---

### Post by _krt_ on 2009-12-06
I've had the same problem. Removed gstreamer0.10-ffmpeg and software center works again.

---

