---
title: "No soundcard detected after update"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by KLineD on 2008-02-05
Although I have experienced some incompatibilities with my soundcard under Linux, I could use it just fine, as long as I didn't have to record anything. I previously updated ALSA following the guide [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and that didn't solved my recording issues but playback was unaffected.

However today I updated my kubuntu installation and upon rebooting I found out that kmix has a X and it says "mixer cannot be found". Alsamixer returns "alsamixer: function snd_ctl_open failed for default: No such file or directory"

Inspecting dmesg output gives several of these messages:
> [   16.868000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   16.868000] snd_hda_intel: Unknown symbol snd_ctl_add
[   16.868000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   16.868000] snd_hda_intel: Unknown symbol snd_pcm_new
[   16.868000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   16.868000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   16.868000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   16.868000] snd_hda_intel: Unknown symbol snd_card_register
[   16.868000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   16.868000] snd_hda_intel: Unknown symbol snd_card_free

I have to point out that I had to reboot because my laptop completely froze while transcoding some video. After that, I started to get the mixer error but I don't know if the froze or the update is to blame.

Any help??

---

### Post by marshal_mellow on 2008-02-05
My sound card is also broken after the update. 
I had to use that hda intel walkthrough to get working when i first installed but now it stopped working again.

---

### Post by aaaantoine on 2008-02-05
If you compiled a new version of ALSA for your PC and have installed the updated kernel, you have to recompile and reinstall the ALSA driver.  Then restart your computer.

Presumably you shouldn't *have* to restart, but the methods I tried using to get sound working without restarting (sudo /etc/init.d/alsa-utils restart ; sudo /etc/init.d/alsasound restart) didn't bring me any sound.

If you did not compile an updated version of ALSA from source before the kernel patch, this solution is not intended for you.

---

### Post by marshal_mellow on 2008-02-05
I recompiled alsa the same way i did before and it worked perfectly.
thanks.

---

### Post by KLineD on 2008-02-05
Excellent, thanks a lot. That fixed it.

---

### Post by aaaantoine on 2008-02-07
No problem.  Don't forget to mark the thread as [SOLVED].

To do this, use the Thread Tools drop-down at the top of the page.

---

### Post by riahmatic on 2008-02-07
Is it possible to revert to the repo version?

---

