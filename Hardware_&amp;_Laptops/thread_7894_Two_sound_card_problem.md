---
title: "Two sound card problem"
date: 2004-12-12
forum: Hardware &amp; Laptops
---

### Post by Marquis_de_Carabas on 2004-12-12
After playing around with a few distros for a couple of months I decided to take the plunge and go all in with Ubuntu.

My problem is that I have SiS on board sound which works just fine, and I also have a Soundblaster Audigy PCI card which is - rather obviously - the one I'd like to use, but it's not working.

The Device Manager lists the Audigy card, and lsmod shows snd_emu10k1 which I believe is the correct one for the Audigy, but alsamixer only shows the SiS.

I don't need to use the SiS sound for anything but there is no option in my bios to disable it. Is there any other way to make Linux ignore it on boot-up? Or simply any way to make the Audigy card usable?

This was never a problem in Windows XP, simply because the on board sound never worked in Windows anyway!

Any help would be greatly appreciated, I've searched Google but haven't found anything of great help, but then perhaps I'm missing something absurdly simple.

---

### Post by Marquis_de_Carabas on 2004-12-13
Okay, I've found a workaround from a [past thread](http://www.ubuntuforums.org/showthread.php?t=985) :

> root@ubuntu:~ # cd /dev
root@ubuntu:/dev # mv dsp /home/backup/   
root@ubuntu:/dev # ln -s audio1 dsp


This strikes me as a bit of a bodge-up job, although it certainly appears to be working. If anybody has any more elegant suggestions then I'd appreciate it, but I'm happy for now  8-)

---

