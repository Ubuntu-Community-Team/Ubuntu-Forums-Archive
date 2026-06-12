---
title: "Webcam and microphone not working after Ubuntu install"
date: 2015-02-17
forum: Hardware
---

### Post by mreider2 on 2015-02-17
hi all, my wifes Dell Inspiron 15 laptop had win 8.1 installed, offcourse w anything MS, once the OS got upgraded to 8.1 a few weeks ago, the laptops microphone stopped working and she couldnt use her Skype. I tried to fix the audio drivers but no luck and decided to just overwrite win 81 with Ubuntu 1404 lts. 

once the install was done, the built-in webcam stopped working, i tried running cheese and it comes back with No Device Found

i ran 'ls /dev/video' but theres no video devices present.  Microphone still not working (and there are no good recording apps out there to test this either).

I find Ubuntu to be very spotty with any sort of device drivers, either graphic, audio or video. 

Going to try to overwrite Ubuntu with Win 7, the only stable Win version out there besides XP.

---

### Post by benrob0329 on 2015-02-17
Maybe:
```
sudo apt-get install libwebcam0
```
For the audio, perhaps a hardware issue?

---

### Post by benrob0329 on 2015-02-17
Audacity is a good audio program, you could try that.
For Skype, [http://www.skype.com/en/download-skype/skype-for-computer/](http://www.skype.com/en/download-skype/skype-for-computer/).

---

### Post by mreider2 on 2015-02-17
will try, thanks.

---

