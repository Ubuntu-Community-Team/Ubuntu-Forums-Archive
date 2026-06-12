---
title: "Both Ubuntu 7.04 And Ubuntu 7.10 Can't Detect My Sound Card Correctly"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by Voyage2nd on 2008-02-04
I'm using ASUS A6R laptop, and in Windows XP, I see my sound card is Analog Devices Soundmax Integrated  Digital Audio, but in Ubuntu 7.04, it was detected as three devices:
0:ATI IXP (Alsa mixer) 1;ATI IXP Modem(Alsa mixer) 2:Analog Devices AD1896(OSS Mixer), in Ubuntu 7.10, the same problem exists, besides, there is no sound at all in both system, so 
can anyone give me some tips?

---

### Post by Voyage2nd on 2008-02-05
:)Now my sound card works fine!!!!!!!!!!!!!
 I should great thank user 'ephraim', I've spend much time on my sound, I even try to remove this silence Ubuntu system, but after I read this page:[http://ubuntuforums.org/showthread.php?t=365342&highlight=asus+a6r](http://ubuntuforums.org/showthread.php?t=365342&highlight=asus+a6r), and did this:open up terminal.

sudo gedit /etc/modprobe.d/blacklist

at bottom of list, type...

#get rid of snd-atiixp-modem
snd-atiixp-modem

then save.

my sound works, After all, I do suggest user with no sound problem in Ubuntu just like me to do some similar things.

My sound card device:  ATI Technologies Inc IXP SB400 AC'97 Audio Controller  

Excuse for my poor English :)

---

