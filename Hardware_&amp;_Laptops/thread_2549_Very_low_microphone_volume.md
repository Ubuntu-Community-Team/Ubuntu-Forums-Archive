---
title: "Very low microphone volume"
date: 2004-10-29
forum: Hardware &amp; Laptops
---

### Post by mflash on 2004-10-29
Hello,

First, many thanks for making such a great distro.

I'm trying to get a microphone to work properly with Ubuntu. It's a standard desktop microphone but the volume is always too low for practical use.

FYI, it works perfectly on the *other* operating system...

The soundcard is a C-Media CMI8738 (onboard audio).

Any ideas ???

Here's the output of amixer:

Simple mixer control 'Master',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 29 [94%]
  Front Right: Playback 29 [94%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 22 [71%] [on] Capture [off]
  Front Right: Playback 22 [71%] [on] Capture [off]
Simple mixer control 'Synth',0
  Capabilities: pvolume pswitch pswitch-joined cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 22 [71%] [on] Capture [off]
  Front Right: Playback 22 [71%] [on] Capture [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Line-In As Bass',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Line-In As Rear',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 22 [71%] [on] Capture [off]
  Front Right: Playback 22 [71%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined cvolume pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: Playback 0 - 31 Capture 0 - 7
  Mono: Playback 24 [77%] [on] Capture 5 [71%] [on]
Simple mixer control 'Mic As Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Boost',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 5V',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Copyright',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Monitor',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Phase Inverse',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Select',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Valid',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Loop',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 2 [67%]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 15
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Four Channel Mode',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

Thanks,

Marcelo

---

### Post by kamstrup on 2004-10-31
I admit! I didn't read the 3MB's of output! ;P

-- but have you tried messing around with the mixer settings you have acces to when rightclicking the volume-applet?

---

### Post by glmeece on 2004-11-01
I've not done a full install of Ubuntu yet, so take all this with a grain of salt...

At any rate, I wanted to try Skype with Ubuntu, and found that my microphone volume was so low as to be unusable.  I had to mess around quite a bit, but in my case I found one of the volume panels (ALSA?  or was it OSS? I dunno...) there was a "boost mic volume 24 Db" with the "mute" checkbox checked.  When I UN-checked it, my mic. volume was acceptable.  
:grin: 

HTH...

---

### Post by mflash on 2004-11-02
[QUOTE=kamstrup]I admit! I didn't read the 3MB's of output! ;P

-- but have you tried messing around with the mixer settings you have acces to when rightclicking the volume-applet?[/QUOTE]

Yes, every possible (sensible) combination... Nothing makes any difference, except the mic boost switch which does indeed boost the volume. But it's stil far from being usable.

And sorry about the long post, but I was hoping that someone would have the same sound chip and would recognize something wrong in my mixer settings.

Thanks anyway,

Marcelo

---

### Post by mercurus on 2004-11-03
I'm probably telling you things you already know, but ...

There are two panels to the Volume Control application, one for OSS device emulation and one for ALSA. Depending on Skype's input modules you will need to enable Mic Boost for one or both of these devices. I have a headset mic which I have setup with GNOME Meeting quite successfully with the ALSA configuration panel.

> Simple mixer control 'Mic Boost',0

I don't know, but I would imagine "0" is off, and "1" is on ... try and enable this ?

Otherwise, disable any other "Record" devices and see if that improves the volume.

Finally, explore other drivers for the device ... maybe a search of the ALSA project for suggestions on improving the recording level ?

---

### Post by PosTi85 on 2006-11-20
I have the same problem too... wating for fixes...

---

### Post by IamAcoconut on 2007-01-11
Same issue here!

---

### Post by amklinux on 2007-01-31
Well, I don't know if this is going to be useful. I'm using Dapper and my soundcard is VIA 8237. I had the same problem, and I solved it playing around with gnome-volume-control. Here's what I did:

- Go to Applications > Sound & Video > Volume Control (or type gnome-volume-control in a terminal). 
- Select Edit > Preferences. 
- Check "Mic Boost (+20dB)" and "Capture".
- Select the "Keys" tab and check "Mic boost".
- Play with the sliders in the "Capture" tab.

Hope that can help you.

amklinux.

---

### Post by redemptateur on 2007-02-01
I ve got the same problem. I've try to mute and unmute and check and uncheck everything in my volume control C-Media PCI CMI8738-MC6 and I've still a low recording sound.

Can someone help ?

Thx

---

### Post by paledread on 2007-03-18
A problem for me too.

I've tried both the on mobo cmi8738 chip, and a separate pci card with a cmi8738 chip on it. No usable microphone from either source, although other sound functions are fine.

This has been a problem for far too long, but how to fix it?

---

### Post by medomedo on 2007-04-17
Oops, this is riplicated post, but I can't find a delete post button so
Sorry again.


Same here.

I have waited for many ALSA version and tried several kernels and surely played around with kmix (Kubuntu Edgy and Feisty). The speakers works fine but the mic is somehow behaves like if its highly suppressed. So I have to use the 20db+ and to be very careful with the distance (nothing to hear OR too high and distorted). Although I am using the same settings for Skype and for Ekiga (Audio plugin: ALSA, device:Intel 82801DB-ICH4), Skype suffers no mic problems though Ekiga and Twinkle do.

I believe that if we can figure out why the mic works fine with skype but BAD in Ekiga and Twinkle we can solve the enigma.


Note: I have done my homework went through many howtos and mailinglists but nothing fixed it.

---

### Post by medomedo on 2007-04-17
Same here.

I have waited for many ALSA version and tried several kernels and surely played around with kmix (Kubuntu Edgy and Feisty). The speakers works fine but the mic is somehow behaves like if its highly suppressed. So I have to use the 20db+ booster and to be very careful with the distance (nothing to hear OR too high and distorted). Although I am using the same settings for Skype and for Ekiga/Twinkle (Audio plugin: ALSA, device:Intel 82801DB-ICH4), Skype suffers no mic problems though Ekiga and Twinkle do.

I believe that if we can figure out why the mic works fine with skype but BAD in Ekiga and Twinkle we can solve the enigma.


Note: I have done my homework went through many howtos and mailinglists but nothing fixed it.

---

### Post by aikiwaza on 2007-07-22
I didn't see many mentions as to the type of mic being used, so sorry if you already know this... and I apologize for the long post.

Professional (any mic not specifically made for the computer)  mics, both dynamic and condenser styles, have very low power outputs... somewhere around 1 millivolt I think.  The problem is that a sound card uses a high impedance level (often called line level, hence line in) Even though one of the ports shows a microphone or has mic in, it doesn't amplify the signal the way it would need to for a "normal" recording.  To fix this, again using an actual mic, you would need to get a pre amp for the microphone.  This would bump up the audio signal.  There are other alternatives too.  If sound quality isn't an issue then you can use a software program to do a digital pre amp, or boost the signal, though I don't know of any off hand for Ubuntu/linux.  It does degrade the sound quality but the output would still be good enough for general use.  Another option is an analog to digital cable.  I've never used one myself, but a friend has and says it works well.  This will change the analog signal from your mic and converts it to digital, usually plugging into a midi, serial, or usb port.  This would work for recording, but I'm not sure how it would work for voice communication.  

A PC mic is a little different.  Most of them use the higher impedance power so it is ready for your computer already and all the above doesn't apply.  

The other thing to check is your sound card.  I'm not certain about on board cards, but a fair percentage of audio cards actually have a pre amp chip for your mic in.  You may want to check the specs of your card to see if yours has one.  If it does there is sometimes a setting, or driver, that can be changed to boost the mic volume more.  These from my experience degrade the sound a bit, but vary in how much.  For voice communication and the such it's usually fine, however for recording it often falls short of my standards (though I have really high standards)

Sorry again for the long post but hopefully this helps someone. Good Luck

---

### Post by Sparky222B on 2007-08-01
[http://ubuntuforums.org/showthread.php?p=3118306](http://ubuntuforums.org/showthread.php?p=3118306)
This fixed it for me.

---

### Post by brigit on 2007-08-02
I had the same problem with unbuntu kunbuntu, and what ever i did wasn't really good enough to talk on skype which is part of the reason I bought a computer.
I did manage to get it working but always with the interferance.that was unill I ran automatix2 after running automatix2 to install the codexes ect it worked, just like that.
Maybe this could help some of you? Easyubuntu did not have the same effect.

---

### Post by zidkenu on 2008-06-22
Guys, there are too many issues with microphone capture volume: sound card driver, impedance, analog noise, volume gain+pre amp... do yourselves a favor, google "ubuntu USB Microphone Logitech/Plantronics/Rocketfish",  just reset sound capture source in alsamixer... Easy!--

---

### Post by luke16 on 2008-07-06
I have this problem with my cmedia pci CMI8768 chipset (sold as auzentech). I am using one of those soundmax soundbeam mics that came with my asus mb. I tried doing the mic boost, setting the mic capture all the way up, and setting mostly everything else to max. My mic can now record and I can understand most of what is said, but the volume is still way lower than what it should be and there are still some other apps such as skype where it needs to be even higher. Setting the sound capture to oss instead of alsa or pulse creates a humming noise, but the volume output is still about the same. With windows, the setting the mic boost on and the capture to full would really make the mic blair. Is there anyway to make mics even louder?

---

