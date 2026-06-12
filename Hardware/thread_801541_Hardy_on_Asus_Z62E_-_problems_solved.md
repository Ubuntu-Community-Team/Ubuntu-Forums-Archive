---
title: "Hardy on Asus Z62E - problems solved"
date: 2008-05-20
forum: Hardware
---

### Post by dlane on 2008-05-20
For anyone with an ASUS laptop that loses sound support on resume from suspend or hibernate in Hardy, here's what I've found:

I found that I have an Realtek sound device called ALC883.  It's supported by the snd_hda_intel kernel module (run > sudo lspci | grep snd_hda_intel to see if it's been installed for you), but that module needs to associate your specific hardware with a known "model" - turns out there are many configurations for the ALC883 hardware.  In my /var/log/messages, I was getting messages like "hda_codec: Unknown model for ALC883, trying auto-probe from BIOS..." during boot, implying that it didn't match a known model signature.  As a result, I suspect I was getting the most generic possible sound support (it was certainly unspectacular).  You can also check what model (if any has been detected) by > sudo cat /sys/module/snd_hda_intel/parameters/model - if that file doesn't exist, then you're in generic mode...

Subsequently, I've found, by going to a console (CTRL+ALT+F1), logging in, and shutting down X (> sudo /etc/init.d/gdm stop), and then - dependencies on sound turned off - removing the snd_hda_intel module (> sudo modprobe -r snd_hda_intel) and reinserting it with various options (see [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)) like > sudo modprobe model=3stack-dig - look at the descriptions for your audio hardware in that ALSA-Configuration file, and pick the one which looks like it matches most closely, regardless of the manufacturer.  If you modprobe the snd_hda_module with a new model, check /var/log/messages immediately afterward, and see if it lists the "Unknown model" message above, then that's not it.  If it succeeds, however, I haven't found any messages to confirm it, just the absence of the "Unknown model message".  

After finding one that worked for me, I added the following line to the bottom of /etc/modprobe.d/alsa-base to use that model option on boot...
> 
#options snd-hda-intel model=asus-laptop
#options snd-hda-intel model=asus
#options snd-hda-intel model=tagra-dig
#options snd-hda-intel model=3stack-dig
options snd-hda-intel model=6stack-dig

(note, I tried quite a few! :)) - also note that in the option stanza, for some reason, you use "-" rather than "_" in the module name.  

After rebooting to the X desktop, I ran gnome-alsamixer to check if anything had changed - and sure enough, I had a whole bunch of new devices (new sliders and tick boxes, etc.) and by fiddling with those, I gained much better control of my hardware.  Also, I didn't lose sound on resuming from suspend or hibernate!   

Hope that helps someone avoid further frustration!

Dave

---

### Post by Languid Heap on 2009-04-10
Although it's nearly a year later, I just wanted to thank you for writing this HOWTO. It helped me solve an issue with my onboard sound (ALC883) on a Gigabyte E7AUM-DS2H. 

I was trying to get the sound on my Winfast 2000xp TV Card working, but I couldn't find the appropriate track (CD or AUX) to unmute in ALSAMixer. Following your HOWTO fixed the problem for me.

Thanks again, and bump for anyone experiencing the same problem, looking for a little help...

---

### Post by alanwww1 on 2009-04-12
> **Languid Heap said:**
> Although it's nearly a year later, I just wanted to thank you for writing this HOWTO. It helped me solve an issue with my onboard sound (ALC883) on a Gigabyte E7AUM-DS2H. 

I was trying to get the sound on my Winfast 2000xp TV Card working, but I couldn't find the appropriate track (CD or AUX) to unmute in ALSAMixer. Following your HOWTO fixed the problem for me.

Thanks again, and bump for anyone experiencing the same problem, looking for a little help...

Hello !

What model did you specify for the Gigabyte board.
I can not get suspend to ram work with the onboard sound.

Thanks

---

### Post by Languid Heap on 2009-04-16
alanwww1,

In /etc/modprobe.d/alsa-base.conf I used

```
options snd-hda-intel model=6stack-dig
```

Be aware that the model of the motherboard that I use is a micro-atx desktop motherboard -- not a laptop.

---

