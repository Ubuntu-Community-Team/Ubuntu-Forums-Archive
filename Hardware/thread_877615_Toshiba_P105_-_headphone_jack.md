---
title: "Toshiba P105 - headphone jack"
date: 2008-08-01
forum: Hardware
---

### Post by dan508 on 2008-08-01
Here is the problem.  Toshiba p100 series have no sound that comes out of the headphone jack.  However the speakers on the laptop will work fine.  I was wondering if anyone had any ideas on how to patch this problem.  I know that there have been many similar reports of this but no resolution yet.  If you for some random reason need a link to fixing the fan on the graphics card for a Toshiba P100 series here is the link... [http://ubuntuforums.org/showthread.php?t=771223](http://ubuntuforums.org/showthread.php?t=771223)  Any and all help would be appreciated.  I have check the alsamixer and have the most up to date drivers for the sound and my bios.  Thanks.

---

### Post by Martin Fierro on 2009-05-20
Hi Dan598,

I had sound from my front speakers but with a quite low quality and showing distortion. When running the same machine with the @indows (vista) the sound was great. The headphone jack was not working also.

I have solved this quality problem replacing Alsa with OSS (open sound system - [www.opensound.com](www.opensound.com)). Now my toshiba P105-S6177 sounds very good and the headphone jack works, allowing me to connect my laptop even with my home theater.

Open sound has its origin in Unix system and was lately replaced by ALSA. 

I installed the debian package corresponding to my operating system and kernel version.

I also removed the pulseaudio from my system (sudo apt-get remove pulseaudio) and everything worked fine.

I am running ubuntu Jaunty.

I hope this info (despite late) may help others.

---

