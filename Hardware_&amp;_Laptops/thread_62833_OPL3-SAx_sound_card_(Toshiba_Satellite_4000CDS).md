---
title: "OPL3-SAx sound card (Toshiba Satellite 4000CDS)"
date: 2005-09-06
forum: Hardware &amp; Laptops
---

### Post by ZeNiTRaM on 2005-09-06
Hi, I installed Kubuntu two days ago, as I don't have much RAM (64mb :( ) I removed KDE and installed XFCE. But the sound doesn't work..

I've tried to follow this instructions [http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html) but it tells me to edit /etc/modules.conf and that file doesn't exist in Ubuntu! Someone told me to try to create it, but it didn't worked (probably because the instructions are for Warty).

What can I do?

---

### Post by az on 2005-09-06
From a terminal

sudo gedit /etc/modules

and add the word snd-opl3sa2 at the bottom of the list.  This will load the module each time you boot.

type 

sudo modprobe snd-opl3sa2

to load the module yourself (so that you do not have to reboot just to load the module)

---

### Post by ZeNiTRaM on 2005-09-06
I'm getting when I run modprobe:

FATAL: Error inserting snd_opl3sa2 (/lib/modules/2.6.10-5-686/kernel/sound/isa/snd-opl3sa2.ko): No such device
FATAL: Error running install command for snd_opl3sa2

P.S: I found this. I'm going to try it..

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Yamaha&card=UX256.&chip=YMF701%2C+YMF711%2C+YMF715%2C+YMF718%2C+YMF719%2C+OPL3+SA2%2C+OPL3+SA3&module=opl3-sa2](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Yamaha&card=UX256.&chip=YMF701%2C+YMF711%2C+YMF715%2C+YMF718%2C+YMF719%2C+OPL3+SA2%2C+OPL3+SA3&module=opl3-sa2)

---

### Post by ZeNiTRaM on 2005-09-06
[QUOTE=ZeNiTRaM]I'm getting when I run modprobe:

FATAL: Error inserting snd_opl3sa2 (/lib/modules/2.6.10-5-686/kernel/sound/isa/snd-opl3sa2.ko): No such device
FATAL: Error running install command for snd_opl3sa2

P.S: I found this. I'm going to try it..

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Yamaha&card=UX256.&chip=YMF701%2C+YMF711%2C+YMF715%2C+YMF718%2C+YMF719%2C+OPL3+SA2%2C+OPL3+SA3&module=opl3-sa2](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Yamaha&card=UX256.&chip=YMF701%2C+YMF711%2C+YMF715%2C+YMF718%2C+YMF719%2C+OPL3+SA2%2C+OPL3+SA3&module=opl3-sa2)[/QUOTE]
 I tryed to compile Alsa but it doesn't work, it says me that the module opl3sa2 doesn't exist..

Lspci doesn't report any sound card, alsamixer doesn't open.. the only sound I can produce is the beep that sounds when you just press backspace on xterm (with no command entered).

---

### Post by az on 2005-09-06
Try loading the opl3 module?

---

### Post by ZeNiTRaM on 2005-09-06
[QUOTE=azz]Try loading the opl3 module?[/QUOTE]
 The opl3 module loaded without errors but sound still doesn't work. Alsamixer says function snd_ctl_open failed for default: No such device

---

### Post by zorglub on 2005-09-07
Hi !

Got the same problem on my old Tecra 780DVD. The soundchip is the same than yours.

This thread solved my sound problem:

[http://ubuntuforums.org/showthread.php?t=32651](http://ubuntuforums.org/showthread.php?t=32651)

Maybe you'll have to use alsamixer to raise the sound because as far as I can remember the alsa settings were set to silent....

Hope this helps ;)

---

### Post by ZeNiTRaM on 2005-09-07
[QUOTE=zorglub]Hi !

Got the same problem on my old Tecra 780DVD. The soundchip is the same than yours.

This thread solved my sound problem:

[http://ubuntuforums.org/showthread.php?t=32651](http://ubuntuforums.org/showthread.php?t=32651)

Maybe you'll have to use alsamixer to raise the sound because as far as I can remember the alsa settings were set to silent....

Hope this helps ;)[/QUOTE]
 I've done these steps 100s of times... but it doesn't work.. it looks like as if there is no sound card.. but there is.

On boot, it says me it can't open some PCI device, could this be? (maybe it's the free PC-Card slot)

---

