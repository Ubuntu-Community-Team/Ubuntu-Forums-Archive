---
title: "audio playback problem"
date: 2009-04-13
forum: Hardware
---

### Post by slimx3m on 2009-04-13
i am wondering if anybody knows how i could fix an audio problem playback.  for example, i am able to hear my mic and record things in "audacity" but not to play it after is being recorded.  this only happens whenever i use "mono".  if i try "stereo" it would  give me an error message.

i followed [this tutorial]("https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems") and still have problem.

here is the information of my audio card:
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
Subsystem: Giga-byte Technology Device a002

---

### Post by slimx3m on 2009-04-17
no thoughts? :(

---

### Post by maakhi on 2009-04-17
i cannot install sound driver. i downloaded sp33867.exe and sp38529.exe but both the installables didn't work. i am using a compaq 6510b notebook. if anyone has any idea.. please tell

---

### Post by slimx3m on 2009-04-26
in ubuntu? you do not need to use *.exe files. you will need to find the proper repositories. 

here are couple of links that might help you to resolve the problem.  thanx to Jaunty my problem is fixed.

ALSO, you need to be part of the following groups:
pulse
pulse-access
pulse-rt

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)
[http://blog.rajatpandit.com/2008/11/15/skype-audio-playback-and-capture-problem-on-ubuntu-810/](http://blog.rajatpandit.com/2008/11/15/skype-audio-playback-and-capture-problem-on-ubuntu-810/)
[http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html)

hope it helps.

---

