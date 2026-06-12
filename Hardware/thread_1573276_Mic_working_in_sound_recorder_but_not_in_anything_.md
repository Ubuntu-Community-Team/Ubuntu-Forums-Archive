---
title: "Mic working in sound recorder but not in anything else"
date: 2010-09-12
forum: Hardware
---

### Post by jorge2904 on 2010-09-12
I have an Acer Aspire 721 and my integrated mic works with sound recorder but in the sound preferances the Input level doesn't move. Its also not working in Skype.

Im using Pulse on 10.10 UNE

Any help is appriciated

---

### Post by an7on on 2010-09-24
Acer Aspire 4820TG - the same.
alsa driver - 1.0.23

---

### Post by Jrgifford on 2010-09-25
Ubuntu 10.04, Asus EEE PC 1001P, same problem.

---

### Post by gale401 on 2010-09-25
You could try going to synaptic package manager and download gnome alsa mixer, it worked for me 
if you see orange this is less volume - the sliders should be at the top, select unmute on mics.
hopefully that works to improve.  cheers

---

### Post by avacado on 2010-10-07
Acer aspire one D260
using lspci most devices show up as N10/ICH7 on this motherboard
mic works well in recorder  and cheese but not skype.
I tried the alsa GUI but this did not help

---

### Post by minimoke on 2010-10-18
Have you tried the mic with the Empathy IM client?

---

### Post by Sane_Malkavian on 2011-01-01
Hi! I'd really like to hear that someone has a solution for this problem, because I can't play my e-guitar with Gtick or Audacity on Aspire One 721 like I usually do on my desktop :guitar:

---

### Post by IWantFroyo on 2011-01-01
Go to sound and switch to analog as the input. If you see a setting for pulse gain, bring it above 0.

---

### Post by edoardo on 2012-04-27
the fix of adding this line

options snd-hda-intel model=acer-aspire position_fix=1

to /etc/modprobe.d/alsa-base.conf 

and then reboot

works perfectly to get Skype working on my Acer Aspire D260 running Ubuntu 11.10
the internal microphone works without having to use pulse audio volume controls and fiddle with the input sources and channels.

found in 
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/mic-issue-with-acer-aspire-one-10-in-ubuntu-unr-729158/#post4087237](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/mic-issue-with-acer-aspire-one-10-in-ubuntu-unr-729158/#post4087237)

---

