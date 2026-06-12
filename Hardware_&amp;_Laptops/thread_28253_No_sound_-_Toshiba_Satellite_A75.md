---
title: "No sound - Toshiba Satellite A75"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by WiFi Net Guy on 2005-04-19
Hi, everyone. 

I have a Toshiba Satellite A75 and have just come over to the 'Ubuntu side' from SuSE Pro 9.2. I have just installed Hoary 5.4. Everything pretty much works fine, except for an annoying periodic lockup (for another thread), with the exception of not having ANY sound. I've tried all that I can think of, however, I'm pretty much a Linux newbie. So I probably don't even know what I don't know. I believe this is a line that describes my sound card from the output of lspci:

Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller

Thanks in advance for any help. Let me know what other information I can give.
 ](*,)

---

### Post by Vache on 2005-04-19
Yes, lspci will list all the PCI/onboard devices.

First, run **alsamixer** from the command line. Unmute anything you see, especially the PCM master volume.

Still no audio? Run **lsmod** and **dmesg**. What modules are loaded? Do you see any errors in dmesg? (dmesg will show you all the screen output that happens at boot)

---

### Post by WiFi Net Guy on 2005-04-19
[QUOTE=Vache]Yes, lspci will list all the PCI/onboard devices.

First, run **alsamixer** from the command line. Unmute anything you see, especially the PCM master volume.

Still no audio? Run **lsmod** and **dmesg**. What modules are loaded? Do you see any errors in dmesg? (dmesg will show you all the screen output that happens at boot)[/QUOTE]
 Vache,

Wow. Some nice reading there!  ;-)

Anyway, I don't want to cut and paste the entire output of lsmod and dmesg here, unless I should. There were some errors in dmesg but I don't know if they pertain to sound or not. How should I proceed?

---

### Post by Vache on 2005-04-19
In lsmod's output, do you see anything related alsa / snd_ / or oss?

---

### Post by Nano on 2005-04-19
Did you read this all?
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

Remember, "search" is always a good friend. :)

---

### Post by WiFi Net Guy on 2005-04-21
[QUOTE=Nano]Did you read this all?
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

Remember, "search" is always a good friend. :)[/QUOTE]
 Yes, Nano. I sure did. However, I still have NO sound whatsoever. 

Vache, here's the output from lsmod:

snd_atiixp_modem       15908  2
snd_atiixp             18596  0
snd_ac97_codec         64608  2 snd_atiixp_modem,snd_atiixp
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_p cm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  9 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_p cm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  3 snd_atiixp_modem,snd_atiixp,snd_pcm

Thanks in advance for any help.

---

