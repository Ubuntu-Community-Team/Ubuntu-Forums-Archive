---
title: "Mic doesn't work"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by Azmodan on 2005-08-21
My father wants to use Skype on Ubuntu.  Skype installed flawlessly but the microphone don't work.

I tried to use "Sound Recorder" to test the mic, it gives 'alsa device "default" had an error. I checked alsamixer and everything seems fine there.

The microphone also works without any hitch on Knoppix.

If I go to system / multimedia selector and switch the source to OSS, it doesn't give any error when trying to record but records only silence.

I Googled for 'alsa device "default" had an error' but it didn't turn out anything useful.

Any idea to find the cause of the problem ?

Thanks

---

### Post by foolsh on 2005-08-21
this is long shot but try killing the esd
open the system monitor and scroll down till you find esd right click and kill 
works for my xmms when i want to play mp3s

---

### Post by Azmodan on 2005-08-21
I killed esd but it didn't change anything...

I already set it to release the sound card when it's not using it anyway (Skype needs that to work).

---

