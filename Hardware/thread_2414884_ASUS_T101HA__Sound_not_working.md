---
title: "ASUS T101HA : Sound not working"
date: 2019-03-16
forum: Hardware
---

### Post by magikstiix on 2019-03-16
Hi !

After many research on the internet, I still cannot get my audio to work.
I tried many things : deleting .config/pulse, giving proper chown, purge / reinstall pulseaudio, modifing default.pa...
The only time was when I used another kernel : [https://ubuntuforums.org/showthread.php?t=2254322&page=132&p=13595504#post13595504](https://ubuntuforums.org/showthread.php?t=2254322&page=132&p=13595504#post13595504)
But sadly, my sound was working, but my Wifi wasn't and my touchpad was horrible...

At the moment, when I try to launch PulseAudio : Connection to PulseAudio Failed ...
When I use start-pulseaudio-x11 I get : 
Échec lors de la connexion : Connexion refusée
Échec de pa_context_connect() : Connexion refusée

(I'm french yeah, but It says : Connection denied)

I can find my sound card in alsamixer, and it get detected with lspci

Can I get some help pls ?
Thanks in advance.

My config :
Asus T101HA GR005T
Ubuntu 18.04.1 LTS

---

### Post by him610 on 2019-03-16
Welcome to the Forums.
I am not familiar with the ASUS T101HA, but I do own some Asus equipment. Maybe someone else will offer some suggestions.

Please show the results, between the code tags, of ***inxi -F***

---

### Post by magikstiix on 2019-03-17
```
magik@magik-T101HA:~$ inxi -F
System:    Host: magik-T101HA Kernel: 4.15.0-45-generic x86_64 bits: 64
           Desktop: Xfce 4.12.3 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: ASUSTeK product: T101HA v: 1.0 serial: N/A
           Mobo: ASUSTeK model: T101HA v: 1.0 serial: N/A
           UEFI: American Megatrends v: T101HA.203 date: 07/15/2016
Battery    BATC: charge: 21.9 Wh 84.4% condition: 26.0/31.6 Wh (82%)
CPU:       Quad core Intel Atom x5-Z8350 (-MCP-) cache: 1024 KB
           clock speeds: max: 1920 MHz 1: 902 MHz 2: 952 MHz 3: 480 MHz
           4: 480 MHz
Graphics:  Card: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 800x1280@60.10hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics (Cherrytrail)
           version: 4.5 Mesa 18.0.5
Audio:     Card-1 Intel HDMI/DP LPE Audio driver: HdmiLpeAudio
           Card-2 chtrt5645 driver: chtrt5645
           Sound: Advanced Linux Sound Architecture v: k4.15.0-45-generic
Network:   Card: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter
           driver: ath10k_pci
           IF: wlp1s0 state: up mac: 74:c6:3b:b7:59:0d
Drives:    HDD Total Size: NA (-)
           ID-1: /dev/mmcblk0 model: N/A size: 125.1GB
Partition: ID-1: / size: 113G used: 15G (14%) fs: ext4 dev: /dev/dm-0
           ID-2: swap-1 size: 1.02GB used: 0.00GB (0%)
           fs: swap dev: /dev/dm-1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 214 Uptime: 2 min Memory: 738.8/1825.3MB
           Client: Shell (bash) inxi: 2.3.56 


```

Here is what you asked for !

---

### Post by him610 on 2019-03-17
well magikstix,
Your system has two audio cards...
```
Audio:     Card-1 Intel HDMI/DP LPE Audio driver: HdmiLpeAudio
           Card-2 chtrt5645 driver: chtrt5645
           Sound: Advanced Linux Sound Architecture v: k4.15.0-45-generic 
```
Try *alsamixer* from the command line; it is a good utility to adjust sound settings. 
Is your wifi and touchpad working properly now?

This issue sounds similar to yours, [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1772891]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1772891")

---

### Post by magikstiix on 2019-03-17
It worked until the next reboot and I can't get it to work again. PulseAudio seams to be the problem. 
I can't adjust the sound of my "HdmiLpeAudio" using Alsamixer (maybe because I don't have any output connected to the hdmi port)

And yes, when I switched back to the "4.15.0-45-generic" kernel, my wifi and touchpad worked again. 

I just can't understand why PulseAudio work without problem on the other kernel (link in my first message) but doesn't work on the generic linux one.
Is there any alternative to PulseAudio to work with ?

Thanks.

PS : In the issue you linked, the guy already got it working before the update. In my case, PulseAudio never worked at all.

---

