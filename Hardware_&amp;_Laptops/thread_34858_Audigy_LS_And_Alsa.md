---
title: "Audigy LS And Alsa"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by Xgates on 2005-05-16
I compiled the alsa-drivers src for my Audigy LS card, and then recompiled the kernel witbout alsa, just sound support as a module. Well now I have sound but when I reboot I'm getting this msg in the console:  

amixer: Mixer attach hw:0 error: no such file or directory 
* /etc/init.d/alsa: Warning : 'alsactl restore' failed with error message 'alsactl: load_state:1267: no soundcards found

I know in other distros with 2.6x you run --> generate modprobe.conf
So is there something like this that I need to do for this?, because when I run "lsmod"
it shows the module loaded at bootup:

snd_ca0106             26852  2
snd_ac97_codec      73848  1 snd_ca0106

By the way forgot to mention that I have 'alsa-utils' installed and there is no 'alsaconf' is the alsa-utils broke?

Thanks

---

### Post by l.tambiah on 2005-05-16
This is unusual i have an Audigy 2 ZS and it works fine, although sound didnt work when i first installed but this was only due to alsamixer being muted. Alsamixer runs in the terminal. I'm hearing 7.1 sound with no problems. 

Id suggest a reinstall from scratch and go from there, don tweak anything until you know you are sure you have tried the most obvious ways, like checking alsamixer for example.

---

### Post by Xgates on 2005-05-16
Ok my bad it looks like, I just did this setup in the Guide:

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

All looks well now, and I see that there is also no alsaconf in Ubuntu.

Thanks

---

### Post by Xgates on 2005-05-16
Nope I jumped the gun I rebooted for the 2nd time, and I got those error messages again.  :(

I need to BEAT my head --->  ](*,)

All I can think is do you run -->  'generate_modprobe.conf' in Ubuntu?

my /etc/modprobe.d/alsa-base file is outdated since I recompiled and might be the problems of my sound, and trying to figure how you go about updating it, at this point.

---

### Post by Xgates on 2005-05-17
Anyone know why I keep getting this in console at bootup:

amixer: Mixer attach hw:0 error: no such file or directory

---

