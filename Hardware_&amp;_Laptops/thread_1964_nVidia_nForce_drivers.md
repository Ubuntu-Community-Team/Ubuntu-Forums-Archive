---
title: "nVidia nForce drivers"
date: 2004-10-24
forum: Hardware &amp; Laptops
---

### Post by Dracontopes on 2004-10-24
I've installed the drivers from nvidia.com.

nvmixer command works, but everytime I reboot I have to set nvmixer all over again (speaker settings etc) It happened in Suse 9.1 also, never found a fix.. (I only had Suse for a week :))

---

### Post by ubuntu-geek on 2004-10-24
[QUOTE=Dracontopes]I've installed the drivers from nvidia.com.

nvmixer command works, but everytime I reboot I have to set nvmixer all over again (speaker settings etc) It happened in Suse 9.1 also, never found a fix.. (I only had Suse for a week :))[/QUOTE]
 Hi,

Actually the best way to install the drivers for nvidia to ensure everything works correctly.

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nividia-glx-config enable

Then do a reboot.

---

### Post by Dracontopes on 2004-10-24
[QUOTE=ubuntu-geek]Hi,

Actually the best way to install the drivers for nvidia to ensure everything works correctly.

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nividia-glx-config enable

Then do a reboot.[/QUOTE]
 Those are the drivers for the graphic cards, aren't they? Those are not the problem (because I have an ATI card). The problem is the nForce chipset drivers for my onboard soundcard (asus a7n8x del.)

---

### Post by ubuntu-geek on 2004-10-24
[QUOTE=Dracontopes]Those are the drivers for the graphic cards, aren't they? Those are not the problem (because I have an ATI card). The problem is the nForce chipset drivers for my onboard soundcard (asus a7n8x del.)[/QUOTE]  ah right mis-read the subject.. :oops:

---

### Post by claymore on 2004-10-25
Are you sure you need them in ubuntu?  Everything has been working right for me automatically with the install.

---

### Post by Rancoras on 2004-10-25
I have the same mobo and all is well here too.  Is there something specific that you need the nvmixer for?

---

### Post by Dracontopes on 2004-10-26
[QUOTE=Rancoras]I have the same mobo and all is well here too.  Is there something specific that you need the nvmixer for?[/QUOTE]
 I have a 4.1 speaker setup. The two rear speakers or not enabled by default, so I need to run nvmixer everytime I start ubuntu to enable them. Otherwise, I only have sound coming from my two front speakers. (and less bass etc)

---

### Post by Dracontopes on 2004-10-27
Nobody has this probem? Damn...

Okay, something else then, how do I remove the nForce drivers (note: NFORCE CHIPSET, not graphic driver) from my system so that I can use the ALSA drivers? (nvidia sound driver only suppors OSS, and I read somewhere that in ALSA you can enable the rear speakers in the volume control)

---

### Post by drunken-wallaby on 2004-10-29
[QUOTE=Dracontopes]Nobody has this probem? Damn...[/QUOTE]

i have the same problem too. i have a motherboard with nforce2 chip and a 5+1 speaker setup. surround sound "just worked" in the preview version of ubuntu. however, in the warty release it is not working at all. i don't want to install the drivers from nvidia because i know that i already HAD surround sound. 

anyone who knows how to solve this?

---

### Post by vishna on 2005-03-20
I have the same porblem with nvmixer, everytime I boot i have to re-set my configuration for 5.1 speakers (ubuntu warty 4.1)

on nvidia site there is sth like this, however i don't know how to make it work under ubuntu  :| 

> 
If your configuration file already contains an entry for the i810_audio, snd-intel8x0, or nvaudio drivers (open-source audio drivers that supports the nForce audio controller), that entry needs to be commented out with a # or removed:

# alias sound-slot-0 i810_audio

Add the following line to the configuration file:

alias sound-slot-0 nvsound

On some distributions, you may need to replace sound-slot-0 with snd-card-0.

If you wish to have nvmixer audio settings automatically restored each time the nvsound driver loads, add the following lines to the configuration file for 2.4 kernels:

post-install nvsound sleep 1; /usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1 ||:
pre-remove nvsound /usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 ||:

For 2.6 kernels:

install nvsound /sbin/modprobe --ignore-install nvsound ; sleep 1; /usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1 || :
remove nvsound { /usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove nvsound

For both 2.4 and 2.6 kernels, you should also edit /etc/rc.d/init.d/halt, or /etc/init.d/halt.local on SuSE distributions:

if grep -q "\(nvsound\)" /proc/modules && [ -x /usr/bin/nvmix-reg ]; then
/usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1
fi

For Red Hat Enterprise Linux 4 and Fedora Core 3, add the following line in /etc/rc.local:

/usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1 

---

### Post by cam8001 on 2005-07-22
If it makes you feel any better, this also happens in Windows. It's not a problem that is restricted to Ubuntu or even Linux.

---

