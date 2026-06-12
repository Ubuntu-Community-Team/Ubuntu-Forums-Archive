---
title: "Sound...I've tried it all...(except the soultion)"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by d1337 on 2005-08-02
I've spent quite a bit of time and have followed quite a few suggestions regarding my sound issue...which is a complete lack of.  I think that I may have it narrowed down to module issues as I get a good *pop* when restart ALSA.  The following will most likely be useful.

```
lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:08.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0a.0 Communication controller: Lucent Microelectronics LT WinModem (rev 02)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
```
and
```
lsmod | grep snd
snd_intel8x0           29984  0
snd_via82xx            25248  1
snd_ac97_codec         64608  2 snd_intel8x0,snd_via82xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  4 snd_intel8x0,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  3 snd_intel8x0,snd_via82xx,snd_pcm
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xxhttp://www.ubuntuforums.org/newthread.php?do=newthread&f=57#
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  12 snd_intel8x0,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  1 snd
```
and
```
/etc/alsa$ cat /etc/asound.conf
pcm.card0 {
type hw
card 0
}

pcm.!mixer {
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
}
```
and finally
```
/etc/esound$ cat esd.conf
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```



First a true newbie question, after a modprobe, how do I make it stick through the next boot?  I have restarted the hotplug system as instructed in one thread, but that didn't work.

As for what I've done, I have followed the [Unofficial Guide](http://ubuntuguide.org/#configuresoundproperly) as well as similar coding from other posts.  I have visited the ALSA page which suggested that the module snd_intel8x0 should work for most VIA82** and AC97 onboard chips, and I have also insured that snd_intel8x0m was blacklisted in /etc/hotplug/blacklist (this appears to be default Ubuntu install now due to a bug).    Nothing is muted in alsamixer (in fact they're all maxed which is likely to give me a heartattack when fixed)  This box is a dual boot with XP and all hardware seems to run well as my sound is great from XP.  I had vanilla Debian installed on this box before Ubuntu and didn't have any issues with sound.  Is this because of the mix of ESD, OSS and ALSA in the Ubuntu environment?  Never paid much attention to how things worked in Debian, as it gave me no troubles (for all I know it was mixed as well).

My box itself isn't anything special...AMD Sempron 2200+ that I bought bundled with a K7 M7VIG 400 mainboard...pretty run of the mill stuff (plus some frankenstein cards I had sitting around).  Just this dadgummed sound thing.  Any help would be appreciated, while I'll also keep digging.  If I find the solution, I'll share it directly for others to reference.

Thanks,
d1337

---

### Post by amohanty on 2005-08-02
> First a true newbie question, after a modprobe, how do I make it stick through the next boot?  

Add the desired module to /etc/modules at the end. Sometimes placemetn matters but in this case I dont think it will.

> Is this because of the mix of ESD, OSS and ALSA in the Ubuntu environment? 

No, I have all three setup and working, however I have a Audigy 2 zs and my onboard AC-97 audio is disabled in BIOS so it could be different.

Have you looked at this thread:
[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

Also try to install the latest alsa, I have 1.0.9.

Finally fire up alsamixer in the terminal or gamix or kmix and unmute everything and mute anything that says IEC...

HTH
AM

---

### Post by heimo on 2005-08-03
I have almost same audio chip. I have no snd_intel8x0 loaded, so try to *sudo rmmod snd_intel8x0 *At the end of /etc/hotplug/blacklist I have snd_intel8x0m

lspci | grep audio
```
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
``` 

I don't load sound modules explicitly (nothing for sound in /etc/modules).

lsmod | grep snd
 ```
snd_opl3_lib		   10624  0
snd_hwdep			   8896  1 snd_opl3_lib
snd_cs4236_lib		 15840  0
snd_cs4231_lib		 25312  1 snd_cs4236_lib
snd_mpu401			  6312  0
snd_seq_dummy		   3620  0
snd_seq_oss			33600  0
snd_seq_midi			9088  0
snd_seq_midi_event	  6848  2 snd_seq_oss,snd_seq_midi
snd_seq			 50736 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx			28608  2
gameport			   14824  3 ns558,snd_via82xx
snd_ac97_codec		 83452  1 snd_via82xx
snd_pcm_oss			52672  0
snd_mixer_oss		  19296  3 snd_pcm_oss
snd_pcm			 88840 5 snd_cs4236_lib,snd_cs4231_lib,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer			 24164 4 snd_opl3_lib,snd_cs4231_lib,snd_seq,snd_pcm
snd_page_alloc		 10600  3 snd_cs4231_lib,snd_via82xx,snd_pcm
snd_mpu401_uart		 7296  2 snd_mpu401,snd_via82xx
snd_rawmidi			24704  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device		 8460 6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd				 54884 16 snd_opl3_lib,snd_hwdep,snd_cs4236_lib,snd_cs4231_lib,snd_mpu401,snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore			   9600  5 sb_lib,sound,snd

```

Maybe editing /etc/modutils/alsa-base could help? (just a hunch, something I'd look at)

---

### Post by d1337 on 2005-08-03
[QUOTE=amohanty]Add the desired module to /etc/modules at the end. Sometimes placemetn matters but in this case I dont think it will.[/QUOTE]Thanks! 
[QUOTE=amohanty]
No, I have all three setup and working, however I have a Audigy 2 zs and my onboard AC-97 audio is disabled in BIOS so it could be different.

Have you looked at this thread:
[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)[/QUOTE]I have indeed seen that thread, but it seems to be something that I would do if I was getting sound, but still had some problems.  I will, however, try this when I get home tonight.  I may give in and scrap my modem or firewire card to make room for an SB Live! 24-bit if I can't resolve this.  For $30.00, it'd likely be worth it from the reported ease of install, compatibility and increased sound quality.
[QUOTE=amohanty]
Also try to install the latest alsa, I have 1.0.9.

Finally fire up alsamixer in the terminal or gamix or kmix and unmute everything and mute anything that says IEC...[/QUOTE]
I have the latest ALSA and I have muted/unmuted in many different combinations most of the settings in alsamixer with no luck (as suggested by another thread).
[QUOTE=amohanty]
HTH
AM
[/QUOTE]Thanks, to you and heimo both, for your replies.  Again, I will try tonight and post back with results.  I'd like to fix this (read:::not give up!).

---

### Post by d1337 on 2005-08-03
Not certain that I can pinpoint exactly what did it...but I've got sound!  And good sound at that.  Considering that it's onboard audio and a 3 piece inexpensive speaker system that I got bundled with a Dell, awesome bass and no static issues.  YAY!!

After everything that I tried yesterday, I followed the [POST](http://ubuntuforums.org/showthread.php?t=44753)  that was suggested by amohanty, to the tee, played with alsamixer some more and bingo.

Credit where credit is due, thanks to amohanty and heimo for response.  This forum/community is one factor that makes Ubuntu great.  Thanks, also, to intangible for his howto.

d1337

---

### Post by varunus on 2005-08-03
I think you'll be happy to know that Breezy will have this problem fixed (by following the howto, pretty much) by default.  So no more crazy asound.conf and esd.conf configuring.

---

