---
title: "Sound - modprobe works, but doesn't load card at boot"
date: 2004-10-31
forum: Hardware &amp; Laptops
---

### Post by taygan on 2004-10-31
Thinkpad 600, I do not have tpctl loaded if that makes a difference.

boot parameters: *ro quiet splash acpi=force pci=noacpi pnpbios=off*

when I modprobe sound works, and all the modules load (no oss problems)
*sudo modprobe  snd-cs4236 port=0x530 cport=0x538 irq=5 dma=1 dma2=0 isapnp=0*

I added the following to /etc/modutils/alsa-base and then ran *sudo modules-update:*

# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-cs4236
# module options should go here

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
	
# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

options snd major=116 cards_limit=1
options snd-cs4236 port=0x530 cport=0x538 isapnp=0 dma1=1 dma2=0 irq=5



I can logout and then log back in and then the gnome volume starts working (before logging out only alsamixer could control the volume)

But when I reboot my system can't detect the soundcard (hence the port specifications) so I get *alsactl: load state 1134: no soundcard found*.  What else can I do to get this to load at boot?

Thanks.

---

### Post by taygan on 2004-10-31
If I add *snd-cs4236 port=0x530 cport=0x538 irq=5 dma=1 dma2=0 isapnp=0* to the /etc/modules (in addition to modules.conf) file I avoid the boot problem, but then sound just loops at the boot sound and I have to drop into the the terminal to shutdown.

---

### Post by taygan on 2004-10-31
I'm still trying..  If I edit /etc/modules to just say snd-cs4236 (without options) I load all the sound modules except for the snd-cs4236 module..  Boot runs fine but still no sound..

snd_opl3_lib            9728  0
snd_hwdep               9120  1 snd_opl3_lib
snd_cs4236_lib         16000  0
snd_mpu401_uart         7296  0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  2 snd_opl3_lib,snd_rawmidi
snd_cs4231_lib         24960  1 snd_cs4236_lib
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  3 snd_cs4236_lib,snd_cs4231_lib,snd_pcm_oss
snd_timer              23172  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd                    50660  11 snd_opl3_lib,snd_hwdep,snd_cs4236_lib,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc         11144  2 snd_cs4231_lib,snd_pcm

---

### Post by wolfchri on 2005-03-15
Hello Taygan,

your lsmod shows *exactly* the same result as on my Thinkpad600 - but i do net get the snd-cs4236 loaded, no matter what or how I try.  It keeps saying "no such device". 

pnpdump shows no devices at all - how did you get the thing working? Did you compile tpctl sources? Did you change your BIOS setup somehow? 

Thank you a lot!

---

### Post by arivera on 2007-03-14
Taygan/Wolfchri:

For Ubuntu 6.10, I edited the /etc/modprobe.d/oss-compat file by adding "&& modprobe snd-cs4236" as follows:

install snd modprobe --ignore-install snd **&& modprobe snd-cs4236** && modprobe snd-seq-oss && modprobe snd-mixer-oss && modprobe snd-pcm-oss

Upon reboot, sound works as espected. Best regards!

---

