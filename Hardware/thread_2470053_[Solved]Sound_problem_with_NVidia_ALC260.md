---
title: "[Solved]Sound problem with NVidia ALC260"
date: 2021-12-18
forum: Hardware
---

### Post by juha-karmala on 2021-12-18
[INDENT] 		I upgraded Ubuntu to my fathers PC.  He had 20.10 originally and I  tried installing first 21.04 and then  20.04LTS, but these both had same  problem with sounds.

He always had this weird crackling sound when system was booting up, but   it stopped as soon as DE was fully loaded and sounds worked fine. Now the   same happens, but the crackling sound ends earlier and sounds  dissapear  all the way after that. I have noticed that by installing   Pavucontrol  you can choose current profile for the sounds from settings  and it  works, but soon as you close pavucontrol-qt the crackling  starts again  and soon drops all the sounds. Also if you keep playing  some sounds the  sounds do work fine, but soon as there is no sounds  activity the  crackling starts and sounds die. So as long as you keep  some kind of sounds  up or pavucontrol-qt on everything works good. So I  added  pavucontrol-qt to autostart on boot and I or my father has to  choose the  current profile every time he boots up the system and then he  minimizes  the pavucontrol-qt to keep it on.

I'm working on some kind of script to male it more convenient, so that   there would be no need to manually do anything. (till  the main problem   is solved)



**Here is some possible useful information about the system:**

Inxi:

 	```
lasse@lasse-ubuntu:~$ inxi -SMA
System:
  Host: lasse-ubuntu Kernel: 5.11.0-37-generic x86_64 bits: 64
  Desktop: GNOME 3.38.4 Distro: Ubuntu 21.04 (Hirsute Hippo)
Machine:
  Type: Unknown System: FUJITSU SIEMENS product: ESPRIMO P v: N/A
  serial: <superuser required>
  Mobo: FUJITSU SIEMENS model: D2461-A2 v: S26361-D2461-A2
  serial: <superuser required> BIOS: FUJITSU SIEMENS // Phoenix
  v: 6.00 R1.15.2461.A2 date: 10/22/2007
Audio:
  Device-1: NVIDIA MCP51 High Definition Audio driver: snd_hda_intel
  Device-2: AMD RV620 HDMI Audio [Radeon HD 3450/3470/3550/3570]
  driver: snd_hda_intel
  Sound Server: ALSA v: k5.11.0-37-generic
```  


Alsa-resore.service:

 	```
lasse@lasse-ubuntu:~$ systemctl status alsa-restore.service
&#9679; alsa-restore.service - Save/Restore Sound Card State
     Loaded: loaded (/lib/systemd/system/alsa-restore.service; static)
     Active: active (exited) since Mon 2021-10-11 20:25:40 EEST; 16h ago
       Docs: man:alsactl(1)
   Main PID: 744 (code=exited, status=0/SUCCESS)
      Tasks: 0 (limit: 3500)
     Memory: 0B
     CGroup: /system.slice/alsa-restore.service

loka 11 20:25:40 lasse-ubuntu systemd[1]: Starting Save/Restore Sound Card Stat>
loka 11 20:25:40 lasse-ubuntu systemd[1]: Finished Save/Restore Sound Card Stat>
```  


Aplay:

 	```
lasse@lasse-ubuntu:~$ aplay -l
**** Luettelo PLAYBACK laitteista ****
kortti 0: NVidia [HDA NVidia], laite 0: ALC260 Analog [ALC260 Analog]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 1: HDMI [HDA ATI HDMI], laite 3: HDMI 0 [HDMI 0]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
``` 


Lsmod:

 	```
lasse@lasse-ubuntu:~$ lsmod | grep snd_hda_intel
snd_hda_intel          53248  2
snd_intel_dspcfg       28672  1 snd_hda_intel
snd_hda_codec         147456  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_i  ntel,snd_hda_codec_realtek
snd_hda_core           94208  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_i  ntel,snd_hda_codec,snd_hda_codec_realtek
snd_pcm               118784  8  snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,sou   ndwire_intel,snd_compress,snd_soc_core,snd_hda_cor  e,snd_pcm_dmaengine
snd                    94208  17  snd_hda_codec_generic,snd_seq,snd_seq_device,snd_h   da_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_code   c,snd_hda_codec_realtek,snd_timer,snd_compress,snd   _soc_core,snd_pcm,snd_rawmidi
``` 



**Steps I've taken this far:**

Reinstalled alsa drivers and pulseaudio:

 	```
lasse@lasse-ubuntu:~$ sudo apt-get install --reinstall alsa-base pulseaudio
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu... Valmis
Luetaan tilatiedot... Valmis                  
0 päivitetty, 0 uutta asennusta, 2 uudelleen asennettua, 0 poistettavaa ja 0 päivittämätöntä.
Noudettavaa arkistoa 964 kt.
Toiminnon jälkeen käytetään 0  t lisää levytilaa.
Nouda:1 [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hirsute-updates/main amd64 pulseaudio amd64 1:14.2-1ubuntu1.1 [818 kB]
Nouda:2 [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hirsute/main amd64 alsa-base all 1.0.25+dfsg-0ubuntu7 [145 kB]
Noudettiin 964 kt ajassa 3s (366 kt/s)
(Luetaan tietokantaa... 162974 tiedostoa ja hakemistoa asennettu tällä hetkellä.)
Valmistaudutaan purkamaan .../pulseaudio_1%3a14.2-1ubuntu1.1_amd64.deb ...
Puretaan pulseaudio (1:14.2-1ubuntu1.1) version (1:14.2-1ubuntu1.1) päälle...
Valmistaudutaan purkamaan .../alsa-base_1.0.25+dfsg-0ubuntu7_all.deb ...
Puretaan alsa-base (1.0.25+dfsg-0ubuntu7) version (1.0.25+dfsg-0ubuntu7) päälle...
Tehdään asetuksia: alsa-base (1.0.25+dfsg-0ubuntu7) ...
Tehdään asetuksia: pulseaudio (1:14.2-1ubuntu1.1) ...
Käsitellään paketin man-db (2.9.4-2) liipaisimia...
Käsitellään paketin dbus (1.12.20-1ubuntu3) liipaisimia...
lasse@lasse-ubuntu:~$ sudo alsa force-reload
Unloading ALSA sound driver modules: snd-hda-codec-realtek  snd-hda-codec-generic snd-hda-codec-hdmi snd-hda-intel snd-intel-dspcfg  snd-hda-codec snd-hda-core snd-hwdep snd-soc-core snd-compress  snd-pcm-dmaengine snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi  snd-seq snd-seq-device snd-timer (failed: modules still loaded:  snd-hda-codec-realtek snd-hda-codec-generic snd-hda-codec-hdmi  snd-hda-intel snd-intel-dspcfg snd-hda-codec snd-hda-core snd-hwdep  snd-soc-core snd-compress snd-pcm-dmaengine snd-pcm snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-realtek  snd-hda-codec-generic snd-hda-codec-hdmi snd-hda-intel snd-intel-dspcfg  snd-hda-codec snd-hda-core snd-hwdep snd-soc-core snd-compress  snd-pcm-dmaengine snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi  snd-seq snd-seq-device snd-timer.
```  
Sounds stated working for little while till sound output was cut and crackling started and then sound driver dropped again.


I cleared pulseaudio settings:

 	```
rm -f ~/.config/pulse/*
sudo pkill pulseaudio
``` 
I installed pavucontrol-qt and changed 'dummy sound' to NVidia  profile.  Sounds started working till I closed pavucontrol-qt unless  music or  some sound was playing during closing of pavucontrol-qt. 	
[/INDENT]

---

### Post by juha-karmala on 2021-12-18
I just noticed that I posted my gathered information from the time whn I was trying to make it work with version 21.04. Here is an update for 20.04LTS.

```
lasse@lasse-ESPRIMO-P:~$ inxi -SMA
System:    Host: lasse-ESPRIMO-P Kernel: 5.11.0-43-generic x86_64 bits: 64 Console: tty 1 
           Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:   Type: Unknown System: FUJITSU SIEMENS product: ESPRIMO P v: N/A serial: <superuser/root required> 
           Mobo: FUJITSU SIEMENS model: D2461-A2 v: S26361-D2461-A2 serial: <superuser/root required> 
           BIOS: FUJITSU SIEMENS // Phoenix v: 6.00 R1.15.2461.A2 date: 10/22/2007 
Audio:     Device-1: NVIDIA MCP51 High Definition Audio driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD/ATI] RV620 HDMI Audio [Radeon HD 3450/3470/3550/3570] 
           driver: snd_hda_intel 
           Sound Server: ALSA v: k5.11.0-43-generic 


```

---

### Post by juha-karmala on 2022-01-10
I figured it out.
disabling module-suspend-on-idle in default.pa fixed it.

---

