---
title: "Help - Microphone not working with Hardy"
date: 2008-05-01
forum: Hardware
---

### Post by Chris2691 on 2008-05-01
I have a Dell Inspiron 1720 laptop with an built in webcam and microphone. When using Skype the webcam works fine but not the microphone. The microphone also does not work when I use sound recorder.
If a use a USB headset I have no problems with sound recording/transmission using the above two applications.
I have played around with Alsa Mixer and have checked that capture is ticked on and that the recording slider is turned up and the mic and speaker icons are not muted.
Has anyone any idea what else I should try?

Thanks

Chris

---

### Post by DSK on 2008-05-02
Hey Chris here is what I did to get my mic working in Hardy.


In teminal window type:
```
alsamixer
```

Then arrow over to the right under to "<Mic Boost> and hit "m" to turn it on.

Then arrow over to the right to "<Mic Sele>" and change it with the up arrow key to "Mic1". (if its already "Mic1" change it and then change it back to "Mic1".

At this point I hit "esc" and rebooted not sure if the reboot is necessary or not.

After reboot in terminal :
```
alsamixer
```

Then hit "F4" to list only the capture devices.

Arrow over to "Mic" and use the up arrow key until all green bars are shown.
Then arrow over to "Analog M" (analog mix) and use the up arrow key until all green bars are shown.

Now hit "ESC" to close alsamixer then close terminal window.

Then open Sound Recorder from Applications->Sound & Video->Sound Recoder.

In Sound Recorder:
Changer "Record from input:  to Microphone
Change "Record as:"   to CD Quality, Lossy(Ogg multimedia)

Hit Record, say a few things, hit stop, then hit play to hear what you just said.

And microphone should now be working!


Hope this helps.
DSK:guitar:

---

### Post by Chris2691 on 2008-05-02
Thanks Mate: Your a genius

---

### Post by atmartin50 on 2008-06-08
Thanks a lot DSK!

Though I had neither "Mic Sele" nor the "Analog M" in alsamixer, I used your post as a stepping stone for tweaking my settings and was able to get my mic working quickly. Many thanks!

Aaron

---

### Post by austar on 2009-07-24
hi i tried all the steps above but when i go to f4 Arrow over to "Mic" and use the up arrow key until all green bars are shown.
Then arrow over to "Analog M" (analog mix) and use the up arrow key until all green bars are shown.

i cant do anything in mic and analog there is just (----)

---

