---
title: "Acer Aspire One D255 microphone?"
date: 2010-11-17
forum: Hardware
---

### Post by PeterTheUnGreat on 2010-11-17
Hi, my Dad is looking at buying one an Acer D255 notebook, but first want's to be sure he can get the microphone working on Skype when using Ubuntu (he is not fussed whether it is the internal or an external mic)
I have searched the forums and the initial indications are not good. However I was wondering if anyone has managed to get the microphone working and if so what did it take?

Many thanks
Pete

---

### Post by laurenbanjo on 2010-11-17
I love this computer, but so far the mic does NOT work out of the box. I got it less than two weeks ago, so I haven't had a chance to play around with it yet. I'll let you know if I figure it out... I'm sure there's something I can do.

---

### Post by PeterTheUnGreat on 2010-11-18
Thanks for your reply, I think I will warn my Dad to either wait or get a different netbook.
Pete

---

### Post by cgallaty on 2010-12-08
I just had to set this up in Ubuntu 10.10 (Netbook Remix) on a D255. 

First get pavucontrol from the Ubuntu Software Center (or apt-get install if you roll that way) 

Launch it, then go to the Input Devices tab and hit the little lock icon, then drop one of the two channels to 0 ('Front Right') worked for me.

You should be able to see your levels right away.

---

### Post by james.kazuba on 2011-03-10
Amazing. This simple fix totally worked. 

Thanks.

---

### Post by frncz on 2011-09-24
This trick worked fine for me, on my D255 running Oneiric Beta2
Thanks

---

### Post by leighdf on 2013-05-04
Oh, this is frustrating. The fix works until Skype places a call. I THOUGHT that unchecking "Allow Skype to automatically adjust my mixer levels" in the Sound Devices options page would fix it, but it doesn't. The workaround I've found that actually works 100% of the time is to do the following:
[LIST=1]
[*]Prior to making a skype call, start a terminal and run "alsamixer", then press F4 to display capture devices.
[*]Place the Skype call.
[*]While the phone is ringing, in the terminal, press "z" repeatedly to set the left channel to 0, and "e" to set the right channel to the desired level (for me, around 75).
[/LIST]
I have to do this for every single Skype call. To me, that's not a Linux problem, that's a Skype problem. 

Being lazy, I've scripted this to a desktop script, which I run while the call is being placed:[INDENT]#! /bin/bash
amixer set Capture,0 0%,75% unmute[/INDENT]

Hope this helps someone else.

---

### Post by logan85 on 2014-01-26
> **leighdf said:**
> Oh, this is frustrating. The fix works until Skype places a call. I THOUGHT that unchecking "Allow Skype to automatically adjust my mixer levels" in the Sound Devices options page would fix it, but it doesn't. The workaround I've found that actually works 100% of the time is to do the following:
[LIST=1]
[*]Prior to making a skype call, start a terminal and run "alsamixer", then press F4 to display capture devices.
[*]Place the Skype call.
[*]While the phone is ringing, in the terminal, press "z" repeatedly to set the left channel to 0, and "e" to set the right channel to the desired level (for me, around 75).
[/LIST]
I have to do this for every single Skype call. To me, that's not a Linux problem, that's a Skype problem. 

Being lazy, I've scripted this to a desktop script, which I run while the call is being placed:[INDENT]#! /bin/bash
amixer set Capture,0 0%,75% unmute[/INDENT]

Hope this helps someone else.


Hi, 

for me this simple trick worked, but skype automatically overwrited the audio settings, 
so I eliminated pulseaudio totally, and then selected the default devices from the list, in skype.
First in alsamixer make the audio adjustments necessary.
Then follow this guide: [https://support.skype.com/en/faq/FA10964/can-i-change-the-sound-system-used-by-skype-for-linux#disable_pulse](https://support.skype.com/en/faq/FA10964/can-i-change-the-sound-system-used-by-skype-for-linux#disable_pulse)

I hope, that this will be a final fix for it!

---

