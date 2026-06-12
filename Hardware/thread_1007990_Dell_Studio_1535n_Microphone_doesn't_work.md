---
title: "Dell Studio 1535n Microphone doesn't work"
date: 2008-12-11
forum: Hardware
---

### Post by justinjstark on 2008-12-11
My internal microphone is not working.  I don't know how to diagnose this.  If I use audacity and change the record setting to hda-intel and try to record, it pops up "Error while opening sound device."

Anybody have any ideas?  I don't know the first thing about diagnosing this problem.

---

### Post by wonderbriefs on 2008-12-11
My Dell Studio 1535 seems to have the same problem. The video from the webcam works fine, but I get no audio.
?

---

### Post by justinjstark on 2008-12-11
> **wonderbriefs said:**
> My Dell Studio 1535 seems to have the same problem. The video from the webcam works fine, but I get no audio.
?

Dang.  I really want to use skype video.  Have you tried using an external microphone through the mic port?

---

### Post by linux_tech on 2008-12-11
Check to make sure Alsa-mixer settings are correct for mic to work.
[http://ankurjain.org/2007/11/03/ubuntu-gutsy-microphone-problem-on-dell-inspiron-1520/](http://ankurjain.org/2007/11/03/ubuntu-gutsy-microphone-problem-on-dell-inspiron-1520/)

---

### Post by justinjstark on 2008-12-11
> **linux_tech said:**
> Check to make sure Alsa-mixer settings are correct for mic to work.
[http://ankurjain.org/2007/11/03/ubuntu-gutsy-microphone-problem-on-dell-inspiron-1520/](http://ankurjain.org/2007/11/03/ubuntu-gutsy-microphone-problem-on-dell-inspiron-1520/)

Holy crap.  It was as easy as going to gnome mixer, edit->preferences, selecting the digital input source options and the capture options, changing digital input source to digital mic 1, and unmuting capture.

Thank you linux_tech.  You are a rockstar. :guitar:

---

### Post by wonderbriefs on 2008-12-21
Yup. I eventually found that too. It's kind of odd that Dell doesn't have this option selected by default.

---

