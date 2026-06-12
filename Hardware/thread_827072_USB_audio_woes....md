---
title: "USB audio woes..."
date: 2008-06-12
forum: Hardware
---

### Post by Optical on 2008-06-12
I've got a Microsoft LifeChat LX-3000 USB Headset (A lot of people seem to have trouble with this particular headset, could it be because it's microsoft?), and unfortunately most programs will not use it. Instead it uses my laptop's onboard speakers, which of course are painfully low quality. When I plug it into the USB port it plays that crazy New Age music clip out of it, and Mplayer will play audio files, but nothing else will use it. I'd really like to use it in firefox, VLC, and Amarok, but none of these programs will recognize it. 

Some of the things I've tried to get the Headset to work...

System-->Preferences-->Sound Changing everything to USB audio.

In the terminal: asoundconf set-default-card default (Somewhere along the way, I've renamed my USB audio to "Default")

A program called "asoundconf-gtk" which apparently is suppose to switch the default soundcard.

I tried going into the VLC preferences-->ALSA-->ALSA Device Name--> and changing it to the USB headset, but it continues to play audio out of the speakers.


I'm running ubuntu 8.04.

One time  I actually got it to work, somehow by doing something in the terminal I got every program to use the USB headset, after a pop-up window in the right-hand corner told me to do it (I think it was the "asoundconf set-default-card default thing), but when I rebooted the computer it went back to using only the laptop speakers in everything except for mplayer.

Any thoughts?

---

### Post by PAFin on 2008-06-13
I have the same problem with a Phillips usb audio mini system.  It works for system sounds but VLC, Kaffeine, and Firefox don't work with it.  I have one success because the Totem Movie Player does work with the USB audio.  I have tried every configuration of the audio settings for the other programs but still no luck.  Why does Ubuntu pick and choose which applications will use the usb audio?

---

### Post by Optical on 2008-06-16
bump...

---

### Post by ukripper on 2008-06-16
> **Optical said:**
> I've got a Microsoft LifeChat LX-3000 USB Headset (A lot of people seem to have trouble with this particular headset, could it be because it's microsoft?), and unfortunately most programs will not use it. Instead it uses my laptop's onboard speakers, which of course are painfully low quality. When I plug it into the USB port it plays that crazy New Age music clip out of it, and Mplayer will play audio files, but nothing else will use it. I'd really like to use it in firefox, VLC, and Amarok, but none of these programs will recognize it. 

Some of the things I've tried to get the Headset to work...

System-->Preferences-->Sound Changing everything to USB audio.

In the terminal: asoundconf set-default-card default (Somewhere along the way, I've renamed my USB audio to "Default")

A program called "asoundconf-gtk" which apparently is suppose to switch the default soundcard.

I tried going into the VLC preferences-->ALSA-->ALSA Device Name--> and changing it to the USB headset, but it continues to play audio out of the speakers.


I'm running ubuntu 8.04.

One time  I actually got it to work, somehow by doing something in the terminal I got every program to use the USB headset, after a pop-up window in the right-hand corner told me to do it (I think it was the "asoundconf set-default-card default thing), but when I rebooted the computer it went back to using only the laptop speakers in everything except for mplayer.

Any thoughts?

It should have worked when you set it to default using asoundconf.

Not sure if this thread can help in anyway - [http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

---

### Post by Optical on 2008-06-16
I think that I'm just going to reinstall ubuntu and see if that can help me fix things... I've got a feeling that I've screwed something up somewhere because I've tried so many things. The fact that I got it to work one time means that there has to be a solution, it's just that I don't know what I've done to prevent it from working again. Maybe along the way I can fix other obnoxious problems like ubuntu always setting the system clock one hour ahead...

Luckily, I don't have much of anything on my linux partition, everything I care about is on my vista partition.

---

### Post by ukripper on 2008-06-16
> **Optical said:**
> 

Luckily, I don't have much of anything on my linux partition, everything I care about is on my vista partition.


I just got the opposite. Everything safe and secure on ubuntu and almost nothing on vista.

---

### Post by Optical on 2008-06-19
Well, just as I was about to burn a CD to install ubuntu with I installed a bunch of patches and now everything uses USB like I want it to. I noticed that to get VLC to use the USB headset I had to set it to "Default" instead of "Microsoft Lifechat..." in  preferences --> audio --> ALSA. Also everything under "Sound Preferences" is set to ALSA, except the first one which is set to ASLA (custom). As opposed to "USB audio"

Well, it works, and that's all I care about. Although I have gotten it to work before, and it has stopped working again shortly afterwards...

---

### Post by ukripper on 2008-06-20
Not quiet sure why it is not working for you. I have wireless usb phone for my skype and i use it everyday without any problem and also play music using my speakers or headset connected via soundcard when i am not using skype with no problem.

---

### Post by mikecar52 on 2008-10-22
> **ukripper said:**
> Not quiet sure why it is not working for you. I have wireless usb phone for my skype and i use it everyday without any problem and also play music using my speakers or headset connected via soundcard when i am not using skype with no problem.
Please explain how then

---

### Post by harmeet on 2008-10-23
I just fixed my YouTube USB sound following this -

[http://hajuria.blogspot.com/2008/10/fixed-firefox-youtube-no-sound.html](http://hajuria.blogspot.com/2008/10/fixed-firefox-youtube-no-sound.html)

---

