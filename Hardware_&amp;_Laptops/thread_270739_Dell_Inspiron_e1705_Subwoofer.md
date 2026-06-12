---
title: "Dell Inspiron e1705 Subwoofer"
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by tekian on 2006-10-03
Hey there. First off, this is my first post ;D Yay.

I've read over numerous forums, gone through #ubuntu on freenode, and read over every piece of documentation I could find. However, I cannot get my Dell Inspiron e1705's subwoofer to work at all. The front two speakers work great/perfectly. However, the small subwoofer on the bottom of the laptop next to the battery bin fails to produce any sound whatso ever. I've looked through alsa-mixer and cannot find any slider for "Mono Master", which I've read is the slider for the sub, anywhere.

I don't know what else to include really, but a reply on what I should would be nice =). Or maybe a solution, I dunno.

Thanks in advance ^_^

---

### Post by vayu on 2006-10-03
> **tekian said:**
> Hey there. First off, this is my first post ;D Yay.

I've read over numerous forums, gone through #ubuntu on freenode, and read over every piece of documentation I could find. However, I cannot get my Dell Inspiron e1705's subwoofer to work at all. The front two speakers work great/perfectly. However, the small subwoofer on the bottom of the laptop next to the battery bin fails to produce any sound whatso ever. I've looked through alsa-mixer and cannot find any slider for "Mono Master", which I've read is the slider for the sub, anywhere.

I don't know what else to include really, but a reply on what I should would be nice =). Or maybe a solution, I dunno.

Thanks in advance ^_^

Does it work in Windows?  Does it use a special Driver when in windows?

---

### Post by tekian on 2006-10-03
No, within Windows it works perfectly. Has its own slider and everything. I do have to download a driver from dell. The card itself uses a SigmaTel chipset. STAC9200 I believe. But I can't figure out if my card is SigmaTel, or HDA Intel Audio.

---

### Post by K.Mandla on 2006-10-04
I used to have an M170 and the subwoofer was controlled through Mono Master ... which I see you don't have. 

You might look up [terminal commands for amixer]("http://www.penguin-soft.com/penguin/man/1/amixer.html"), although I don't know that it would be any help. 

Try *amixer scontrols*, and look for something about a woofer, or perhaps master mono. Then try setting it with *amixer set name_of_control 75% unmute*. 

It might work, might not. I'm not real sure on this. I'm kind of shooting in the dark.

---

### Post by tekian on 2006-10-04
> **K.Mandla said:**
> Try *amixer scontrols*, and look for something about a woofer, or perhaps master mono. Then try setting it with *amixer set name_of_control 75% unmute*. 

Tried to see if anything with my subwoofer was listed. Only things that are:

```
tekian@tekian-laptop:~$ amixer scontrols
Simple mixer control 'Master',0
Simple mixer control 'PCM',0
Simple mixer control 'Capture',0
Simple mixer control 'Capture Mux',0
Simple mixer control 'Input Source',0
tekian@tekian-laptop:~$
```

I'm under the impression that my sound card driver isn't the right one. I did an aplay -l, and this was the result:

```
tekian@tekian-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Don't know if that helps any. Thanks in advanced again.

---

### Post by tekian on 2006-10-08
Bump. Still need help ;_; Cant find a thing on how to fix this. Is there just no driver that supports e1705 sound cards yet?

---

### Post by SnowPunk98 on 2007-02-12
I have the same problem/question anyone know?

---

### Post by fmaste on 2007-02-20
Edit the file /etc/modprobe.d/alsa-base

    sudo nano /etc/modprobe.d/alsa-base

Add the line

    options snd-hda-intel model=ref

Now reboot your computer
Open the volume control that is next to the clock (If it is nos there add it with right click and Add to panel)
Go to File -> Change device and select HDA Intel (Alsa mixer)
then go to Edit -> Preferences and check the one that is LFE, is the subwoofer
unmute it and start playing your favorite music
If LFE is not there (Like it happened to me) follow this HOWTO and install the newest version of Alsa: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
and when says "Manually tell the driver which flavor you are using" change 3stack with ref

For more info or to change the way your volume buttons behave go here [http://ubuntuforums.org/showthread.php?t=335285]("http://ubuntuforums.org/showthread.php?t=335285")

---

### Post by PhrankDaChickenGeek on 2007-02-21
> **fmaste said:**
> Edit the file /etc/modprobe.d/alsa-base

    sudo nano /etc/modprobe.d/alsa-base

Add the line

    options snd-hda-intel model=ref

Now reboot your computer
Open the volume control that is next to the clock (If it is nos there add it with right click and Add to panel)
Go to File -> Change device and select HDA Intel (Alsa mixer)
then go to Edit -> Preferences and check the one that is LFE, is the subwoofer
unmute it and start playing your favorite music
If LFE is not there (Like it happened to me) follow this HOWTO and install the newest version of Alsa: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
and when says "Manually tell the driver which flavor you are using" change 3stack with ref

For more info or to change the way your volume buttons behave go here [http://ubuntuforums.org/showthread.php?t=335285]("http://ubuntuforums.org/showthread.php?t=335285")

Thanks so much!  Nice to have the subwoofer back
This worked on a e1705 running edgy eft 6.10

---

### Post by jokez on 2007-03-08
double click volume control click on options, then down to properties and then click on subwoofer. And now you should be able to control your subwoofer.

---

### Post by helixed on 2007-06-15
I followed these instructions and they worked for enabling my subwoofer, but the master volume control seems to only control the front two speakers.  How can I tie the master volume to the LDE speaker?

Thanks,

Helixed

---

### Post by fmaste on 2007-07-01
> **helixed said:**
> I followed these instructions and they worked for enabling my subwoofer, but the master volume control seems to only control the front two speakers.  How can I tie the master volume to the LDE speaker?

Thanks,

Helixed

The little problem is that the master volume is not working as the master one. what you can do is make then work in parallel, both Master and LFE go up and down at the same time. To do this right click on the volume icon (by default near the clock) and select Prefefences, select the one that says Alsa mixer and them select Master and by holding CTRL on you keyboard select also LFE. Now if you also want this behavior with your volume keys do the same the lower part of the device section in System->Preferences->Sound.

You can also select PCM instead of Master and LFE, play a little with the different combinations and select the one you prefer, I prefer Master and LFE.

---

### Post by leo_rockway on 2007-07-30
i tried doing this and it worked for me until i updated alsa... now lfe is gone and i dont know what to do to make the subwoofer work again, any suggestions?

EDIT: it wasn't alsa, it was the kernel. i'm on 2.6.22-12 right now and this happened when i updated from  2.6.20-15 to 2.6.20-16. all the kernels after that had the same problem, including the one i'm using now.

---

