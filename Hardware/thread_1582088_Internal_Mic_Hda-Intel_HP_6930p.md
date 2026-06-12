---
title: "Internal Mic Hda-Intel HP 6930p"
date: 2010-09-26
forum: Hardware
---

### Post by Volens on 2010-09-26
I'm running Lucid (10.04) x64 on an HP Elitebook 6930p.

My internal mic is not working properly and I am unable to use Skype/record audio. When I open the sound preferences interface and go to "input," the mic is not muted, the volume is up and the input level meter shows no indication of any sound from the mic.

Basically, I have added the following to my alsa-base.conf file
```

options snd-hda-intel model=laptop

```It had no effect. I also went through all the *alsamixer* options under playback AND capture. The only effects I was able to achieve were a lot of static when "mic" was turned up under playback and the ability to hear what the mic was picking up through the speakers when I turned up "internal." Tuning off "capture" did not effect the "internal" output. So in other words, the mic is definitely processing sound in some way, but it only seems able to direct it directly back to the speakers. (See picture for screenshot of my alsa options)

I tried compiling the alsa drivers myself at some point and it was a disaster because I'm pretty incompetent when it comes to compiling and especially making sure the modules etc. are loaded properly and reconfigured.

```

lspci -k

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio  Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30dc
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d8420000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```[IMG]http://ubuntuforums.org/[IMG]http://img121.imageshack.us/img121/8166/alsaoptions.png[/IMG]

[http://img121.imageshack.us/img121/8166/alsaoptions.png](http://img121.imageshack.us/img121/8166/alsaoptions.png)
[IMG]http://yfrog.com/3dalsaoptionsp[/IMG]

---

### Post by Volens on 2010-10-15
I thought I would never solve this, but I made a change that I thought had not worked in the past.

I added
```

options snd-hda-intel model=mobile

```
to both alsa-base.conf and options.conf and it appears that the mic is working properly

---

### Post by logoonlinepros on 2010-10-15
However, if you post a Reply within a Thread, clicking on "View First Unread" will no longer bring you to the firstnew message since your last visit - but will instead bring you to your own Post.

---

### Post by 007freak on 2010-10-24
Will this work for an HP Pavilion dv6626us?  I have tried a couple of other things to get the mic to work on my laptop and have not had any luck so far.

---

### Post by Volens on 2010-10-24
You can try this solution, but you will need to change what you add to those files because I'm not sure what model your sound card is. The following command ```
lspci -v
``` will list your devices as well as your sound card and you should be able to figure out what model and driver your card is currently using.

Mine looks like:
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 281a
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f0220000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

Once you find what model your card is look around the web for what options apply to that model. If you don't have an intel based card you may add a line that differs completely.

Try checking out: [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

I'll warn you that I'm still a noobie and I am currently trying to help someone else with this problem because he now has no sound at all after trying this.

---

### Post by mcduarte2000 on 2010-11-07
To me, on Mint Julia it was enough to add:

options snd-hda-intel model=mobile

to the bottom of the file:

/etc/modprobe.d/alsa-base.conf

---

### Post by akosh on 2010-11-10
I had this problem on a HP EliteBook 8530p.

Device:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

External microphone worked, but the sound through the internal one I only could hear  from the speakers. With Skype for example I could not use it.

It last worked with Karmic (9.10), and not anymore, neither with Lucid (10.04) nor with Maverick (10.10).

Adding:
*options snd-hda-intel model=mobile*

to:
*/etc/modprobe.d/alsa-base.conf*

solved the problem. Thanks!

---

### Post by andersgr on 2010-11-16
Would just like to confirm that this works.

I had the same issue with my hp 8530w on 10.10, and had tried setting the model value in alsa-base.conf to laptop with no effect, mobile did the trick however.

Thanks a bunch!

---

### Post by justleen on 2011-01-27
Just for reference:

Ubuntu 10.10 x64  on HP Probook 6540b.

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
        Subsystem: Hewlett-Packard Company Device 1726
        Flags: bus master, fast devsel, latency 0, IRQ 49
        Memory at d4600000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

All sound was working, apart from microphone.

Adding ```
options snd-hda-intel model=mobile
```
to /etc/modprobe.d/alsa-base.conf  fixed the problem.

---

