---
title: "No Shutdown/Logoff Sound"
date: 2008-07-13
forum: General Help
---

### Post by ProgenitorVirus on 2008-07-13
Ubuntu not playing logout sounds, but everything else works fine.

Anybody know how to fix this?

Thanks!

---

### Post by fooman on 2008-07-13
have you checked under the system > preferences > sound > "sounds" tab ?

scroll down to the bottom and make sure "log in" and "log out" are set to something besides "no sound".

---

### Post by ProgenitorVirus on 2008-07-13
Tried that, actually had it set to a custom LogOff sound, so it isn't anythign like that.  I've hear people are having a lot of problems with PulseAudio server that Ubuntu is using, could it be that thats causing the problems?

---

### Post by bark50 on 2008-07-14
I'm having the same problem.  My system > preferences > sound > sounds tab is set for the logout theme, but nothing plays when I shut down.  Playing the sound I realize I used to have it, but it's gotten lost somewhere along the way.  Any help would be appreciated.

---

### Post by MatthewPlanchard on 2008-07-14
I'm having the same problem and I didn't even realize it until just now. Interesting.

---

### Post by Aearenda on 2008-07-14
I've read somewhere that it's because the new Pulseaudio sound server shuts down too quickly at logoff - but I don't remember where I read it.

---

### Post by JR_Moneybags on 2008-07-15
Also having the same problem here.
All system sounds (login logoff beep) do not work - the standard games have no sound (although I'm not sure that they actually have sounds to start with but eI have enabled them) - wine will not play sound.

In system>preferences>sound>devices I can get the test to work if I set it to either ICE1712 or ALSA (although system sounds still do not play) but I get the following error if I select PulseAudio or Autodetect.
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

- Interestingly media players work fine - and the little drum tappy sound thing that plays at the login screen works fine also.

My guess is that the problem is with the Pulseaudio server somehow, although I wouldn't the slightest how to fix it.

Love some help.
JR

---

### Post by Avinash.Rao on 2008-07-16
I get the same error. But, the login sound works! Is this a bug and should we report it.



> **JR_Moneybags said:**
> Also having the same problem here.
All system sounds (login logoff beep) do not work - the standard games have no sound (although I'm not sure that they actually have sounds to start with but eI have enabled them) - wine will not play sound.

In system>preferences>sound>devices I can get the test to work if I set it to either ICE1712 or ALSA (although system sounds still do not play) but I get the following error if I select PulseAudio or Autodetect.


- Interestingly media players work fine - and the little drum tappy sound thing that plays at the login screen works fine also.

My guess is that the problem is with the Pulseaudio server somehow, although I wouldn't the slightest how to fix it.

Love some help.
JR

---

### Post by Aearenda on 2008-07-16
It's already there: [https://bugs.launchpad.net/ubuntu/+bug/214370](https://bugs.launchpad.net/ubuntu/+bug/214370)

See [http://ubuntuforums.org/showthread.php?t=789858](http://ubuntuforums.org/showthread.php?t=789858) for a hack workaround.

JR_Moneybags' problem sounds different.

---

### Post by jimmydean886-2 on 2011-07-11
I like the idea of creating a new shutdown sequence, but my login screen preferences window has no "edit commands" button.

[IMG]https://readsds.sytes.net:5997/~jim/scst123.png[/IMG]

This is very disappointing, and I would much appreciate someone pointing me in the right direction.

---

### Post by Aearenda on 2011-07-11
That button was part of an old version of Ubuntu, and it's long gone. This thread is 3 years old. I suggest you start a new thread seeking help for what you are trying to achieve, but be aware that Oneiric may well replace GDM with another login manager, so anything you achieve on Natty would not necessarily carry forward into Oneiric.

---

