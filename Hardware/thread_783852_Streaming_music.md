---
title: "Streaming music"
date: 2008-05-06
forum: Hardware
---

### Post by hannulan on 2008-05-06
I need some kind of hardware to stream music from my laptop (and maybe my desktop too) to my speakers. 

I have seen Apples AirPort Express and this is almost what I want, but for me it would be enough with the 3.5 mm port, don't really need usb (but it would be useful). After some search it seems that Airport Express didn't work so easily in Ubuntu, I'm not so good at mixtering with the computer.

Anyone how can give me a tip what to look for.

---

### Post by sj_ on 2009-10-16
Airport Express works in Ubuntu even better than in Windows, instead one thing that i can't use my iphone remote. But u can stream not only iTunes music collection, it just works like standart audio output with pulse audio


[http://ubuntuguide.org/wiki/Ubuntu:Jaunty_ru](http://ubuntuguide.org/wiki/Ubuntu:Jaunty_ru)

**Airport Express with Pulse Audio**

The Airport Express (AEX) is a network device with an audio output jack that can be connected to speakers or an amplifier. You can stream audio over the network (wired or wirelessly) to (or from) this device.

These capabilities require the newest version 0.9.15 of Pulse Audio and Pulse Audio Volume Control 0.98

You need to  install:

```
sudo apt-get install pulseaudio pavucontrol paprefs padevchooser pulseaudio-module-raop
```

Then configure Pulse Audio:

    Menu -> Settings -> PulseAudio Preferences Sound Audio preferences -> Network Access 

and check both:

    > Make discoverable network sound devices available locally 
    Make discoverable Apple Airtunes devices available locally 

Note: Make sure your firewall is not blocking ports 5353, 5000, and 6000.

My AEX is discovered, but I got no sound through it until I selected it as the default sink (output) from the PulseAudio Device Chooser.

   menu -> Multimedia -> PulseAudio Device Chooser -> Manager -> Devices -> Sinks

        I then noted the name of my Airport Express device to be raop.Base-Station-e60157.local, so I entered that as the sink: 

    PulseAudio Device Chooser -> Default sink -> Other -> raop.Base-Station-e60157.local 

Now, any devices (or multimedia players) setup to play through PulseAudio will play through the stereo attached to the Airport Express.

---

### Post by sj_ on 2009-10-16
Guys, i wrote the post on my blog how to setup Ubuntu to stream to AirPort Express. You are welcome [http://www.1ph0ne.com/?p=402](http://www.1ph0ne.com/?p=402)

---

### Post by rckdrews on 2009-10-16
Tnx sj, I tried your suggested set up and it's working. :D

---

### Post by sparkle12 on 2011-01-06
Thanks SJ_, works fine :p

---

