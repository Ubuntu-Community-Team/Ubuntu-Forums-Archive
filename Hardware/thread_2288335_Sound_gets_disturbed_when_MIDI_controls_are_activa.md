---
title: "Sound gets disturbed when MIDI controls are activated with updated kernel"
date: 2015-07-26
forum: Hardware
---

### Post by bestdani on 2015-07-26
Hello,
I use Ubuntu Studio 11.10 (3.0.0-12 generic) for quite a long while for DJing with mixxx. Since this system is extremely outdated and I was not able to install the lighting software qlc+ for instance additonally I've installed Ubuntu Studio 14.04 as well now.
But the following issue also happend when I updated the old 3.0.0-12 kernel and is present in ubuntu studio 14.10 as well. I think it's a kernel usb sound module problem but I'm not sure what I can do to solve it:

When I use the sound card of the DJ controller (Vestax Typhoon) every sound output works flawless as long as mixxx does not open the midi input/output of the dj controller. As soon as the midi controls are activated the sound gets disturbed extremely and sometimes the hardware crashes completely and I have to turn it off and on again.
I've recored a short audio sample of the two main stereo outputs, you can clearly hear when the midi controls are activated: [Dropbox Link]("https://www.dropbox.com/s/2b6cozc339oswev/midi-sound-problem.wav?dl=0"). On the two other channels you can only hear a very loud squeaking while midi controls are activated.

I read I could load the old kernel modules somehow for instance but I'm not sure if this solves the problem at its roots and I've not really an idea how I could do this. Since everything works flawless with the 3.0.0-12 kernel I think it's not related to mixxx.

I would be very grateful for any help.
Daniel

---

### Post by howefield on 2015-07-26
> **bestdani said:**
> Hello,
I use Ubuntu Studio 11.10 (3.0.0-12 generic) for quite a long while for DJing with mixxx. Since this system is extremely outdated and I was not able to install the lighting software qlc+ for instance additonally I've installed Ubuntu Studio 14.10 as well now.

Whilst possibly not helping with your question, please be aware that 14.10 is also end of life and no longer supported. Might be better looking at either 14.04 or 15.04, with the recommendation of 14.04.

---

### Post by bestdani on 2015-07-26
It's 14.04.2 LTS, I mixed it up since I was reading about 14.10 before posting. #-o  Edit: Just a noob speculation: Is it possible that for any kernel > 3.0.0-12 midi synthesizer capability has been added for usb audio devices or something like this? And that midi data that gets send to the device to control its LEDs is "directed" to the audio stream?  Is there any way to query the full ALSA "configuration" for the working and non working kernel versions?  Receiving midi data and setting the controllers LEDs via midi works flawless though.

---

### Post by bestdani on 2015-07-30
Hello, since it seems that the Ubuntu Studio category is not the correct place for [this problem]("http://ubuntuforums.org/showthread.php?t=2288335") (pleas read this first), I hope I can get any help by posting it here, now.  I've found some ALSA script after a lot of searching that shows that there are at least some difference in the configuration:

3.0.0-12 kernel system 
 ```
!!Module: snd_usb_audio
   async_unlink : Y
   device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
   enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    id :  (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
   ignore_ctl_error : N
   index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
   nrpacks : 8
   pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
   vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1 
```  

3.16.0-44 kernel system
```
!!Module: snd_usb_audio
   autoclock : Y
   device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
   enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    id :  (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
   ignore_ctl_error : N
   index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
   pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
   vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
```

I figured out that some changes were made to the kernel for which at least the nrpack property got dropped. But are these changes causing the error now? I also disabled autoclock but this did not solve the problem.

The next difference I could find is that the driver for the usb hub specified when using *lsusb -t* is *ehci_hcd* for the working system and *ehci_pci* for the new system, but I can't find any information if this could cause the problem.

I also get some "usb 2-1.3: current rate 48000 is different from the runtime rate 44100" dmesg notifications on the new system after switching the device to on, but I have no idea what causes this, the devices sample rate is indeed 44100 but this is detected correctly by any ALSA software.

I really hope for any input on how I could solve this or at least any redirection where chances are higher that I can get some help since the only solution for now was to change the operating system. :(

Daniel

---

### Post by howefield on 2015-07-30
Threads merged.

You can always report a thread if you feel it should be moved. :)

---

