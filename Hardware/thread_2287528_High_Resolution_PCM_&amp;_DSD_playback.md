---
title: "High Resolution PCM &amp; DSD playback"
date: 2015-07-20
forum: Hardware
---

### Post by Welly Wu on 2015-07-20
I own both a Lenovo IdeaPad Y510P notebook PC and ZaReason Zeto desktop PC both of which run Ubuntu 14.04.2 64 bit LTS GNU/Linux. I also own an Oppo Digital HA-1 DAC and headphone amplifier and a Sennheiser HD-800 headphone for my ZaReason Zeto desktop PC and I own a CEntrance HiFi-M8 LX XL4 portable DAC and headphone amplifier and Shure SE-846 CL earphones for my Lenovo IdeaPad Y510P. I added the DeaDBeef PPA and I successfully installed it. I reconfigured ALSA plugin output to disable ALSA resampling and to release the device when stopped. I am having problems selecting and playing high resolution 24 bit 96/192 kHz FLAC music albums when I select my Oppo Digital HA-1 IEC958 (S/PDIF) or any of the listings for the Oppo Digital HA-1. It won't play audio. I have to choose the playback through the PulseAudio sound server. It limits me to 32 bits 44.1 kHz playback. This used to work previously, but I'm not sure what's going on now. I also purchased J River Media Center 20 64 bit with the master license for J River Media Center 21 at a discounted price and it keeps crashing randomly and it too is limited to 32 bits 44.1 kHz. I would also like to know how to play DSD music albums using Ubuntu 64 bit LTS GNU/Linux. I'm not a Linux newbie and I'm not an audiophile newbie either. I just need to know what's going on that prevents high resolution PCM and DSD playback and I need some guidance and help. Thank you.

```
wellywu@ZaReasonZeto:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: DAC [OPPO HA-1 USB AUDIO 2.0 DAC], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
wellywu@ZaReasonZeto:~$
```

Why does card2: DAC [OPPO HA-1 USB AUDIO 2.0 DAC], device 0: USB Audio [USB Audio] state that it only has Subdevices: 0/1?

Let me be clear. When I use the Ubuntu sound settings and I select my Oppo Digital HA-1 (S/PDIF) or Analog Output, I do hear audio and music. It's when I try to use DeaDBeef to select my Oppo Digital HA-1 and it won't play audio. This is required to get the sample frequency and bit depth correct especially for high resolution PCM and DSD albums to play. It won't play audio or music when I select my Oppo Digital HA-1 within DeaDBeef at all. It used to work in the past, but I got my ZaReason Zeto desktop PC and I upgraded to Ubuntu 14.04.2 64 bit LTS GNU/Linux. What is going on here? What more information do you need from me? How can this get fixed?

---

### Post by Welly Wu on 2015-07-21
[FONT=arial]I fixed it! I simply plugged my Oppo Digital HA-1 into another Super Speed USB 3.0 port and I restarted my ZaReason Zeto desktop PC and it works.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]wellywu@ZaReasonZeto:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: DAC [OPPO HA-1 USB AUDIO 2.0 DAC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
wellywu@ZaReasonZeto:~$
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I am using DeaDBeef and I successfully selected my Oppo Digital HA-1 IEC958 (S/PDIF) and it is playing 32 bits 96 kHz for my Diana Krall All for You HDTracks album. I recently purchased and got my Sennheiser CH 800 S balanced 4 pin XLR headphone cable and I plugged it into my Oppo Digital HA-1 DAC and headphone amplifier. My Oppo Digital HA-1 cost me $1,200.00 USD and my Sennheiser HD-800 headphones cost me $1,979.00 USD. I also own my CEntrance HiFi-M8 LX XL4 portable DAC and headphone amplifier which cost me $700.00 USD and my Shure SE-846 CL quad driver earphones which cost me $1,000.00 USD. They work with my ZaReason Zeto and Lenovo IdeaPad Y510P desktop and notebook PCs right out of the box.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Problem solved by simply reconnecting and restarting my PC.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thanks for the suggestion, but it's not necessary now. I have been using Ubuntu and various other GNU/Linux distributions since April 2009 and my gut told me that I needed to restart my ZaReason Zeto desktop PC and this problem would go away by itself without tearing out my hair. So, I followed what my gut told me to do.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thank you for looking into this issue.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Best Regards:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Welly Wu[/FONT]
[FONT=arial]07/21/2015[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]PS:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]They say that GNU/Linux is the poor man's OS, but few people have heard of me.[/FONT]

---

### Post by Welly Wu on 2015-07-22
I also figured out that when I use Google Chrome to play audio or music, then it takes exclusive control of my Oppo Digital HA-1 until I exit the web browser completely. So, if I want to use DeaDBeef or J River Music Center 20 64 bit, then I have to exit my web browser and check aplay -l to ensure that I can fully access my HA-1. Then, I can set the sound device to my Oppo Digital HA-1 and play high resolution PCM music albums in full. I contacted J River's Interact forum and the administrator told me to update to version 132 and to run ./alsacap in the /usr/lib/jriver\Media\ Center\ 20/alsacap to check my sound devices and which names and assignments are given to each one. So I selected IEC958 (S/PDIF) which corresponds to my Oppo Digital HA-1 and everything works now. Solved!

---

