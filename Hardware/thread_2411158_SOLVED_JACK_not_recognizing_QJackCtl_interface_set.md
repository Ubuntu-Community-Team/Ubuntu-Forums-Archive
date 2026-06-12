---
title: "SOLVED: JACK not recognizing QJackCtl interface settings"
date: 2019-01-25
forum: Hardware
---

### Post by zurn2 on 2019-01-25
Hello everyone, I'm somewhat new to the Linux world and this is my first post, so here goes...

Basically my problem is exactly what the title says: I'm trying to use a USB audio device (just a simple usb to headphone/mic ports) as my audio output when using JACK, and it doesn't seem to be recognizing it. It works perfectly fine with PulseAudio, though I've been sure to turn the device off in PulseAudio Volume Control when trying to use it with JACK. I've confirmed that I am using the correct device name through the cad /proc/asound/card1 terminal command. It comes up there as something like hw:Device [USB Audio Device] and that's what I set the QJackCtl interface to. 

One other thing that's worth noting is that I've configured PulseAudio to automatically route through JACK when JACK is connected. I can't say whether this has anything to do with it as I made these changes before I got the USB audio device. 

After several hours of research and trying different things, what I have concluded is that the interface settings in QJackCtl are not actually effecting the changes they're supposed to. The closest I've come to explaining this is that maybe I have jackd AND jackdbus installed at the same time? I think I read somewhere that you can't have that. 

ANY guidance would be greatly requested. I've search and read through many many forums but have not managed to track down anyone with the same problem. 

Oh yes, I'm running Ubuntu Studio 16.04 on a Lenovo Thinkpad X230.

Thanks,
-Z

---

### Post by zurn2 on 2019-01-25
Someone on IRC gave me these lines and now it works fine. 

killall -9 jackd jackdbus
jack_control ds alsa dps capture none dps playback none
jack_control dps device hw:Device  dps rate 48000  dps period 1024  dps nperiods 2 start

:):):):):):)
Thank you Linux Community!

****
I don't know how to make the : D in the above code not be a smiley, face

---

### Post by yetimon_64 on 2019-01-25
> **zurn2 said:**
> ...
I don't know how to make the : D in the above code not be a smiley, face
Use bbcode tags around any parts of your post that need it... [[COLOR=#0000ff]--link to UF bbcode list --[/COLOR]]("https://ubuntuforums.org/misc.php?do=bbcode")

Place [noparse][noparse][/noparse][/noparse] tags around the [noparse]:D[/noparse] that you don't want showing up as a smiley.

**Edit:** an alternative to [noparse][noparse][/noparse][/noparse] tags would be post all commands and/or terminal output in between [noparse]```

```[/noparse] tags, this will automatically preserve formatting and prevent smilies etc.

P.S: Welcome to the ubuntuforums. :-)

---

