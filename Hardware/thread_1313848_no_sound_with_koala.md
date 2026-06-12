---
title: "no sound with koala"
date: 2009-11-04
forum: Hardware
---

### Post by mr.ivan on 2009-11-04
hello there,
few days ago i upgraded from jaunty to karmic. everything goes well except of sound.
with jaunty everything was ok, but koala remains silent no matter what i try... 
at first i thought it was problem with codecs as ogg files were played ok, but after installing ffmpeg, and other codec packcages there was no sound at all.

anyway problem is, that if i play any song or movie it looks like there is no problem, even alsa output meter is showing, that sound is played and speakers are in full use, but i can hear no sound at all.
i checked every volume setting i could find as rookie, but all volume settings were set to 100% . 

so i would really like to get any suggestions on my problem , thanks

btw i have asus X51L notebook with factory hardware...

---

### Post by mr.ivan on 2009-11-04
few hours later...  quick status brief

this is status after trying warious combinations of ideas and ggk /google gathered knowledge/ and after almost everything i again reloaded deafult karmic konfiguration...

alsa -- ok /tested for 5 hrs. now/
mic -- working fine
CD:
working only with KsCD , nothing else is able to give me some sound / every other aplication is working properly but without sound/
EVERITHING ELSE IS SILENT / without errors/ , all config files seem ok

so please if there is ANYBODY with ANY ideas i would really like to hear ANY opinions on this...  thanks for suggestions

---

### Post by mr.ivan on 2009-11-04
hey hey... again i cant fully understand what i just did...
 SOUND WORKS FINE
i tryed to stop alsa so i typed :

>> alsa unload
ivan@ivan-laptop:~$ sudo alsa unload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ivan/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 1423(slmodemd) 2895(kscd). 
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
ivan@ivan-laptop:~$ slmodem

so i tryed to stop all devices that are using alsa... and voila after removing sl-modem-daemon sound suddenly started to work properly / now when everything is working i only get some error message that sound is probably not working/kinda feels like windows ;)

 i would really like if someone could tell me what was wrong... also i think i should report this as bug as it was deafult karmic config...

---

### Post by Intel91 on 2009-11-04
All I know is smart link modem daemon = no sound. This can also be removed by accesing System>Administration>Hardware Drivers then uninstall Software Modem sl-modem-daemon.

---

### Post by Nausser on 2009-11-04
This did the trip for me as well. I was extremely baffled when I had no sound hardware showing up under sound preferences after upgrading to Koala from Jaunty. I unfortunately did a clean install and was happy to find my audio was then working. Of course after I spent all day re-installing all my beloved software codecs and add-ons, it of course disappeared and was not working again. I removed the software modem driver and the sound returned again. YAY! 

Other than this little hiccup, I absolutely love Koala! A job well done with it's fit and finish. The best release yet!!

Its the first release of Ubuntu that I didn't have to do any fancy configuring in the audio settings anywhere to get Skype to work correctly! Everything has simply worked. This is my experience on two laptops so far. An Acer TravelMate 2480(mine) and a Compaq Presario CQ50. The Presario had that nasty loud beep when shutting down and it wouldn't standby. Now everything works without a hitch with Karmic Koala.

Sorry to get off on a bit of a tangent there.

Thanks for the help!!

---

