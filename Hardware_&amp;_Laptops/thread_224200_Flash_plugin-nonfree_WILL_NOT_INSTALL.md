---
title: "Flash plugin-nonfree WILL NOT INSTALL"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by ViperAFK on 2006-07-27
I went to synaptic to install flash and java, but the instalation progress freezes on this "setting up flashplugin-nonfree and the computer is still working fine but the instalation hasn't progressed for about 10 minutes. I can't end the install either, its stopped progressing near the end (see screenshot)

---

### Post by ViperAFK on 2006-07-27
i got annoyed and restarted and synsptic tells me to run dpkg --configure -a but that just goes to "setting up flash plugin-nonfree again" which DOESNT DO ANYTHING, and i can't install any java plugins it goes to "setting up flash plugin-nonfree yet again, can someone please help

---

### Post by siman on 2006-07-27
i have this problem for a while now - 3 months i guess, havent found a solution or gotten an answer so far.

seems this problem is rare?

see also:
[http://ubuntuforums.org/showthread.php?p=1206027#post1206027](http://ubuntuforums.org/showthread.php?p=1206027#post1206027)
[http://ubuntuforums.org/showthread.php?t=196569](http://ubuntuforums.org/showthread.php?t=196569)

---

### Post by AbEx on 2006-07-27
Ran into this today.... took about 30 minutes, thought it hung up on it but eventually moved on.

---

### Post by ioxer on 2006-07-28
I recently did two installs of Ubuntu. The first I didn't have this problem, the second I did. The only differences were that the second install had all the latest updates prior to installing flash and I had done a manual install of flash first. I'm guessing an update creates this problem. I'm currently taking AbEx's advice and am playing the waiting game...

As for the "dpkg --configure -a" part, all I had to do was "sudo apt-get remove flashplugin-nonfree". It removed what it had installed with flash and got apt-get, Synaptic, etc working again.

EDIT: It seems that after I had tried manually installing flash first that the flashplugin-nonfree installed quite rapidly. It finished in about two minutes versus the 30 it took with AbEx. My advice: manually install flash first (this will only install it for firefox, I believe) then install flashplugin-nonfree with apt-get or Synaptic.

---

