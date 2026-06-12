---
title: "M-Audio Keystation 49e not working.."
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by haxality on 2007-01-23
I recently obtained an M-Audio Keystation 49e USB MIDI keyboard, and I was wondering what I'm supposed to do to get it working. I've loaded all the required modules in many different combinations, installed a firmware loader, tried multiple synth programs, and still no luck. It seems like everywhere I look the solution is "plug it in and it magically works!" which can be really frustrating when it doesn't. As usual, any help would be greatly appreciated.

---

### Post by czad on 2007-01-28
I have an Axiom by M-audio..

I would be happy to know if you resolved this.  The cd-rom included is not linux friendly.

-cv.

---

### Post by markedman on 2007-02-08
Hi... I was having problems with this too.  Boot up your computer with the Keystation turned off, and do a  
```
sudo modprobe snd-seq-midi
```
Now turn on the keyboard, and it should be detected in rosegarden, or whatever you're using.  In rosegarden, if you go to "Configure midi devices", it should be there.

Cheers,
-Mark

---

### Post by eric71 on 2007-02-09
I just bought a Keystation 49e.  It was recognized upon plugging it in and turning it on.  Didn't need to load any drivers manually.  It works well with Rosegarden. This is in Feisty, but I've read that the Keystation series have been well supported in Linux for a while now. I've read that people have had problems with the USB connection to the keyboard.  If it wiggles a little bit, they get no signal. When switched on, are the blue lights lit by the octave control buttons?  It may be the connection is loose.

Edit:  Actually what I thought was an on/off switch is to switch between USB/9V power sources.  Make sure it is set to USB.

---

