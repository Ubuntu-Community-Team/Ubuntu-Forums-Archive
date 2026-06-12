---
title: "Speaker/Headphone Port Issue"
date: 2008-04-30
forum: Hardware
---

### Post by nicholas.Platt on 2008-04-30
Hello,


I've searched around here a bit and found quite a few threads left unanswered, and several guides that didn't seem to quite address my issue. I have a Vaio VGN-FZ140E, and I'm trying to get my external speakers to work. The problem appears to be a missing driver for my headphone/audio out port.

Right now the sound is coming through the laptop speakers fine, but I can't use my external speakers -- even when the jack is plugged in, the sound still comes through my laptop speakers only.

Thanks for your assistance. =)
Ubuntu 8.04 is excellent so far, I love it.

---

### Post by Nepherte on 2008-04-30
I had the same issue with my Sony Vaio SZ6 (intel HDA) and alsa 1.0.15 or higher solves this issue. If you have an intel hda, this might help you installing the latest alsa drivers: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

edit: damn, 8.04 has 1.0.15. Maybe you still have to check the internal micro under sound preferences

---

### Post by nicholas.Platt on 2008-04-30
Hello,


I've already gone through all settings within System -> Preferences -> Sound and System -> Preferences -> Volume Control. Nothing is muted, in fact most are rather high. Still no sound through the headphone port, however... :(

---

### Post by mkrahmeh on 2008-05-01
Hi
am having the very same problem on my ACER aspire 4920 laptop
i tried to install alsa automatically through an executable install file..but ddnt work (the installation not the headphone)
actually it savaged the existing sound modules, so i cant operate sound files now :-)
the system diagnosed the problem as: 

libasound.so.2 : cannot open shared object file : no such file or directory

how can i recover this problem ?? before going with installing the alsa manually 
thx

---

### Post by nicholas.Platt on 2008-06-02
Wondering if this problem has been solved yet?

---

### Post by Nepherte on 2008-06-02
Sorry that I've lost my eye on this thread. There should exist a solution for your problem.

1. Let's find out which model of sound card you use:
```
cat /proc/asound/card0/codec#* | grep Codec
```

The output on my sony vaio sz6 looks like:
```
SigmaTel STAC9872AK
```
Of course yours might look differen.

2. Search for your model on this site: [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

3. Take a look at the model type options and take the one that fits best to your laptop, for example 'sony' or 'vaio' or the like.

4. Open up /etc/modprobe.d/alsa-base:
```
sudo gedit /etc/modprobe.d/alsa-base
```
and add ```
options snd-hda-intel model=MODEL
``` to the end of the file, assuming it is an intel hda sound card which is most likely the case with your sony laptop. Restart your laptop and let's pray it has fixed your problem.

---

### Post by nicholas.Platt on 2008-06-02
Thanks very much for the quick reply.

Following your steps...
1. I received the following for my model:
> Codec: SigmaTel STAC9872AK
Codec: Conexant ID 2c06

Noticing our model numbers were the same, I disregarded the second codec, and moved on.

2.,3. I found the model on line number 1021. Because I don't have an AR series, I assumed the model type "sony" fits my issue.

4. I have the file open, but I'm not sure where to add the line. Can you confirm this:
> # Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
**options snd-hda-intel model=STAC9872**
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

If so, what was the point of steps 2 and 3?

Perhaps it should be this?
> 
**options snd-hda-intel model=STAC9872 sony**


Again, thanks for the assistance. :)
**-- Edit:** Tried the first effort, no change. I'll try the second now...
I have tried the following with no results. The second actually disabled all sound...
> 
options snd-hda-intel model=STAC9872
...
options snd-hda-intel model=STAC9872 sony
...
options snd-hda-intel model=sony


Have I done something incorrectly?
Or is there another solution?

---

### Post by Nepherte on 2008-06-02
If you look more closer to the list of all those sound card models, it says '**vaio**' under STAC9872.

**Remove the following lines f you have added these lines yourself**:
```
options snd-hda-intel model=STAC9872
options snd-hda-intel model=STAC9872 sony
options snd-hda-intel model=sony
```

**Now add the correct line at the end of the file**:
```
options snd-hda-intel model=vaio
```

Reboot and you should be fine.

---

### Post by nicholas.Platt on 2008-06-02
Golden! Thank you so much, I really appreciate your long-term support. :)

---

### Post by glbrighenti on 2008-07-27
> **Nepherte said:**
> If you look more closer to the list of all those sound card models, it says '**vaio**' under STAC9872.

**Remove the following lines f you have added these lines yourself**:
```
options snd-hda-intel model=STAC9872
options snd-hda-intel model=STAC9872 sony
options snd-hda-intel model=sony
```

**Now add the correct line at the end of the file**:
```
options snd-hda-intel model=vaio
```

Reboot and you should be fine.

worked perfectly too on my vaio fz-340
thanx a lot!!

---

### Post by colin.bellinger on 2008-08-26
Hi, I have a sz640 running Ubuntu 8.04. The cat /proc/asound/card0/codec#* | grep Codec output is:

Codec: SigmaTel STAC9872AK
Codec: Conexant ID 2c06

Initially I had sound, but not through the headphones. After adding 

options snd-hda-intel model=vaio

I have no sound.

---

### Post by colin.bellinger on 2008-09-20
Is this thread still active?

---

### Post by banhbau01 on 2008-09-22
I hope this thread is still active! I've tried the steps mentioned above on my toshiba satellite laptop, but still no sound out of the headphones. Perhaps I'm not adding the the right model after: options snd-hda-intel model=MODEL   

I've tried Satellite, satellite, and toshiba. No luck so far. 

When I try to find out what sound card I have this is what I get:

 cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20551 (Waikiki)

Anyway, I'm a noob to most of this, so if someone could point out what I'm doing wrong I'd appreciate it!

Thanks

---

### Post by nrayever on 2008-12-27
> **Nepherte said:**
> Sorry that I've lost my eye on this thread. There should exist a solution for your problem.

1. Let's find out which model of sound card you use:
```
cat /proc/asound/card0/codec#* | grep Codec
```

The output on my sony vaio sz6 looks like:
```
SigmaTel STAC9872AK
```
Of course yours might look differen.

2. Search for your model on this site: [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

3. Take a look at the model type options and take the one that fits best to your laptop, for example 'sony' or 'vaio' or the like.

4. Open up /etc/modprobe.d/alsa-base:
```
sudo gedit /etc/modprobe.d/alsa-base
```
and add ```
options snd-hda-intel model=MODEL
``` to the end of the file, assuming it is an intel hda sound card which is most likely the case with your sony laptop. Restart your laptop and let's pray it has fixed your problem.

Great tutorial Nepherte. Thanks a lot for your instrucions. They worked like a charm with my brother's laptop. It is a sony VGN-NR310FH and i'm using Intrepid Ibex.

---

### Post by bhanu3112 on 2008-12-27
hey dude thanks for your replies
I have got the same problems but not able to sort them out.I have got HP dv-5 laptop
can you help me out?

---

