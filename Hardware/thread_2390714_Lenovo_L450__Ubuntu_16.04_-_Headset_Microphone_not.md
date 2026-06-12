---
title: "Lenovo L450 / Ubuntu 16.04 - Headset Microphone not working, speaker work"
date: 2018-05-01
forum: Hardware
---

### Post by ibims on 2018-05-01
Hello,

I am using Ubuntu 16.04 on my Lenovo Thinkpad L450. The notebook has a single audio jack that can be used for both input and output. I plugged my Headset (Trust Chat Headset Primo) in it and tested if it works. The output works, but I cannot record anything. When I open my sound settings in Ubuntu and go to "Input", the sound level remains at 0% when I speak. 

Which logfiles /tools could help me finding the issue?

---

### Post by ibims on 2018-05-02
Does anyone have an idea?

---

### Post by #&amp;thj^% on 2018-05-02
This is just an idea for you try.
Have you tried using the terminal and enter
```
alsamixer
```
And then enter "F6" for your soundcard.
And checking to see if the headset and mic is muted?
Use your arrow right/left to select the device and to unmute use your keyboard and press m to unmute, and then use the up and down arrow keys to increase/decrease your volume levels.
See Screenshots

---

### Post by ibims on 2018-05-02
Hi,
thank you for your reply. I didn't know that tool, looks nice to me :)
Unfortunately it didn't help. I still managed to get the microphone working now (finally).

The problem was that I disabled the built-in microphone of my Thinkpad L450 in the BIOS and I didn't expect that this would also disable any manually plugged-in microphone. So there seems to be no way to really disable the built-in microphone while still being able to use a headset. Or do you know a way to do that?

Why I want this? Paranoid reasons. I also disabled the fingerprint sensor and the webcam in the BIOS and would love to be able to do the same with the microphone without losing the ability to use a headset.

---

### Post by #&amp;thj^% on 2018-05-02
Well I'm glad you got it working. ;)
But in Bios it is all or nothing as far as disabling builtin Mic, as you like me have only a single audio jack for both in and out. (Mine is a Lenovo Thinkpad T430)
Lenovo needs to get a bit more creative with those Bois functions. 
However there are USB Soundcards out there that would allow you to disable your internal Mic, if you are really in need for that. :)

---

### Post by 13787110225-p on 2018-05-10
the same case

---

