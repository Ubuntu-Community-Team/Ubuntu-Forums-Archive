---
title: "Skype issues on HP NX9420"
date: 2009-03-07
forum: Hardware
---

### Post by gjosef on 2009-03-07
Having some troubles using Skype (2.0.0.72) on my HP NX9420-laptop, in Intreprid Ibex (8.10).

Simply put, sound does not work:

When the sound devices in the options panel are set to their defaults ("Default device (default)"), I am unable to make any audio calls. The test call stops with the error message "Problem with Audio Playback". I can fix this by manually setting the Sound Out device to "pulse", but then stumble upon the message "Problem with Audio Capture". Setting the Sound In device to either "HDA Intel (hw:Intel,0)" or "pulse" instead of "Default device (default)" makes the test call run. However, I still do not here my own voice in the echo's playback. :( Any advice on what I need to do?

TIA

---

### Post by gjosef on 2009-03-23
Got it to work. Found some good tips on this page:

[http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/](http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/)

My final problem was probably the microphone volume.

---

