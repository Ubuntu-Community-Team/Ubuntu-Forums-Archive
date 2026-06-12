---
title: "chaintech av710 back"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by gaillard on 2007-01-27
Well after having pulled everything that the search found I still can't seem to get audio through the av710 and alsa through the back stereo or rear surround (better dacs)

I got the asound.state file from here [http://www.head-fi.org/forums/showthread.php?t=195610](http://www.head-fi.org/forums/showthread.php?t=195610) and then put it in /var/lib/alsa and ran alsactl restore but that didn't do anything...

my lspci shows it there and so does cat /proc/asound/cards

Any idea anyone? Perhaps its a new thing that has changed since I really can't find any info from the new year


Also does anyone know how to get xset m 0 0 to stay without changing it every boot up, or a better way to set no mouse acceleration but still relatively good speed?

Thanks everyone!~!

---

### Post by gaillard on 2007-01-27
anyone?

---

### Post by MCC on 2007-01-27
You might need to try that asound.state file with different versions, the installation of my AV-710 was rather touchy. I'm not anywhere near that computer right now, but I remember that the sample rate needed to be set at 48KHz or it wouldn't work. If alsa gives any errors loading the head-fi asound.state, you need to try a different version of alsa, Also, head-fi has several different asound.states available. Try searching for different ones and try them all until it works. Sorry I can't be more specific but I tried so many combinations I don't remember what worked.

---

### Post by gaillard on 2007-01-27
Ya I've tried some of the different asound.state files but I'd rather just format it like it is supposed to be.  Do you know where I can get its specs or documentation? I can't seem to find it on the alsa site, only asoundrc

Thanks for the help

---

### Post by gaillard on 2007-01-27
apparently all of those asound.state files only work with .9 or earlier from what I have read.  Does anyone with a newer install of alsa have the two rear channels 7 and 8 working with this card?  Because those are the higher quality dacs.  When using the asound.state file that alsa loads for me (11kb) I only hear very faint sound on the FRONT two channels and only in the right ear.  This is with everything unmuted and full volume in alsamixer.

I really need some help here as my work is audio related here at school and I need to get this output working. 
Thanks!

---

### Post by gaillard on 2007-01-27
Thanks for the help, but nevermind because there is a new asound.state on this forum I missed. I will have to test later

[http://166.90.205.111/forums/showthread.php?t=142981&page=3](http://166.90.205.111/forums/showthread.php?t=142981&page=3)

Thanks!

---

### Post by gaillard on 2007-01-27
Awsome. the asound.state on the 3RD PAGE of the link listed above works like a charm.  Thanks

---

### Post by MCC on 2007-01-28
Good to hear, If you haven't already done it, the BlackGate mod helps quite a bit. Just a FYI. My HD-595s / HeadFive amp never sounded better. :)

---

### Post by Bakon Jarser on 2007-12-14
> **gaillard said:**
> Thanks for the help, but nevermind because there is a new asound.state on this forum I missed. I will have to test later

[http://166.90.205.111/forums/showthread.php?t=142981&page=3](http://166.90.205.111/forums/showthread.php?t=142981&page=3)

Thanks!

This link is broken.  Any links to working asound.state files for the latest ALSA(1.0.14)?

---

