---
title: "How to install nforce proprietary drivers on ubuntu"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by sc0rpi0n on 2005-08-18
I would like to install the nvidia provided drivers to improve audio performance, but afaik ubuntu use a different way from debian to handle modules. Anyone knows how to install them?

---

### Post by sc0rpi0n on 2005-08-19
nobody can help me?

---

### Post by tseliot on 2005-08-19
Download the drivers from this page:

[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp) 

I GUESS the installation of the drivers isn't much different from the one of nvidia graphic drivers. Read the README on the website.

---

### Post by sc0rpi0n on 2005-08-19
[QUOTE=tseliot]Download the drivers from this page:

[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp) 

I GUESS the installation of the drivers isn't much different from the one of nvidia graphic drivers. Read the README on the website.[/QUOTE]
 yes i've readed it, but i have to configure ubuntu to use the nvidia modules and in that documentation isn't written. :(

---

### Post by mo_x on 2005-08-19
I assume you have run the NFORCE installer and it went ok.

In the file /etc/hotplug/blacklist add the following:
```
snd_intel8x0
forcedeth
```
Create the file /etc/modprobe.d/nforce and put the following in it:
```
alias eth0 nvnet
alias sound-slot-0 nvsound
```

Now reboot and the nforce modules will be used. Remember that the nvsound module is for OSS so you have to change your applications to use OSS instead of ALSA.

Mo X.

---

### Post by sc0rpi0n on 2005-08-19
thank you very much. it worked

---

### Post by sc0rpi0n on 2005-08-22
now i have the problem to save the volume settings, so that they are restored when i reboot my ubuntu. Once again the instructions contained in nvidia help file aren't useful...

---

### Post by oxynaz on 2005-08-31
hi,

i followed the instructions.. sounds works, 

but same as before (when i was with the free sound driver)

= no center sound and no rear sound...

I launch nvmixer on "advance options" I checked "mic to center/lfe" and "line to surround LR" and "center and LFE"
On the "speaker" tab, i have it set to 5.1 speakers... but can t select "speaker wizard" and "surround settings"... is there a problem ?

by the way, I launch xmms, i set it to use OSS output, = i have only sound from LR front speakers, no center sound and no rear sound :(

How can I fix it to use correctly my 5.1 speakers ?

And is there a way to make "Kmix" work with the nvidia nforce driver ?


Please HELP ME cause i really need to have sound output from all my speakers...


ps the "information" tab from nvmixer report these values:
Nvidia product name: NForce Audio
Hardware model: nforce3
hardware rev: a2
audio driver version: 1.0-6
linux kernel version: 2.6.10
codec manufacturer; realtek
codec model: alc650
code capabilities: 1 codec, 6 channels

---

### Post by fourhead on 2005-11-04
Hello,

I'm afraid to say that this didn't work for me. On a server, I need the nvnet driver because the forcedeth driver causes a very slow upload to the server via Samba. I installed only the nvnet driver, and it loads and I can use it etc. I've added 'forcedeth' to /etc/hotplug/blacklist, and I also created /etc/modules.d/nforce with just 'alias eth0 nvnet' in it - but still, after rebooting BOTH modules are loaded and eth0 uses the forcedeth driver. How can that be?


Tom

---

