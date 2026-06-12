---
title: "Soundblaster Live! 24-bit External USB Sound card"
date: 2008-05-20
forum: Hardware
---

### Post by wicky615 on 2008-05-20
I have a Sound Blaster live! 24-bit external USB sound card that I bought when my laptop's soundcard died.  It doesn't seem to be working properly.  I think this might be because my laptop's sound card was discovered instead.  When I tried switching to "USB Sound" in the sound options in ubuntu, I hear the test beep fine, but it won't play anything through the card otherwise.

Any help is appreciated.

---

### Post by kakyoism on 2008-05-20
I'm using the exact same soundcard and I solved my problem by
1. in preference->sound, set all devices to "pulseaudio", 
   and select the mixer device to your SBlive external.
2. install "pulseaudio" control interface, pavucontrol, from apt-get.
3. use pavucontrol, to set your default playback/recording sound device, you can configure your 5.1 surround using that as well; you can also open an application (media player) and then direct the audio stream to either your builtin soundcard or the external.

NOTE: the trick with the pavucontrol is that you have to right-click the device text-label to bring out the context-menu to do all the stuff, kinda confusing in the beginning.

hope this helps.

---

### Post by wicky615 on 2008-05-20
Alright, now I've got the sound working, but I still have no sound in Firefox, flash really.  Any help there?

---

### Post by kakyoism on 2008-05-21
sudo apt-get install libflashsupport

---

### Post by wicky615 on 2008-05-31
Alright.  Somthing is amiss.

I think because I have my onboard sound card on the laptop, it's been detected and is causing problems.  I get sound in totem and pidgin, but no sound in firefox/flash (I installed the flash library you suggested, no dice.) and no sound in VLC.  Halp!

---

### Post by Pirate on 2008-10-27
it doesnt work for me also,
i did first and second step but altough i set my default sound card sb , i get sound from my laptops built-in sound card and i cant set sound 5.1 with pavucontrol

---

### Post by juniperubu on 2008-11-02
Thanks, pavucontrol worked to help me select my external sound card.

Another pavucontrol hint (I'm using .9.6):
Play a video or sound clip in your application.  If it's not coming through your desired sound card, run pavucontrol.  The first tab, Playback, will show any current streams.  Right-click on the application name and select 'Move Stream...' and select your desired sound card.  Pavucontrol will remember and use the last selected sound card (sink) next time you run your application.

---

### Post by cignu on 2009-08-05
> **kakyoism said:**
> I'm using the exact same soundcard and I solved my problem by
1. in preference->sound, set all devices to "pulseaudio", 
   and select the mixer device to your SBlive external.
2. install "pulseaudio" control interface, pavucontrol, from apt-get.
3. use pavucontrol, to set your default playback/recording sound device, you can configure your 5.1 surround using that as well; you can also open an application (media player) and then direct the audio stream to either your builtin soundcard or the external.

NOTE: the trick with the pavucontrol is that you have to right-click the device text-label to bring out the context-menu to do all the stuff, kinda confusing in the beginning.

hope this helps.


thanks, it did the trick!
i own a toshiba portege m300, usb soundblaster live! and i use ubuntu 9.04

cignu

---

