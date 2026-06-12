---
title: "Logitech H600 usb wireless headphones"
date: 2012-01-20
forum: Hardware
---

### Post by tommyss4l on 2012-01-20
My old wired headphones stopped working so I got wireless headphones, and I can't seem to get them to work, has anyone had any luck getting them to work?

Sound options recognize they are there, both mic and headphones, but no sound in or out.

Thanks for the help

---

### Post by DemonSpeedster on 2012-02-01
I'm planning to get one. Have you tried to go System > Preferences > Sound, and open the “hardware” tab and use the test function?

---

### Post by cvikas on 2012-02-03
Is it working with your Ubuntu?

Because in mine its not working, if you could please let me know the steps then that would be awesome.

I have Dell L501X and Ubuntu 10.10

Thanks

---

### Post by mikrowelle on 2012-02-20
[SIZE=1][COLOR=Gray][SIZE=2][COLOR=Black]Greyed out my old post because for some reason after formatting my computer (wanted to give archlinux a try) and re-installing Ubuntu 11.10 instead of Xubuntu 11.10 the headset worked.[/COLOR][/SIZE]

I could get my new Logitech H600 headset working, but it's just working in VLC. Everything else comes out of my notebook speakers. I'm using Xubuntu 11.10.

I opened the preferences and changed the[/COLOR][/SIZE][COLOR=Gray] [/COLOR][SIZE=1][COLOR=Gray]** output module** to **"ALSA audio output"** and the **device** to **"Logitech Wireless Headset"**. Ta-dah! Works in VLC. But just there.

So I suspected that it has something to do with ALSA and the headset being configured as default there. Thanks to Google I stumbled upon this forum post ([/COLOR][/SIZE][COLOR=Gray] [/COLOR][SIZE=1][COLOR=Gray][http://forums.debian.net/viewtopic.php?f=7&t=72772](http://forums.debian.net/viewtopic.php?f=7&t=72772)) in which approximately the same problem is being described. The only difference is that he got it working, and I didn't :(

I tried both creating a [/COLOR][/SIZE][COLOR=Gray] [/COLOR][SIZE=1][COLOR=Gray]**.asoundrc** in my home folder and creating **/etc/asound.conf**, and added **pcm.!default front:Headset** to both of them. Neither the local nor the system-wide configuration changed anything.

**(EDIT1: I read on the german ubuntuusers wiki ([http://wiki.ubuntuusers.de/.asoundrc#asoundrc-wird-ignoriert](http://wiki.ubuntuusers.de/.asoundrc#asoundrc-wird-ignoriert)) that in some cases .asoundrc is being ignored when using Ubuntu, and that it doesn't happen in other distributions. Probably that's the reason?)**[/COLOR][/SIZE][COLOR=Gray]  [/COLOR][SIZE=1][COLOR=Gray]
[B] 
(EDIT2: Headset also works perfectly in Audacity (which has ALSA set as it's output). It also works when I try playing a soundfile through the default device (which is set to headset in my asound.conf) through aplay -D default soundfile.wav. So I guess it really is some problem with Pulse, but I have no idea how to fix this)  

(EDIT3: Could get my headset working by deinstalling pulseaudio. The only downsides (so far) are that the dock plugin doesn't do anything else anymore than showing the alsamixer, and that I have to manually configure asound.conf if I want to switch between the headset and my laptop speakers. I guess the first one is harder to fix, and I'm too lazy right now to look for a fix for the switching thing (if there even is one).)

(EDIT4: There seem to be more problems than just with switching forth and back between different output devices. Just tried plugging in usual headphones and then I suddenly had sound on the headphones but not on the headset, when I unplugged them I suddenly had the sound coming from the netbook speakers, and couldn't get it back to my headset without restarting the music player.)
 [/B]
I'm not really an expert of linux so I don't know whether this could be right, but my first guess is that I need to configure something for pulseaudio. Didn't yet figure out where to do this though. Any advice?[/COLOR][/SIZE][COLOR=Gray]  [/COLOR][SIZE=1][COLOR=Gray]

Btw, if it's any help, here's my output of aplay -L:[/COLOR][/SIZE][COLOR=Gray] [/COLOR][SIZE=1][COLOR=Gray]
```
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=Intel,DEV=0
    HDA Intel, HDMI 0
    HDMI Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Hardware device with all software conversions
front:CARD=Headset,DEV=0
    Logitech Wireless Headset, USB Audio
    Front speakers
surround40:CARD=Headset,DEV=0
    Logitech Wireless Headset, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Headset,DEV=0
    Logitech Wireless Headset, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Headset,DEV=0
    Logitech Wireless Headset, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Headset,DEV=0
    Logitech Wireless Headset, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Headset,DEV=0
    Logitech Wireless Headset, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Headset,DEV=0
    Logitech Wireless Headset, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Headset,DEV=0
    Logitech Wireless Headset, USB Audio
    Direct sample mixing device
dsnoop:CARD=Headset,DEV=0
    Logitech Wireless Headset, USB Audio
    Direct sample snooping device
hw:CARD=Headset,DEV=0
    Logitech Wireless Headset, USB Audio
    Direct hardware device without any conversions
plughw:CARD=Headset,DEV=0
    Logitech Wireless Headset, USB Audio
    Hardware device with all software conversions
```And here the output of aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech Wireless Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```[/COLOR][/SIZE]

---

### Post by bhankins on 2012-03-01
I'm a little late on this thread, but I just got one of these myself and had the same problem. I ended up plugging it into a windows machine at work and had the same problem, no sound. I discovered a pairing utility on [Logitech's website]("http://logitech-en-amr.custhelp.com/app/answers/detail/a_id/26661/section/troubleshoot/crid/438/lt_product_id/8391/tabs/1,3,2,4,5/cl/us,en"). After I successfully paired it once and got it working in windows it worked right off the bat in Ubuntu.  Note, if you move the usb connector immediately to the Ubuntu machine after pairing you need to turn the power on the headphones off and then on again. I hope this helps someone with the same problems we had.

---

### Post by ferhatelmas on 2012-10-24
> **bhankins said:**
> I'm a little late on this thread, but I just got one of these myself and had the same problem. I ended up plugging it into a windows machine at work and had the same problem, no sound. I discovered a pairing utility on [Logitech's website]("http://logitech-en-amr.custhelp.com/app/answers/detail/a_id/26661/section/troubleshoot/crid/438/lt_product_id/8391/tabs/1,3,2,4,5/cl/us,en"). After I successfully paired it once and got it working in windows it worked right off the bat in Ubuntu.  Note, if you move the usb connector immediately to the Ubuntu machine after pairing you need to turn the power on the headphones off and then on again. I hope this helps someone with the same problems we had.

Yes, that works. Thanks!

---

### Post by cafuse on 2013-02-19
I got working Logitech H800 in Ubuntu 12.04 LTS through the USB only by connecting it first to a Macbook pro laptop, then to Ubuntu. No need to use the pairing utility.

Before doing this, Pulse Audio did not see the headset.

I tried the same trick with the bluetooth but it did not work.

Thanks for the advices!

---

