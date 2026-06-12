---
title: "C-Media CM6501B not working properly"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by vladk2k on 2006-12-05
**This has begun as a complaint, but the solution is generic to any kind of sound malfunction that cannot be explained otherwise. The synopsis is the same, for every chip that is "blacklisted" from grabbing the default position.**

I am not very deeply familiar with Linux (I can use it and can install simple things, also follow guides and such, but not recompile kernel or stuff like that). I have started using Ubuntu now, with 6.10 (Edgy Eft as I see it is called) and I'd like it very much, be it not for a problem with my audio card.

I have a [ASrock 939Dual-VSTA motherboard]("http://www.asrock.com/product/939Dual-VSTA.htm") which uses C-Media's CM6501B chip for 7.1 sound. Don't bother searching for it, [C-Media]("http://www.cmedia.com") does not have it on its website, but the chip exists nevertheless. Under MS Windows it is seen through a PCI 2 USB bridge of sorts, and it looks like it is on an emulated USB port or something (you will see what I mean below)
I tried following different guides, [especially this one]("http://www.ubuntuforums.org/showthread.php?t=205449"), which is quite comprehensive, but I still cannot get it to work correctly. Here are some outputs:
```
vladk2k@AthlonuXP:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```And here it is on the USB list:
```
vladk2k@AthlonuXP:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0d8c:0201 C-Media Electronics, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:00e3 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
``` (the other thing is a the dual receiver for my keyboard and mouse)
Also, if I go to System -> Preferences -> Sound, I can put "USB audio" for everything on the "Devices" tab (and pressing Test results in the correct tone being played), but on the Sounds tab I can select only PnP Audio Device for the sound card and testing the Login/Logout sounds yields no sound.

I have installed XMMS. Initially, I got error messages whenever I tried to play a sound, but I got rid of them (and actually got to play some music) by going to XMMS's preferences and for the ouput plugin i have "ALSA 1.2.10 output plugin [libALSA.so]", which i configured to use not "default PCM device", but "PnP Audio device (USB audio)". It works and I can hear music only from the front two speakers (I have a 4.1 setup). Problem is, the system setting for the mixer (clicking the little speaker near the clock) doesn't seem to affect the output.
*As far as my experience with MS Windows goes, leaving default means XMMS uses the system setting for audio card, and putting something else forces output to the given card (if I have more and want to listen music only on one of them, irrespective of the system setting), so I guess the problem is the default card for alsa.*
Ok, so the music plays, and also I can hear myself blowing in the micrphone if I unmute it. so, presumably, this should work too:
```
vladk2k@AthlonuXP:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```But, this works:```
vladk2k@AthlonuXP:~$ alsamixer -c1
```I also just got this message, if I run *aplay* without the *-l*:
```
vladk2k@AthlonuXP:~$ aplay
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:547: audio open error: No such device
```The only thing I can imagine is that my card is recognized as card 1 (see *aplay -l* above) and the system is configured to default to card 0. Do you know how can I determine if this is the case and how to change it?

---

### Post by vladk2k on 2006-12-09
Okay, after much digging and probing ("thanks" everybody for helpful advices - :mad: ) I found out that, in fact, Ubuntu prevents USB audio from becoming device 0:
```
vladk2k@AthlonuXP:~$ sudo nano /etc/modprobe.d/alsa-base
```
And we have right at the end:
```
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

```
As you can see, you just have to put your specific soundcard as index=0 (in my case, it was snd-usb-audio). Now everything works yay

---

### Post by diebels on 2007-03-27
=D> Thanks a lot!

Now I have great x-fi sound on my laptop with the creative xmod.

:)

---

### Post by Dave in Tempe on 2007-04-23
I changed "options snd-usb-audio index=-2"  to "options snd-usb-audio index=0" and it didn't work for me with my xmod.  Did you do anything else?  (RIght now the volume knob on my xmod works--I can adjust the volume and mute with it, but the sound still goes to my laptop speakers rather than the line-out jack on the xmod).

---

### Post by capran on 2007-04-30
I just got mine to work. I did the preceding, but it still wasn't working, and the volume light on the Xmod wasn't lit. So I tried unplugging it and then replugging it, and the light came on! And lo and behold, if you set ALSA as the playback device under Preferences/Sound devices, it works!

Only thing is, the volume knob/button doesn't actually work. All it does it bring up a pop-up volume slider on the screen, but it doesn't actually change the volume or mute/unmute.

> **Dave in Tempe said:**
> I changed "options snd-usb-audio index=-2"  to "options snd-usb-audio index=0" and it didn't work for me with my xmod.  Did you do anything else?  (RIght now the volume knob on my xmod works--I can adjust the volume and mute with it, but the sound still goes to my laptop speakers rather than the line-out jack on the xmod).

---

### Post by capran on 2007-05-01
Hmm. Reboot and I have to unplug/replug the Xmod again to get sound.

Also, it seems there's no audio mixer for the system, whatever app uses sound gets control and nothing else can make sound. I had Gaim open, then I openned firefox and went to Youtube, video and sound plays, but now I get no sound from Gaim. Can I fix this?

---

### Post by nicors on 2007-05-10
Hello
Thanks for your post because was a great start point to solve my sound problems whit my c-media onboard sound card. I also solved the problem with the mixer. Reading on other posts I've seen similar problems and in one of them find this workarround that solved the problem. The problem seems to be that file /etc/asound.conf does not exist. I created as follows:

 /etc/asound.conf

```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
```
}

After this the mixer started to work. Now I can play two music files without problems. Maybe you need edit the line "pcm "hw:0,0" " depending on your hardware. 0,0 worked for me. If this works you only need to select the default mixer channel (for volume buttons on keyboard if any). In my case was speaker 2.

---

### Post by nicors on 2007-05-11
Hi again
I made a mistake on the file, the one that worked for me was 


/etc/asound.conf

```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:1,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}
```

Observe the line pcm "hw:1,0". THIS values worked for me... I guess It's time to go bed.... 
Sorry

---

### Post by tatadeluxe on 2007-10-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/122896](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/122896) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Change
> options snd-usb-audio index=-2
to > 
options snd-usb-audio index=0

Solved the problem
In my case, create /etc/asound.conf is not necessary.

Thanks

---

### Post by daxm on 2007-10-21
In case anyone else has an Asus M2N-SLI-E motherboard with the c-media onboard sound I got it to work by using your asound.conf file and by setting "options snd-usb-usx2y index=0" instead of the snd-usb-audio in the alsa-base file.

Thanks for the lead!  I've spent far too long trying to get something as simple as sound working (especially since Ubuntu 7.10 even recognized my soundcard).

:guitar:

---

### Post by silentsunami on 2007-10-22
i'm using asus m2n-e sli motherboard, finally found a solution for my problem. i missed the ubuntu login sound for so long and now it's back. thank you very much

---

### Post by bve on 2008-04-04
So did anyone actually get S/PDIF output too?

I already have sound on 2 channel in every vid app. xine, mplayer, vlc - however all I seem to have is 2 channel.

---

### Post by bve on 2008-04-04
> **daxm said:**
> In case anyone else has an Asus M2N-SLI-E motherboard with the c-media onboard sound I got it to work by using your asound.conf file and by setting "options snd-usb-usx2y index=0" instead of the snd-usb-audio in the alsa-base file.

Thanks for the lead!  I've spent far too long trying to get something as simple as sound working (especially since Ubuntu 7.10 even recognized my soundcard).

:guitar:

Did this give you the full 8 channel audio like the card is capable of?

---

### Post by MartinuxP on 2008-04-27
I've got the same sound card, this solution activate che analog output, but no digital out :( why? :(

---

