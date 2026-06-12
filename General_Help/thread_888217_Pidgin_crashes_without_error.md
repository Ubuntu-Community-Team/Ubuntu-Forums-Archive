---
title: "Pidgin crashes without error"
date: 2008-08-12
forum: General Help
---

### Post by Altay_H on 2008-08-12
Recently, Pidgin has been crashing without an error about 20 seconds after I run it. I'd been using it with the facebook extension successfully for a while, but now it just crashes. When I run it from the Terminal I usually just get a "Segmentation Fault" error, but I managed to get a more interesting error after running it with the facebook account disabled. It doesn't crash consistently. Sometimes it runs without any issues. Searching this forum I've found similar issues which were resolved by changing the sound to ALSA or reinstalling Pidgin. I tried the former without success, and plan to try reinstalling Pidgin. If anyone knows what may be causing this issue, I would be quite grateful. Here's the error:

```
altay@altay-laptop:~$ pidgin

(pidgin:8925): GStreamer-CRITICAL **: 
Trying to dispose element play, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(pidgin:8925): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:8925): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
Segmentation fault

```

---

