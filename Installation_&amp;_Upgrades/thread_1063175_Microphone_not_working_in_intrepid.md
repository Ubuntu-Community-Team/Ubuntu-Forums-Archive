---
title: "Microphone not working in intrepid"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by triplemaya on 2009-02-07
Want to use skype, no mic. I have googled and followed a number of different instructions but no joy. Last was the following:-
  * killall pulseaudio
        * sudo apt-get remove pulseaudio
        * sudo apt-get install esound
        * sudo rm /etc/X11/Xsession.d/70pulseaudio
from 
[http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/](http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/)
which did not work.

Everthing is on in volume control and nothing muted.

When I use sound recorder no input shows up, and I tested the mic on skype but all was silence from my end.

Playing sound has always worked fine, but I've never wanted to use a mic before, mic works fine on other pc.

---

### Post by jimscafe on 2009-02-25
Nobody is replying to this problem. I have the same problem.

In 2006 I installed ubunto and used is as desktop for 8 months. However, I never got the microphone to work and hence had to boot into XP to use skype.

I had to go back to using XP eventually and returned to Ubuntu only yesterday. Guess what, the same problem. Skype is installed ok but no microphone. Different hardware, different version of ubunto - but the same problem.

(Microphone and skype work fine in XP - dual booting, so not hardware problem.)

---

### Post by jimscafe on 2009-02-26
Still no help getting a microphone working.

Just for comparison, I also installed slackware on the same pc and although installing packages is more cumbersome in slackware, it seems easier to get things done with the help from the forums.

I have got the microphone and skype working in slackware through the help of the forums. The following is what I did to get the microphone working
in a terminal type
alsaconf
followed by
alsamixer
and in alsamixer move to the capture section and activate it.

After that the mocrophone worked.

I couldn't do that in ubuntu as alsaconf doesn't seem to be there. So still no microphone in ubuntu. (I did check alsamixer, which is available but it looked quite different from the version I had in slackware.)

I am still hoping to get the microphone working in ubuntu.

---

### Post by fpiragibe on 2009-04-01
I'm using an Intrepid based 64 bits Mint version (version 6 - Felicia). Same problem here. I've tried everything, even removing Pulse audio, with no results. OSS-static version doesn't work; static version doesn't work; no input device choice works. 'seems Skype is trying to use a non-existent front microphone (my box doesn't have the jackets, although the MOBO has support for it), or it needs a not installed 32 bits library. My notebook runs a 32 bits Mint Felicia distribution and everything works just fine. The differences are the 32 bits distribution and the presence of a "front mic" jacket; so, I'm assuming the problem relates to that. Can anyone offer a guess?

---

### Post by tacantara on 2009-04-01
I just recently made the leap from Intrepid to Jaunty (beta).  I did have external mic problems in Intrepid, and sure enough, the same problems came back when I switched OS versions.  Nonetheless, I uninstalled all the PulseAudio stuff, etc. as described in the first post.  Then, I went into alsamixer, made sure that the audio inputs were all set to digital, and cranked everything up.  I still can't get an external mic to work, but the mic that's built into my laptop is working well enough.  If you're using a laptop that has a built-in mic, you might want to give it a shot.  Good luck :)

---

### Post by JoshTodd on 2009-04-02
I'm havin the same issue with an external mic.  Any ideas?

---

