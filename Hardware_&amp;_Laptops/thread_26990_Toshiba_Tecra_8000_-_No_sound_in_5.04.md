---
title: "Toshiba Tecra 8000 - No sound in 5.04"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by denyerec on 2005-04-14
Hi there,

Firstly, I am aware that there are many posts concerning this issue, I have resorted to posting here simply because I have attempted to follow them all, and failled.

Ok.

I have a Toshiba Tecra 8000 using a PCMCIA network adapter (Linksys). Sound on this laptop was working fine in Fedora Core3. I can't remember how I got it to work in FC3, but it was.

Taking a look at Ubuntu, I was seduced and installed Hoary5.04.

No sound.
I tried every method presented that I could find, and no luck.

So, I re-installed Fedora Core4. Sound did not work. More reading.
Eventually, I discovered if I edited /etc/pcmcia/config.opts  and added the line :

  exclude irq 5

Then at the console ran the following:

  modprobe snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530

Bingo! Working sound.

With this in mind I re-installed Ubuntu 5.04, edited the PCMCIA config to exclude IRQ5 and then ran the exact modprobe line that worked in Fedora.

Nothing but this error:

  Yamaha OPL3-SA soundcard no found or device busy
  FATAL: error inserting snd_opl3sa2 (path/to/lib): No such device
  FATAL: Error running install command for snd_opl3sa2

the dmesg output after running the modprobe command states:

  Yamaha OPL3-SA soundcard not found or device busy

When I shutdown the machine, some mixer software goes mental and posts about 20 errors before timing out and powering off. Unfortunately I can't read the errors before the machine shuts down and am unaware where to find them.

I really don't want to install Fedora again, but as my girlfriend demands the laptop makes sounds, unless someone has some more light to shed I'm stumped.

Any pointers would be appreciated,
Kind regards,
Distressed Denyerec

---

### Post by denyerec on 2005-04-16
Thanks to a chap called Jordz who helped me in a PM, sound on the Tecra is sorted!

Here's what happens, for Hoary 5.04:

I also got a clean install.
Here is what i did:

added this 2 lines in /etc/modutils/alsa-base
```
alias char-major-14 snd-pcm-oss
alias sound-slot-0 snd-card-0
```

Changed this line in /etc/modprobe.d/alsa-base

```
install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 && /lib/alsa/modprobe-post-install snd-opl3sa2
```

into this one:

```
install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530 && /lib/alsa/modprobe-post-install snd-opl3sa2
```

Check your bios settings for the irq/dma settings.

And added this in /etc/modules:
```
snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530
``` <--- its one long row!


The problem I have now is ESD causing sounds to be ungodly slow, but I'll figure that out soon Im sure...

Reboot and cross your fingers! Thankyou Jordz!

---

### Post by buellman on 2005-04-16
hi!

damn :-) i thought i could make my second (<-- [http://www.ubuntuforums.org/showthread.php?t=3047&highlight=tecra+8000](http://www.ubuntuforums.org/showthread.php?t=3047&highlight=tecra+8000)) "homerun" in posting how to setup sound on my tecra 8000. now you were faster :-D
anyway... here the way i get my sound back on a fresh hoary-final install :-)
-------
1.) sudo apt-get install esound-clients
2.) sudo mv /etc/modprobe.d/alsa-base /root <-- i did that because i felt that this file disturbed me from getting sound out of my tecra 8000. if denyerecs way is better, than pls tell me.
3.) sudo vi /etc/modprobe.d/tecra_sound
     # ALSA Configuration.
     alias snd-card-0 snd-opl3sa2

     # some stuff for the OSS drivers
     alias char-major-14 snd-pcm-oss
     alias sound-slot-0 snd-card-0

     # aliases for sound card #1
     alias sound-service-0-0 snd-mixer-oss
     alias sound-service-0-1 snd-seq-oss
     alias sound-service-0-3 snd-pcm-oss
     alias sound-service-0-8 snd-seq-oss
     alias sound-service-0-12 snd-pcm-oss
4.) sudo vi /etc/modules
     snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330
     port=0x538 sb_port=0x220 wss_port=0x530 <--- its one long row!
5.) refering to this link [http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567) i    
     only did:
     sudo apt-get install libesd-alsa0
6.) restart
7.) have fun :-D
-------
so... hope that help you guys and also i hope, i did not forget something, because i did many things to get this damn notebook to work with sound. but anyway: this should be everything you have to do :-)

greets. buellman

---

### Post by buellman on 2005-04-16
i wonder about something:
when i try denyerec method i have alsa and oss loaded... but with much to slow sound. my method only loads the alsa-modul but with normal speed of sound. if i look in the alsa-base file, i dont see anything related with oss... or am i blind? any ideas?

greets. buellman

---

### Post by denyerec on 2005-04-17
If you disable the GNOME sounds (System Settings -> Sound) which play sounds on events, it disabled the ESD server, I *think*

(I am certainly no expert!!)

Disabling this means the ALSA sound output can play at the normal speed, but means you can't use system sounds...

I've no idea which method is better, or why two modules end up loaded! If anyone wants to shed light onto it feel free  :smile:

---

### Post by amias on 2005-04-24
heres some notes on the sound chip used in the Tecra 8000:

<b>duplex<b><br>
/dev/dsp on these machines is not full duplex , if you want full duplex use
/dev/dsp to read and /dev/dspW to write. This is essential for SIP phones.
<br><br>
<b>mixer</b><br>
use /dev/mixer1 instead of /dev/mixer , for some reason the normal mixer
doesn't work . aumix -d /dev/mixer1 always works for me.
<br><br>
<b>permissions</b><br>
add users to the audio group to allow them to access the sound functions
sudo usermod -G audio user_name
<br><br>

---

### Post by pepax on 2005-05-19
Hi,
I have Toshiba 335CDS with probably the same soundcard. I made it work using the oss module: modprobe opl3sa2 mpu_io=0x330 io=0x370 mss_io=0x530 irq=5 dma=1 dma2=0. 
Denyerec, thanks for the advice on excluding irq 5, that was the key! :)
However, I haven't been successful with snd-opl3sa2 with the same values (taken from BIOS).
The good ole' error appears:
Yamaha OPL3-SA soundcard no found or device busy
FATAL: error inserting snd_opl3sa2 (path/to/lib): No such device
FATAL: Error running install command for snd_opl3sa2

So now I know the noise can be made :) but how to push it through ALSA?

---

### Post by fparri on 2006-07-04
Did any of you guys try these settings on a Dapper install? Did you have any success with getting the opl3sa2 chip working?

---

