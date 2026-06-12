---
title: "Sound and Video Problems on Laptop"
date: 2008-05-27
forum: Hardware
---

### Post by jacobh on 2008-05-27
Just installed Ubuntu a few hours ago, and I'm having trouble with both sound and video.

Sound:

- Speakers don't work, but headphones do (???)
   - to clarify: headphones work when i stream youtube or listen to internet radio for example. headphones also work when i do hardware testing (system --> administration --> hardware testing).
   - but rhytmbox won't play any files at all... just stays at 0:00
- Soundcard: Intel 8280 IG (ICH7), Realtek ALC880 Chipset (as far as I can determine)
- clicking the test icons under System --> Preferences --> Sound provides the following error message: 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect stream: Invalid argument


video:

- videocard: ATI Radeon Mobility X1400
- installed proprietary drivers earlier, but running hardware testing under system --> administration --> hardware testing gives me the message (when i get to video) "impossible with fglrx"
- what does this mean?

hope you can help me find the solution to these two problems, thank you!

---

### Post by muximus on 2008-05-27
you need to install the propreitary codecs. Check out the multimedia howtos on this forum

---

### Post by jacobh on 2008-05-28
tried following the basic how-to's and i still can't seem to get it working.

keep in mind i'm very new to linux. i found another thread about my particular audio card, where they ask for the following information:

jacob@jacob-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jacob@jacob-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd8500000 irq 22
jacob@jacob-laptop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
jacob@jacob-laptop:~$ amixer info
Card default 'Intel'/'HDA Intel at 0xd8500000 irq 22'
  Mixer name	: 'Realtek ALC880'
  Components	: 'HDA:10ec0880 HDA:11c13026'
  Controls      : 25
  Simple ctrls  : 15


is this of any help?

---

### Post by jacobh on 2008-05-28
solved the sound issue!

[this]("http://ubuntuforums.org/showthread.php?t=616845") post worked like a charm!

however, it seems that there is still a lot of static. how do i eliminate this? (FIXED! Alsamixer, turn down the volume on "Front" speakers)

video issue still remains. 3D seems really glitchy. In the Chess app that comes with ubuntu for example, i can turn on 3d-view and then it shows a black screen that flickers to the 3d-view now and then. also, screensavers just turn up a black screen, and my laptop refuses to wake up from suspend mode.

any ideas?

---

