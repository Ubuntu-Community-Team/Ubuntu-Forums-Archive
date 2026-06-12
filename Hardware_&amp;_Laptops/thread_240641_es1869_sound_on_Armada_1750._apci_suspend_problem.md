---
title: "es1869 sound on Armada 1750. apci suspend problem"
date: 2006-08-21
forum: Hardware &amp; Laptops
---

### Post by segalion on 2006-08-21
The soundcard ess1869 fails when resume from suspend or hibernate state.

The sound works fine with alsa. I had to force configuration (not autodetected) with snd_es18xx module, and specific options (isapnp=0, enable=1, port=0x220, mpu_port=... and most important: dma1=1, dma2=0). 

I have an /etc/asound.conf specific file, /etc/esound/esd.conf file with "-d default" option, and default gstreamer-properties redirected to alsa.

The problem is when I make a suspend or hibernate, I loose the sound at resume, and all gnome works wrong (esd fails, and gnome speed go off, until "killall esd"). It make "dsp command kernel errors".

I can restore the sound manually reloading the module, but firts I have to kill all process open sound (i.e. mixer_aplet)
$lsof -t /dev/snd/* |kill -9
$sudo modprobe -r snd_es18xx
$sudo modprobe snd_es18xx

and sound works again

I´ve been reading the suspend and resume scripts and no sound module are reloaded, only alsa service are restarted in process. Seen the source of the module es18xx, I could see that it has power management options, and it is supposed the chip ess1869 to support suspend options.

I have revised bios options and appear the dma2 at channel 5 (not 0), and in the DSDT.aml patch (found at [http://acpi.sourceforge.net/dsdt/view.php?id=168]("http://acpi.sourceforge.net/dsdt/view.php?id=168")
) seems appears the same (dma 1 and dma 5). But if I configure dma2=5, sound work chopply. I dont know why. 
I have the same problems with all lastest dapper kernels.

Can anybody help me to make snd_es18xx work after resume without kill all apps opening sound? Thanks.

PD. All other things work fine with dapper, except 3D DRI with ATI rage. Im in process to fix it with the howto help at this forums.:)

---

