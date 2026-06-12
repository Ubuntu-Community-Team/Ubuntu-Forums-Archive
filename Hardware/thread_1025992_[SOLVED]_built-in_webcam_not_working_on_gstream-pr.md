---
title: "[SOLVED] built-in webcam not working on gstream-properties on thinkpad x300"
date: 2008-12-30
forum: Hardware
---

### Post by andresmh on 2008-12-30
While [unsuccessfully trying to get cheese to work]("http://ubuntuforums.org/showthread.php?t=1020342") on a x300 thinkpad, I read on the README that one of the requirements are > to ensure that it works with the Gstreamer Framework and Video4Linux2 (V4L2) or Video4Linux (V4L). To test this, you can use the 'gstreamer-properties' tool

I tried running gstreamer-properties and it freezes after trying the video input, see this screenshot:
[[IMG]http://img514.imageshack.us/img514/5688/screenshotuc1.th.png[/IMG]](http://img514.imageshack.us/my.php?image=screenshotuc1.png)

While running on the command-line I think I don't get any critical errors:
```
$ gstreamer-properties 
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

```

One interesting thing is that the webcam works on Skype. See this:
[[IMG]http://img369.imageshack.us/img369/7383/screenshotoptionsmn0.th.png[/IMG]](http://img369.imageshack.us/my.php?image=screenshotoptionsmn0.png)

---

### Post by andresmh on 2008-12-31
I fixed the problem by enabling intrepid-backport and intprepid-proposed in Software Sources > Updates and then getting the latest kernel and other packages.

---

