---
title: "NBR on eee 1005 hab: No Microphone"
date: 2010-01-07
forum: Hardware
---

### Post by phaedral on 2010-01-07
I have spent a fair few hours trying various suggestions, including installing a backports module, adding pavmenu, removing pulseaudio. Nothing seems to get me to my onboard internal microphone.

I am not a newb, but neither am I a guru. All pointers and help appreciated.

The box is an eeePC 1005HAB. I created an installer usb stick with 9.10 netbook installer as directed at pendrive linux, then installed to an 8gb SD card. Everything is really, really groovy except I can't seem to get the onboard mic to work (so no skype, no audacity, ...)

---

### Post by rlsimpso on 2010-01-30
I am having the same problem on the same hardware.  Does anyone have any suggestions?

---

### Post by Alienhunter2010 on 2010-02-28
Me too, using a 9.10 Ubuntu (NOT remix serie).

I add that:

[LIST]
[*]I try some manual fix for older Ubuntu releases; Internal Mic for EeePC seems to be really weird on any EeePC netbook!
[*]**External** Mic is working! On Skype and using the soundrecorder too.
[/LIST]

My EeePC 1005PE has a stereo microphone array (**why** on a netbook!?)

I buy a Netbook to travel light, I would like to use the existing internal mic, not an external one!

Thanks to all!

---

### Post by dondada on 2010-03-24
I would love to sort this out, too. I can confirm that the mic works in sound recorder but not in skype. This was both in 9.10 nbr and 10.04 nbr.

---

### Post by luwandah on 2010-03-27
I followed some of the other threads advice and installed pavucontrol. For some reason you have to offset the left/right mic controls (on 1005PE - stereo mic) to something like 90% left, 10-20% right (or vice-versa). Then in Skype I unchecked the "allow skype to change mixer levels". Audio works with skype, though if there is a lot of background noise the other end of skype calls says the sound drops out.

---

### Post by dondada on 2010-04-22
I tried pavucontrol as per luwandah's advice. Still no audio from the mic. Mic works fine in Sound Recorder as well as in XP and Win 7.

---

### Post by dondada on 2010-10-10
Offsetting the left/right channel levels in pavucontrol does indeed get the mic working in Skype. Don't forget to disallow Skype access to the mixer levels, too.

---

