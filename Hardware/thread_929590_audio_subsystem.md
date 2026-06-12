---
title: "audio subsystem"
date: 2008-09-25
forum: Hardware
---

### Post by catonano on 2008-09-25
How is it layed out ?

I mean, in the skype options window, the audio periferals tab, for the output periferal and for the input periferal, thera are 2 drop down lists I have to choose the periferals from.

There are 8 (8 !!) periferals:
[LIST=1]
[*]HDA Intel (hw Intel,0)
[*]HDA Intel (plughw Intel,0)
[/LIST]

and then 3 more couples, similer to the above but with a 1 in the end, than a 2 and then a 6.

Now, this is ridiculous, this machine just has its speakers and the jack for the headphones.

It seems that several layers of software are attempting to recognize the hardware but which layers ?

Also what exactly is PulseAudio and what exactly is ALSA and what exactly is the relationship between the two ?

It shouldn't be that hard, anyway.

Now, suddenly, after an update, the USB headphones are not working anymore, the mike still is.

Thanks for ANY hint
Catonano

---

### Post by LunatikOwl on 2008-09-25
ALSA, PulseAudio, OSS and JACK are uniform sound drivers. That is, they have modules for each sound adapter and they serving an API for applications to communicate with the sound hardware. The reason for so many of them is historical of-course. About the USB headset not working you should file a bug report in launchpad, preferably as soon as possible since they need to know that one of they're patches are broken. 

And yes, it is annoying that lately the dev team seam to create more bugs than fix... 
maybe someone needs a wakeup call up there cause this really shaken my faith in this distro:(

---

### Post by markbuntu on 2008-09-25
Since it is impossible to test every update/bug fix on every possible combination of hardware, what do you want the devs to do?
The choices are:
Do nothing
Test as much as possible, release the update and fix the next set of bugs that crop up.
Or wait for about a decade until the fix is tested on absolutely everything.

No organization, no matter how big, can test their products on every single piece or combination of hardware available for a pc. Microsoft spent years and $Billions testing Vista before they released it and it still had a zillion bugs.

---

### Post by catonano on 2008-09-27
I filed the bug report, it's here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275166](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275166)

Now, I hope for the best

I would appreciate if anyone would fix it about the affected package or anything else.

Thanks folks
Bye
Cato

---

