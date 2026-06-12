---
title: "Sound is strange and distorted"
date: 2008-08-02
forum: General Help
---

### Post by knutschr on 2008-08-02
Suddenly the sound is very strange.
It is like a dark, slow zombie voice.
This is not related to any program, as the logout sound is like this too.
What can I do to repair it?

---

### Post by Xuniltoor on 2008-08-02
I had a couple of bizzare sound issues and removed pulse audio using synaptic and all of my sound problems were cured.

---

### Post by knutschr on 2008-08-02
I tried your suggesting but it didn't help :-( I had installing upgrades going on when it happened, so that may be the reason.
So may be I just have to wait for next upgrade?

---

### Post by knutschr on 2008-08-03
[bump]
I'm not able to repair this :-(

---

### Post by Xuniltoor on 2008-08-03
did u restart after removing pulseaudio and check to make sure you show alsa under all 4 dropdown menus under system, preferences, sound? it really doesnt sound like a big deal and it sure sounds like a pulse issue.

---

### Post by JaimeZX on 2008-08-03
> **Xuniltoor said:**
> did u restart after removing pulseaudio and check to make sure you show alsa under all 4 dropdown menus under system, preferences, sound? it really doesnt sound like a big deal and it sure sounds like a pulse issue.

How does one remove PulseAudio?

---

### Post by Sjovan on 2008-08-03
Could it be that you have PCM-volume at 100% ?

For some strange reason that do **** up the sound in linux...

---

### Post by der_joachim on 2008-08-04
> **Sjovan said:**
> Could it be that you have PCM-volume at 100% ?

For some strange reason that do **** up the sound in linux...

Only with certain chipsets. My EEEPC sounds happy with 100% PCM. So does the SB128 of my home PC. My work PC has an intel sound chip and that one does have the PCM issue.

@OP: the [ALSA wiki]("http://alsa.opensrc.org/index.php/Category:Troubleshooting") has a good troubleshooter.

---

### Post by knutschr on 2008-08-04
I changed everything to use ALSA.
Then I in synaptic searched for ALSA and reinstalled everything related to it.
And now it is fine again :-)

And thanks to Xuniltoor who made me remove Pulseaudio and switch to ALSA!

---

