---
title: "ubuntu 11.10 with HP8510W : no s/pdif available..."
date: 2011-12-10
forum: Hardware
---

### Post by lapk on 2011-12-10
Hi,

I'm new on that forum...
I installed ubuntu in place of a windows on my laptop and I'm trying to make the sound work over the hdmi... I've been able to make the video work but for the sound it's still very difficult for me to understand what to do.

What I can tell you so far is that I should be using  s/pdif to have some sound on the TV but alsamixer isn't showing anything...

I already spent a lot of time looking around and I'm out of ideas so if someone know a nice procedure to follow I'll be happy to try !

Thanks for your help !

---

### Post by BC59 on 2011-12-10
Check here there are some solutions if they fit to your case:

[http://ubuntuforums.org/showthread.php?t=1871349](http://ubuntuforums.org/showthread.php?t=1871349)

---

### Post by lapk on 2011-12-10
My video card is a nvidia FX 570M... the topic you mention seems related to ATI cards.

the lspci -v | grep -i audio only reports the following line
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

That's why I think I need the S/Pdif output... the pb is: it doesn't show up when I run alsamixer.

---

### Post by lapk on 2011-12-10
aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Hardware device with all software conversions

---

### Post by lapk on 2011-12-13
I dropped ubuntu and installed opensuse 12.1 instead... and you know what ? It worked directly !  Now I can switch from the stereo ouput to the digital one and have some sound over HDMI ! Yepee \o/
I no longer have other small issues like some text box too small that couldn't be resized, some menu that couldn't stay opened unless I kept the mouse button pressed, the video output on HDMI that was just messed up sometimes killing gnome-wm...

For the record the GPU is a FX570M (equivalent to a NVidia 8600M)...

---

