---
title: "No audio - Compaq Presario V6000"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by Patrus on 2008-04-14
hi there.

since installation i haven't been able to experience any sound on my laptop. I've read through countless posts and tried everything i've read, however i still can't get it to work.

alsa mixer shows that the master and pcm are at 100% and unmuted. however on the manual volume touch control the mute light is red (signalling mute) opposed to its unmuted blue. when i use vista i can obviously switch between the two, however when i attempt to change between mute and sound in ubuntu the red light remains and a small window comes up showing that the sound has been muted or unmuted. after entering 'aplay -l' into the terminal this shows:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

any ideas anyone?

---

### Post by friedbrains on 2008-04-14
hi!  my 1st post here...

just 2 days ago i installed Ubuntu 7.10 on my Compaq Presario V6000, dual booth with Vista HP pre-installed, and so far did not do any changes on the drivers...  my audioo works- using the HDA Intel (Alsa Mixer), the Sound Events set to autodetect, and so are the music and movies, and audio conferencing...  i actually like the booth-up sound...

:guitar:

---

### Post by Patrus on 2008-04-14
seems as though i am in your exact position... minus audio. your laptop has a 64bit processor yes? my audio has not worked since the beginning, even with the live cd it does not work. what is "sound events"?

---

