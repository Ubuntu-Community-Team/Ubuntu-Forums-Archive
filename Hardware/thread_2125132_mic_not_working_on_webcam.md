---
title: "mic not working on webcam"
date: 2013-03-13
forum: Hardware
---

### Post by deusabscondus on 2013-03-13
I enter gstreamer-properties and get this output

```
godfreysown@Gregory:~$ gstreamer-properties


(gstreamer-properties:2745): Gtk-WARNING **: Unknown property: GtkDialog.has-separator


(gstreamer-properties:2745): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
```

Could anyone provide dummy-proof instructions on what I must do to fix this?
Thanks,
DeusAbs

---

### Post by deusabscondus on 2013-03-13
i tried 
pulseaudio -D and got:

```
godfreysown@Gregory:~$ pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.
godfreysown@Gregory:~$ 





```

Could someone kindly lend a hand?
Thx,
DeusAbs

---

### Post by lisati on 2013-03-13
Threads merged.

Please do not start multiple threads for the same problem, not only can it get confusing, it dilutes the community's efforts to help.

---

