---
title: "not a peep - alsa ens1371"
date: 2005-01-11
forum: Hardware &amp; Laptops
---

### Post by fashions on 2005-01-11
your guidence would be g r e a t l y  appreciate!
have been enjoying ubuntu,  last to configure is the sound. 
no sound on the pc speaker even, not a peep from this machine.
if i run alsaconf: command not found
can you please review the info below and get me back on track.
I am looking forward to hearing the drums i've been reading about.:-)

Creative Sound Blaster Audio PCI64V pci card

Sound Driver:3.8.1a-980706 (ALSA v1.0.4 emulation code)
Kernel: Linux ...... 2.6.8.1-4-686-smp #1 SMP Sat Jan 8 20:21:53 UTC 2005 i686

$ lspci
0000:00:0f.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
_________________________________________

$ lsmod
 
snd_ens1371            25956  0
snd_rawmidi            25664  1 snd_ens1371
snd_seq_device          8296  1 snd_rawmidi
snd_pcm_oss            53864  0
snd_mixer_oss          19744  1 snd_pcm_oss
snd_pcm                99552  2 snd_ens1371,snd_pcm_oss
snd_page_alloc         11688  1 snd_pcm
snd_timer              26756  1 snd_pcm
snd_ac97_codec         68772  1 snd_ens1371
snd                    57828  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ac97_codec
soundcore              10688  1 snd
_____________________________________
/etc/modules.conf
### update-modules: start processing /etc/modutils/alsa-base
above snd-pcm snd-pcm-oss
### update-modules: end processing /etc/modutils/alsa-base
________________________________________
alias char-major-14 soundcore
___________________________________________
/etc/modprobe.d/isapnp/isapnp.aliases
# These aliases are used by /etc/hotplug/isapnp.rc and are needed here
# because the modules themselves are not providing them.
alias pnp:dPNP0800 pcspkr
________________________________________
/etc/modprobe.d/alsa-base
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && /sbin/modprobe snd-pcm-oss
______________________________________
/etc/modutils/alsa-base
above snd-pcm snd-pcm-oss
_______________________________________
_________________________
cat /var/log/kern.log |less
Jan 10 18:19:14 localhost kernel: input: PC Speaker
.......
Jan 10 18:19:14 localhost kernel: AC'97 0 does not respond - RESET
Jan 10 18:19:14 localhost kernel: AC'97 0 access is not valid [0xffffffff], removing mixer.
Jan 10 18:19:14 localhost kernel: ENS1371: probe of 0000:00:0f.0 failed with error -5
_____________________________________________
$ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.4 emulation code)
Kernel: Linux i40dtp 2.6.8.1-4-686-smp #1 SMP Sat Jan 8 20:21:53 UTC 2005 i686
Config options: 0
Installed drivers:
Type 10: ALSA emulation
Card config:
[B]--- no soundcards ---[/B
Audio devices: NOT ENABLED IN CONFIG
Synth devices: NOT ENABLED IN CONFIG
Midi devices: NOT ENABLED IN CONFIG
Timers:
7: system timer
Mixers: NOT ENABLED IN CONFIG
_______________________________
 $ cat /etc/hotplug/blacklist.d/alsa-base
........
es1370
es1371
sound
......
_______________________________
$ cat /etc/hotplug/blacklist
# added per boot errors 1/05
pciehp
shpchp
________________________


*looking forward to your post.*

---

### Post by fashions on 2005-01-17
*bump*

---

### Post by excelsior on 2005-02-05
I've had the same problem too, but only after upgrading the kernel.
Some help from the pros?

---

### Post by excelsior on 2005-02-05
I use the Ensoniq ES1371 [AudioPCI-97] too
I tried using modconf, but it says the driver is already installed!

---

### Post by cacofonix on 2005-02-05
I will get the most obvious question out of the way first. Have you checked the volume settings? 
[QUOTE=fashions]
your guidence would be g r e a t l y appreciate!
 have been enjoying ubuntu, last to configure is the sound. 
 no sound on the pc speaker even, not a peep from this machine.
 if i run alsaconf: command not found
 can you please review the info below and get me back on track.
 I am looking forward to hearing the drums i've been reading about.
[/QUOTE]
You may need to download alsa-utils and alsa-base if alsaconf can't be found.
```
 sudo apt-get install alsa-base alsa-utils 
```

After you have done that you should be able to run alsaconf, but by the looks of it the modules are loaded allready. Try running alsamixer and see if any of the channels are muted or turned down. 

cacofonix

---

### Post by malegria on 2005-02-05
You might have to install the latest drivers from ALSA and compile them to get your card working. You may have to. 

Also, one must always reinstall drivers when using a *new* kernel.

---

### Post by excelsior on 2005-02-07
[QUOTE=malegria]You might have to install the latest drivers from ALSA and compile them to get your card working. You may have to. 

Also, one must always reinstall drivers when using a *new* kernel.[/QUOTE]

Thanks!
I did what you said, but it didn't seem to work. Is there any way to check if i did it properly?

---

### Post by excelsior on 2005-02-08
I took the chicken way out, reinstalled ubuntu and now I have sound again! 
Guess i'll just make do with an outdated kernel

---

### Post by Shadow Skill on 2005-02-08
I am pretty much having the same problem I just got Ubuntu 64 installed and I have got jack for sound, I get this when I try to run alsa mixer ```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```  I have no clue where to even start since I can't launch any of the configuration tools.  I'm running an nforce4 ultra vnf Zenith amd socket 939 2.2ghz 3200+.  I am not using a pci sound card and am instead using what is present on the motherboard.  Looking on the ALSA site at the nforce chipset driver section the way I am reading this makes it sound like the driver is only good for intel based machines am I right? [I hope I am not otherwise I'll have to uninstall Ubuntu. :( ]

---

### Post by excelsior on 2005-02-08
Update: after reinstalling ubuntu and reupgrading the kernel, my sound works!!
Maybe you just have to reinstall the system, that's all?

---

### Post by macewan on 2005-02-08
[http://alsa.opensrc.org/](http://alsa.opensrc.org/) is a great source of information.
[http://alsa.opensrc.org/index.php?page=Quick+Install](http://alsa.opensrc.org/index.php?page=Quick+Install)

I had to download & compile latest alsa from the project page.

---

