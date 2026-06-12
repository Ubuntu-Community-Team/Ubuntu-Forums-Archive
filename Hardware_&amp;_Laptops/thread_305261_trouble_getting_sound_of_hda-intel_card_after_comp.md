---
title: "trouble getting sound of hda-intel card after compilng alsa-source"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by Doojek9 on 2006-11-23
Found [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Using_alsa-source]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Using_alsa-source") Howto and used it (tried the alsa-source using module assistant and getting alsa drivers. right after the first compilation and modprobe of course, I've managed to get sound. the Howto also says you need to add the line snd-hda-intel at /etc/modules file and reboot. on startup the computer hanged and I got something like modprobe - abnormal exit. using the rescue mode and deleted the line I've added at /etc/modules I've managed to bring the computer up but now it doesn't detect the sound card at all. hitting  modprobe snd-hda-intel doesn't return the prompt and obviously doesn't load the module.

Any suggestions?

Thanks.

---

### Post by rax_m on 2006-11-26
Hmm.. I seem to be having the same problem... 

did you get anywhere with this?

Cheers
Rax

---

### Post by StormGuy on 2006-12-20
I can't manage to get my snd-hda card to work either.  

aplay -l returns
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

But no sound.  Anyone managed to get it to work in Edgy?  I'm also using a laptop (a Gateway MX6448 ), and tried adding snd-hda-intel to /etc/modules.  It didn't freeze up...but it didn't do anything, either.

---

### Post by zvandiver on 2006-12-30
Has anyone come across a solution for this?  I, too, have compiled the latest alsa drivers to no avail.  I have a new Gateway MX6447 laptop.
Zane

---

