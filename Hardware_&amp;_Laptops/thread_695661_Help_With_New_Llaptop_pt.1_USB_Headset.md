---
title: "Help With New Llaptop pt.1: USB Headset"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by wyth on 2008-02-13
I recently picked up a new Lenovo Ideapad Y510, and for the most part and very happy with it.  It's a snappy machine that holds great linux possibilities.  But I do have a few issues with it that I'm trying to fix, and this is part 1 in that series, my [Logitech usb notebook headset]("http://www.logitech.com/index.cfm/webcam_communications/internet_headsets_phones/devices/223&cl=us,en").  I know it can work, because it worked fine on my ancient Gateway laptop that recently bid farewell to this world.

So: lsusb recognizes it and gives me an ID of 046d:0a01.  However, in Skype, Logitech USB Headset does not appear under my device options.  Nor can I hear anything from the headset on any other application.  So I'm looking for a way to get that to work.

The overall sound was okay on install, but there were a few issues that needed the latest ALSA (like the speakers still delivering sound when headphones were plugged in). To get the sound to work properly, I had to compile the latest ALSA using [this guide]("https://help.ubuntu.com/community/HdaIntelSoundHowto"). In the alsa-kernel documentation, there were three model options for Lenovo: lenovo-101e, lenovo-nb0763, and lenovo-ms7195-dig.  I don't have a clue what the differences are and can find no info on them, so at the end of my /etc/modprobe.d/alsa-base file, I added
```
options snd-hda-intel model=[FONT=Tahoma,Sans,Arial,Helvetica,sans-serif]lenovo-101e[/FONT]
```[FONT=Tahoma,Sans,Arial,Helvetica,sans-serif]
That seems to work, but I haven't yet tried the other models since I don't even know the difference.
[/FONT] 
In /etc/modules, both snd-hwdep and snd-hda-intel are set to be loaded at boot.  

I *did* find some random info about making sure the snd-usb-audio module is loaded, but I can't seem to find it and don't think it's compiled;  when I modprobe it, I get  
```
 FATAL: Module snd_usb_audio not found.
```So maybe that's the key; if someone has some insight on getting the snd-usb-audio module in place, you'd have my gratitude.  If more info is needed, ask away.

---

### Post by wyth on 2008-02-13
Already an update:

snd-usb-audio was blacklisted in /lib/linux-sound-base/noALSA.modprobe.conf.

I commented that out, tried to modprobe it, and got 
```
FATAL: Error inserting snd_usb_audio (/lib/modules/2.6.22-14-generic/updates/sound/usb/snd-usb-audio.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
dmesg just  complains about snd_pcm_new and a bunch of stuff in the snd_pcm_* family.

---

