---
title: "Mi webcam is not being recognized!"
date: 2011-04-13
forum: Hardware
---

### Post by carega on 2011-04-13
Hi there! I'm using a COMPAQ PRESARIO CQ-40-320LA laptop and ubuntu meerkat doesn't seem to recognize my webcam. Can anyone tell me how can I solve this? Skype doesnt recognize it and Cheese doesn't as well. I tried gstreamer-properties and the following appears:

```
carega@amaterasu:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux  (v4l)': El dispositivo «/dev/video0» no existe. [v4l_calls.c(168):  gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc1]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2  (v4l2)': No se puede identificar el dispositivo «/dev/video0».  [v4l2_calls.c(488): gst_v4l2_open ():  /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
system error: No existe el fichero o el directorio]
```

Thanks for your help!

---

### Post by ghostcatzero on 2011-06-07
I'm having the same problem. Cheese and Skype both won't recognize my built-in webcam, and I get the same terminal output as carega. Cheese worked fine before this started just today.

---

### Post by ghostcatzero on 2011-06-07
Ok, after going through a bunch of plugin installs and still failing, I found a fix that makes me feel like a total dolt. My netbook has a key for the webcam that lets you turn it on and off. If I press Fn+Esc on my keyboard (Lenonvo Ideapad),Cheese picks it up right away! Look to see if you have a key, prob an F- key in the top row that has a camera icon. Press that key with the Fn key and see if that works.

---

### Post by carega on 2011-06-07
Thanks for the advice! However my computer doesn't have a button for turning the webcam on... so I'm still stuck with the same problem.

---

