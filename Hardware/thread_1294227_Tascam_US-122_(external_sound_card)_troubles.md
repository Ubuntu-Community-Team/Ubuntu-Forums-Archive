---
title: "Tascam US-122 (external sound card) troubles"
date: 2009-10-18
forum: Hardware
---

### Post by Zoey.Marie on 2009-10-18
I've been trying for SO long, scouring every bit of info that comes up, and still nothing seems to be working.

My external sound card/interface just WON'T work. :(
I followed these instructions: [https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

and I get the light on, it stayed on when I plugged/unplugged it, sometimes I even got sound through it via the preferences > sound > test sound stuff...
-- but most of the time it would just freeze my computer, and I would need to hard reboot it.

I found a way to uninitialize it, and then followed these directions: [http://alsa.opensrc.org/index.php/Tascam_US-122](http://alsa.opensrc.org/index.php/Tascam_US-122)
-- subbing the most recent alsa-firmware (1.0.20) in. 

Now I don't get any sound, and it's still freezing when I try and test it.

I really need some help. :(

---

### Post by Cracauer on 2009-10-18
These things are a pain to get working.  I did it three times under Debian, copy'n'pasting the commandlines to get there and on both subsequent tries I had to modify the procedure.

Here's the latest. Again, Debian, not Ubuntu.
```

- install package alsa-firmware-loaders
- in debian it is misspelled us-112
- debian forgets to install the firmwares
   10  fetch http://ftp.mj2.org/pub/alsa/firmware/alsa-firmware-1.0.17.tar.bz2
        mkdir /usr/share/alsa/firmware
        zcat | tar fx -
        ./configure  --with-hotplug-dir=/usr/share/alsa/firmware &&
        make.  Do NOT `make install`, it messes up the installation.
        mv usx2yloader /usr/share/alsa/firmware/.
        sh /etc/init.d/udev restart
- plug out, plug in
- aplay -l
card 4: USX2Y [TASCAM US-X2Y], device 0: US-X2Y Audio [US-X2Y Audio #0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
- amidi -l
IO  hw:4,0,0  TASCAM US-X2Y MIDI 1


```

Stock up on coffee or beer or whatever keeps you going. You'll need it.

---

### Post by Zoey.Marie on 2009-10-18
Thank you a bunch for replying. I think a really hard part of all this is when people don't even try and help. :(
-- so thank you. :)

Though, to be honest, I'm still pretty new at all this, so I don't really understand a lot of your note (I don't really know how to break all of it down into steps and commands)--totally my shortfall, I know. Is there any way to translate it into newb language? If it's too much effort, I totally understand. I can try and get someone on the IRC channel to help (though sometimes they're too busy). Shrugs.

Also, I've been reading a lot of tutorials/how-to's etc. and I keep noticing that I always have the light on my us-122 on even though sound is not getting into the box (though, the only things I've tried are the preferences > sound, and JACK for testing--so there could be faults there too). It's just really hard running diagnostics on it when I don't really know what's wrong with it.
-- The light's on, that means it's initialized, right? So why wouldn't I be getting sound from it?? :/ I guess if it's a bad install, there could be a million things wrong with it.


Let me know your thoughts, and if you have any further help, it'd be wonderful. :)


~ Z

---

### Post by Zoey.Marie on 2009-10-18
I've tried [https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)
I've tried  [http://alsa.opensrc.org/index.php/Tascam_US-122](http://alsa.opensrc.org/index.php/Tascam_US-122)

I've tried subbing the latest alsa firmware (1.0.20), I've tried the 1.0.17, I've tried the 1.0.19.

I can't even get the preferences > sound tests to work anymore.

This is so frustrating.

The light is on, but I can't figure out how to get sound from it. :(

is there something else I should be testing? Some other place to check it? Gr...

~ Z

---

### Post by Cracauer on 2009-10-18
Please give us dmesg, /var/log/messages and lsusb after you plugit out and back in with what you have.

---

### Post by Zoey.Marie on 2009-10-18
> **dmesg] [10624.354228] usb 1-3.2: USB disconnect, address 10
[10652.771934] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 332
[10655.028147] usb 1-3.2: new full speed USB device using ehci_hcd and address 11
[10655.140150] usb 1-3.2: configuration #1 chosen from 1 choice
[10655.325192] usb 1-3.2: USB disconnect, address 11
[10657.076154] usb 1-3.2: new full speed USB device using ehci_hcd and address 12
[10657.190952] usb 1-3.2: configuration #1 chosen from 1 choice
[10660.449458] Sequence Error!(hcd_frame=4 ep=8in said:**
>  Most propably some urb of usb-frame 1025 is still missing.
[10660.449464] Cause could be too long delays in usb-hcd interrupt handling.
[10660.484202] Sequence Error!(hcd_frame=39 ep=10out;wait=39,frame=36).
[10660.484205] Most propably some urb of usb-frame 39 is still missing.
[10660.484208] Cause could be too long delays in usb-hcd interrupt handling.
[10660.523195] Sequence Error!(hcd_frame=78 ep=10out;wait=78,frame=75).
[10660.523198] Most propably some urb of usb-frame 78 is still missing.
[10660.523200] Cause could be too long delays in usb-hcd interrupt handling.
[10660.563190] Sequence Error!(hcd_frame=118 ep=10out;wait=118,frame=115).
[10660.563194] Most propably some urb of usb-frame 118 is still missing.
[10660.563196] Cause could be too long delays in usb-hcd interrupt handling.
[10661.473288] Sequence Error!(hcd_frame=4 ep=8in;wait=1025,frame=1).
[10661.473292] Most propably some urb of usb-frame 1025 is still missing.
[10661.473294] Cause could be too long delays in usb-hcd interrupt handling.



[quote=/var/log/messages] 
Oct 18 14:49:04 zoey-laptop kernel: [10574.144330] usb 1-3.2: new full speed USB device using ehci_hcd and address 9
Oct 18 14:49:04 zoey-laptop /lib/udev/tascam_fw: load /usr/share/alsa/firmware/usx2yloader/us122fw.ihx for 1604/8006/100 to /proc/bus/usb/001/009
Oct 18 14:49:04 zoey-laptop kernel: [10574.258801] usb 1-3.2: configuration #1 chosen from 1 choice
Oct 18 14:49:04 zoey-laptop /lib/udev/tascam_fw: load /usr/share/alsa/firmware/usx2yloader/us122fw.ihx for 1604/8006/100 to /proc/bus/usb/001/009
Oct 18 14:49:04 zoey-laptop /lib/udev/tascam_fw: unknown product 
Oct 18 14:49:04 zoey-laptop kernel: [10574.442675] usb 1-3.2: USB disconnect, address 9
Oct 18 14:49:06 zoey-laptop kernel: [10576.192170] usb 1-3.2: new full speed USB device using ehci_hcd and address 10
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for /proc/bus/usb/001/010
Oct 18 14:49:06 zoey-laptop kernel: [10576.306923] usb 1-3.2: configuration #1 chosen from 1 choice
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for /proc/bus/usb/001/010
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:06 zoey-laptop last message repeated 2 times
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:06 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:07 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:07 zoey-laptop last message repeated 2 times
Oct 18 14:49:07 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:07 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:07 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:07 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:07 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:07 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:07 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:08 zoey-laptop last message repeated 3 times
Oct 18 14:49:08 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:08 zoey-laptop last message repeated 3 times
Oct 18 14:49:08 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:08 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:08 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:08 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:09 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:09 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:09 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:49:09 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:49:09 zoey-laptop last message repeated 2 times
Oct 18 14:49:09 zoey-laptop pulseaudio[3837]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
Oct 18 14:49:54 zoey-laptop kernel: [10624.354228] usb 1-3.2: USB disconnect, address 10
Oct 18 14:50:23 zoey-laptop kernel: [10652.771934] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 332
Oct 18 14:50:25 zoey-laptop kernel: [10655.028147] usb 1-3.2: new full speed USB device using ehci_hcd and address 11
Oct 18 14:50:25 zoey-laptop /lib/udev/tascam_fw: load /usr/share/alsa/firmware/usx2yloader/us122fw.ihx for 1604/8006/100 to /proc/bus/usb/001/011
Oct 18 14:50:25 zoey-laptop kernel: [10655.140150] usb 1-3.2: configuration #1 chosen from 1 choice
Oct 18 14:50:25 zoey-laptop /lib/udev/tascam_fw: load /usr/share/alsa/firmware/usx2yloader/us122fw.ihx for 1604/8006/100 to /proc/bus/usb/001/011
Oct 18 14:50:25 zoey-laptop /lib/udev/tascam_fw: unknown product 
Oct 18 14:50:25 zoey-laptop kernel: [10655.325192] usb 1-3.2: USB disconnect, address 11
Oct 18 14:50:27 zoey-laptop kernel: [10657.076154] usb 1-3.2: new full speed USB device using ehci_hcd and address 12
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for /proc/bus/usb/001/012
Oct 18 14:50:27 zoey-laptop kernel: [10657.190952] usb 1-3.2: configuration #1 chosen from 1 choice
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for /proc/bus/usb/001/012
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:27 zoey-laptop last message repeated 2 times
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:27 zoey-laptop last message repeated 2 times
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:27 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:28 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:28 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:28 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:28 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:28 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:28 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:28 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:28 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:28 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:29 zoey-laptop last message repeated 2 times
Oct 18 14:50:29 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:29 zoey-laptop last message repeated 2 times
Oct 18 14:50:29 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:29 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:29 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:29 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:29 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:29 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:30 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:30 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:30 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:30 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:30 zoey-laptop /lib/udev/tascam_fpga: calling /usr/bin/usx2yloader for 
Oct 18 14:50:30 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:30 zoey-laptop /lib/udev/tascam_fpga: leaving
Oct 18 14:50:30 zoey-laptop pulseaudio[3837]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
Oct 18 14:52:23 zoey-laptop kernel: [10772.777142] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 248
[/quote]

[quote=lsusb]
Bus 001 Device 012: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 001 Device 005: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 004: ID 03f0:5411 Hewlett-Packard Officejet 4300
Bus 001 Device 003: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/quote]


I hope that was what I was supposed to paste. :/

---

### Post by Zoey.Marie on 2009-10-18
Update:

This is what it says when I test it through preferences > sound

>  gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback. -- it does that for all options when set to the Tascam (alsa) setting.

This is what Jack says:
>  
 ALSA: cannot set hardware parameters for playback
 ALSA: cannot configure playback channel
 cannot load driver module alsa

Any thoughts?

---

### Post by Zoey.Marie on 2009-10-18
Update:

I just followed this ([http://ubuntuforums.org/showpost.php?p=5277136&postcount=1](http://ubuntuforums.org/showpost.php?p=5277136&postcount=1)) thread, specifically these directions:

>  
killall pulseaudio
sudo alsa force-reload


And now I get this when I hit "test":
> 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource.


*then* I did the  "pulseaudio -D" part, and it went back to the previous error message. 
>  gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.

So, hey... interesting, right?


Can someone please help me figure out what it means? :(
[]("http://ubuntuforums.org/showpost.php?p=5277136&postcount=1")

---

### Post by Cracauer on 2009-10-19
> [10660.449458] Sequence Error!(hcd_frame=4 ep=8in;wait=1025,frame=1).
[10660.449462] Most propably some urb of usb-frame 1025 is still missing.


Gotta love high end error messages.

But alas, this looks like b0rked USB. Are you using some questionably quality hub or something?

---

### Post by Cracauer on 2009-10-19
> **Zoey.Marie said:**
> Update:

I just followed this ([http://ubuntuforums.org/showpost.php?p=5277136&postcount=1](http://ubuntuforums.org/showpost.php?p=5277136&postcount=1)) thread, specifically these directions:



And now I get this when I hit "test":


*then* I did the  "pulseaudio -D" part, and it went back to the previous error message. 


So, hey... interesting, right?


Can someone please help me figure out what it means? :(
[]("http://ubuntuforums.org/showpost.php?p=5277136&postcount=1")

I think those things just mean the device doesn't exit (in the OS). Ignore.

---

### Post by Zoey.Marie on 2009-10-19
[quote=Cracauer] But alas, this looks like b0rked USB. Are you using some questionably quality hub or something?[/quote]

I was really excited for a second, because something different happened when I switched the port from my hub to my actual computer's port. It wouldn't turn on, so then I did the "sudo usx2yloader" thing, and I got the "No USX2Y-compatible cards found"-thing. Then I did the  "sudo ln -s /usr/share/alsa/firmware/usx2yloader /lib/firmware/usx2yloader"-thing (which I think spit out some error message). THEN I re-copied the 55-tascam.rules thing and unplugged and re-plugged it in, and alas! It worked! I tested the sound and sound came out!

Then the computer froze, and I haven't been able to get it to work since... :(
same error message:

[quote=bane of my existance] 	 	 		 			 				 gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback. [/quote]

Thoughts?

---

### Post by Cracauer on 2009-10-20
You need a new hub I guess.

Test the soundcard with aplay.

---

### Post by Zoey.Marie on 2009-10-24
Okay. So... here's the update:
-- I was depressed since the last time I posted, so I just really didn't want to deal with it.

I can hear sound using aplay
I can record using arecord, then hear what I recorded using aplay...
-- so the thing works.

BUT 

When I try and use hydrogen, jack, testing it via preferences > sound, probably anything else... **it freezes my system up**

I no longer have it plugged into that hub, I've verified that it's working... how do I actually use it?

If I need to repost dmesg, lsusb, whatever, let me know... I'll probably be near the computer most of the day. **Thoughts?**

---

### Post by Cracauer on 2009-10-24
No, if aplay works all the system and driver things are in order.

I don't use any of that wizzy wizzy software, can't really help you there.

---

### Post by Zoey.Marie on 2009-10-24
Well... I know it's installed right or something because aplay works... (I did  aplay -D plug:hw:1 -c 2 /usr/lib/openoffice/basis3.0/share/gallery/sounds/cow.wav, and it plays without freezing).

But, it doesn't really matter what program I use to test it out... it crashes anything I try it on (besides the command line stuff).

Where would I even begin looking for the problem?

I don't think it's jackd, hydrogen, whatever... I think it's the card b/c literally everything I try it on it crashes... 

:/

---

### Post by Cracauer on 2009-10-24
> **Zoey.Marie said:**
> Well... I know it's installed right or something because aplay works... (I did  aplay -D plug:hw:1 -c 2 /usr/lib/openoffice/basis3.0/share/gallery/sounds/cow.wav, and it plays without freezing).

But, it doesn't really matter what program I use to test it out... it crashes anything I try it on (besides the command line stuff).

Where would I even begin looking for the problem?

I don't think it's jackd, hydrogen, whatever... I think it's the card b/c literally everything I try it on it crashes... 

:/

Why is the Tascam hw:1? What is hw:0?

You need to tell the applications to use the Tascam. 

Might be easiest to kill the drivers for whatever is hw:0

---

### Post by Zoey.Marie on 2009-10-28
Just so that it's noted, I installed the 686 multimedia real-time kernel and it works perfectly (I just had to tweak the settings in JACK I used, because I was getting crackles in the sound)

though now my wireless adapter doesn't work... any thoughts on what I should do for that? :D

---

