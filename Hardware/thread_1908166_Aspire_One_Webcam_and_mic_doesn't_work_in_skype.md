---
title: "Aspire One: Webcam and mic doesn't work in skype"
date: 2012-01-12
forum: Hardware
---

### Post by DocSeaLion on 2012-01-12
Hi,

I'm a fresh guy in ubuntu. It looks interesting since ubuntu 11.10 runs really nice on my wife's Acer Aspire One netbook. But I've recently got sudden bug: inbuilt webcam has disappeared from Skype showing "No Devices Found" though it was before.

lsusb gives just
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Thank you in advance

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-01-14
Don't know about the camera problem, but is your mic also not working in Skype? If yes, does the problem occur only in Skype or elsewere as well? Take a look at this thread here:

< [http://ubuntuforums.org/showthread.php?t=1579600](http://ubuntuforums.org/showthread.php?t=1579600) >

---

### Post by madvinegar on 2012-01-14
Try to switch off one of your two speakers by setting the sound balance far left or far right.
If your mic will work, then download and install from ubuntu software center the "pulse audio volume control".

Open it. Go to the 4th tab (input devices), press the little button with a lock on it (so as to unlock the two channels from moving together), and switch off completely one of the two channels.

You can then set back your overall sound balance as it was before so as to get sound from both of your speakers.

This should do the trick.

---

### Post by DocSeaLion on 2012-01-14
thank you for the help with the mic. I have already fix it. but I still suffer from not working of my web cam...(((

---

### Post by axelrad on 2012-02-11
hi,'
did you ever fix your webcam problem?
I also can't get it to work on aspire 5630 even tough lsusb shows its there:
Bus 001 Device 005: ID 046d:0896 Logitech, Inc. OrbiCam
I'd appreciate your input

---

### Post by joao.taborda on 2012-03-20
having the same problem, but no camera listed on lsusb did anyone found a solution?

---

