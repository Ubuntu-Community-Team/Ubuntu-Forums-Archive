---
title: "Hda intel"
date: 2008-11-08
forum: Hardware
---

### Post by holodila on 2008-11-08
I used kubuntu 8.04 for 2 months already. Everything worked perfect on my Sony vaio vgn-sz750n. Today, I have no sound. KMix didn't start at startup, and it also doesn't start manually.  When I open the sound settings, hda intel card appears to be turned off. Can anybody tell me what happened and how can I get the sound back?

---

### Post by Tom--d on 2008-11-08
In terminal, do this and then see if sound works after:
```
sudo modprobe snd-hda-intel
```

---

### Post by holodila on 2008-11-08
Here is the result
```
root@holodila-VAIO:/home/holodila# sudo modprobe snd-hda-intel
WARNING: /etc/modprobe.d/alsa-base.save line 3: ignoring bad line starting with '/sbin/modprobe'
WARNING: /etc/modprobe.d/alsa-base.save line 5: ignoring bad line starting with '/sbin/modprobe'
WARNING: /etc/modprobe.d/alsa-base.save line 7: ignoring bad line starting with '/sbin/modprobe'
WARNING: /etc/modprobe.d/alsa-base.save line 11: ignoring bad line starting with '--quiet'      
WARNING: /etc/modprobe.d/alsa-base.save line 12: ignoring bad line starting with '--ignore-install'
WARNING: /etc/modprobe.d/alsa-base.save line 14: ignoring bad line starting with '/sbin/modprobe'  
WARNING: /etc/modprobe.d/alsa-base.save line 15: ignoring bad line starting with '/sbin/modprobe'  
WARNING: /etc/modprobe.d/alsa-base.save line 16: ignoring bad line starting with 'snd-seq-midi'    
WARNING: /etc/modprobe.d/alsa-base.save line 17: ignoring bad line starting with 'snd-rawmidi'     
WARNING: /etc/modprobe.d/alsa-base.save line 18: ignoring bad line starting with '/sbin/modprobe'  
WARNING: /etc/modprobe.d/alsa-base.save line 21: ignoring bad line starting with '$CMDLINE_OPTS'   
WARNING: /etc/modprobe.d/alsa-base.save line 22: ignoring bad line starting with 'snd-via82xx'     
WARNING: /etc/modprobe.d/alsa-base.save line 23: ignoring bad line starting with '{'               
WARNING: /etc/modprobe.d/alsa-base.save line 28: ignoring bad line starting with '{'               
WARNING: /etc/modprobe.d/alsa-base.save line 34: ignoring bad line starting with 'snd-seq'         
WARNING: /etc/modprobe.d/alsa-base.save line 37: ignoring bad line starting with 'index=-2'        
WARNING: /etc/modprobe.d/alsa-base.save line 38: ignoring bad line starting with 'index=-2'
WARNING: /etc/modprobe.d/alsa-base.save line 39: ignoring bad line starting with 'index=-2'
WARNING: /etc/modprobe.d/alsa-base.save line 42: ignoring bad line starting with 'snd-hda-intel'
WARNING: /etc/modprobe.d/alsa-base.save line 43: ignoring bad line starting with 'model=vaio'
sh: Syntax error: end of file unexpected (expecting "}")
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: /etc/modprobe.d/alsa-base.save line 3: ignoring bad line starting with '/sbin/modprobe'
WARNING: /etc/modprobe.d/alsa-base.save line 5: ignoring bad line starting with '/sbin/modprobe'
WARNING: /etc/modprobe.d/alsa-base.save line 7: ignoring bad line starting with '/sbin/modprobe'
WARNING: /etc/modprobe.d/alsa-base.save line 11: ignoring bad line starting with '--quiet'
WARNING: /etc/modprobe.d/alsa-base.save line 12: ignoring bad line starting with '--ignore-install'
WARNING: /etc/modprobe.d/alsa-base.save line 14: ignoring bad line starting with '/sbin/modprobe'
WARNING: /etc/modprobe.d/alsa-base.save line 15: ignoring bad line starting with '/sbin/modprobe'
WARNING: /etc/modprobe.d/alsa-base.save line 16: ignoring bad line starting with 'snd-seq-midi'
WARNING: /etc/modprobe.d/alsa-base.save line 17: ignoring bad line starting with 'snd-rawmidi'
WARNING: /etc/modprobe.d/alsa-base.save line 18: ignoring bad line starting with '/sbin/modprobe'
WARNING: /etc/modprobe.d/alsa-base.save line 21: ignoring bad line starting with '$CMDLINE_OPTS'
WARNING: /etc/modprobe.d/alsa-base.save line 22: ignoring bad line starting with 'snd-via82xx'
WARNING: /etc/modprobe.d/alsa-base.save line 23: ignoring bad line starting with '{'
WARNING: /etc/modprobe.d/alsa-base.save line 28: ignoring bad line starting with '{'
WARNING: /etc/modprobe.d/alsa-base.save line 34: ignoring bad line starting with 'snd-seq'
WARNING: /etc/modprobe.d/alsa-base.save line 37: ignoring bad line starting with 'index=-2'
WARNING: /etc/modprobe.d/alsa-base.save line 38: ignoring bad line starting with 'index=-2'
WARNING: /etc/modprobe.d/alsa-base.save line 39: ignoring bad line starting with 'index=-2'
WARNING: /etc/modprobe.d/alsa-base.save line 42: ignoring bad line starting with 'snd-hda-intel'
WARNING: /etc/modprobe.d/alsa-base.save line 43: ignoring bad line starting with 'model=vaio'
sh: Syntax error: end of file unexpected (expecting "}")
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

### Post by holodila on 2008-11-08
BTW will the reinstall fix the problem? perhaps I have to install windows to fix it, and the installl kubuntu again?

---

### Post by holodila on 2008-11-12
Can't anybody help me out? :'(:'(:'(:'(:'(

---

### Post by dream_coder on 2008-11-12
if you edit/reduce asla-base to just this - if u need the shell command to type here "sudo kate /etc/modprobe.d/asla-base" on kubuntu and "sudo gedit /etc/modprobe.d/asla-base" on Ubuntu.)

options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

Then Reboot!

if that also fails try the hda-verb fix from [http://jan.saell.org/blog/archives/30](http://jan.saell.org/blog/archives/30)

good luck

---

