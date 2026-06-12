---
title: "Fixing sound issues on the MSI GX660r series"
date: 2011-03-07
forum: Hardware
---

### Post by csantos.bh on 2011-03-07
When I first installed ubuntu 10.10 on my notebook (MSI GX660r-060us), I noticed that the audio quality was far below the one experienced on windows. Soon I realised that the sound was only coming from the subwoofer.

On this post, I will describe the solution I found for this problem, as well as its implications. Please note that this might work for other notebook models as well, so I'll try to be a little bit generic here.

**First step: Fix the alsa installation (Optional)**
If you have broken your alsa installation (so did I when trying to fix my issues), follow the steps under Getting the ALSA drivers from a *fresh* kernel on [this link]("http://ubuntuforums.org/showthread.php?t=205449"). Now reboot the system, and proceed to the next step if only your subwoofer is working. 

**Second step: Find the correct model for your alsa-base.conf**
This step is specific for GX660r owners. If you have some other notebook wich features an hda-intel soundcard, you can find a list of chip models [here]("http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD"). For a clue on your chip model, take a look in the alsamixer panel:
```
$ alsamixer
```
For example, this panel outputs the following information on my notebook:
Card: HDA Intel                                                                                                                                                                           Chip: Realtek ALC888

For the MSI GX660r, the model that worked best during my tests was targa-8ch-dig (I'll have to confess: I haven't tried all models in the list, so if you find another one that works better than targa-8ch-dig, please let me know).

**Third step: Set up the soundfix boot script**
Firstly, you'll need to know if this script will work for you. In order to check it, follow these steps:
[LIST=1]
[*]sudo gedit /etc/modprobe.d/alsa-base.conf
[*]Add this line to the end of the file: options snd-hda-intel model=YOUR_MODEl_HERE (in my case, YOUR_MODEL_HERE=options snd-hda-intel model=targa-8ch-dig)
[*]Save and close the file. 
[*]sudo alsa force-reload
[*]Run alsamixer on the terminal. Adjust the volumes to the max and try to play some audio. If your speakers start to work, go to the next step. Otherwise, you could try other settings in the alsamixer or test another model from the hda-intel list below.
[*]Turn your notebook off and on again. If the sound has stopped working once again, you'll need the script - go to the next step. Otherwise, I'd say your issue is solved.
[*] Remove the hda-intel model line from /etc/modprobe.d/alsa-base.conf (from steps 1 and 2).
[*] sudo gedit /etc/init.d/soundfix, add the following to this file (do not forget to replace the YOUR_MODEL_HERE part - once again, targa-8ch-dig is my current recommended model for the MSI GX660r):
```
cp /etc/modprobe.d/alsa-base.conf /tmp/alsa-base.conf
echo "options snd-hda-intel model=YOUR_MODEL_HERE" >> /etc/modprobe.d/alsa-base.conf
alsa force-reload
cp /tmp/alsa-base.conf /etc/modprobe.d/alsa-base.conf
```
[*] Make it run during the boot:```
sudo update-rc.d soundfix defaults
```
[/LIST]

**Drawback for this approach**
The script itself did not fix everything for me. Sometimes, when plugging my headphone jack, the subwoofer did not stop playing sound, so I had to manually disable it through alsamixergui.

Note that this is not a very elegant solution, but my main concern right now is to make the sound work. I wish to update this thread in the future with better solutions for this, but for now, I can just hope it will help many people out there.

---

### Post by Alex_Alex on 2011-03-20
Thank you csantos.bh, your post helped me.

My laptop is a MSI GX660r-427fr. I use "options snd-hda-intel model=targa-dig".
It fixed a part of the problem. However, when I plug headphone jack, the subwoofer continue playing sound too.

---

### Post by DaH-RaT on 2011-06-08
thank you so much everything worked as it said, ive been looking for a solution for my gx660-260us for a long time, very tired of windows 7 lol.

---

### Post by csantos.bh on 2011-10-17
I found out that some system updates might eventually break the fix. For instance, kernel updates will most likely break this fix, at least on my machine. An issue like the one described by Alex_Alex is a good sign that your fix is broken. Whenever that happens to me, I simply do the following:


[LIST=1]
[*]Reinstall the alsa driver:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
```
[*]From ubuntu documentation (I don't remember which page, though): [I]This may result in some other packages which depend on the sound-base and alsa-utils from being removed, such as gdm and ubuntu-desktop. If this happens, then do:

[/I]```
sudo apt-get install gdm ubuntu-desktop
```
[/LIST]
Hope that helps.

---

### Post by dwigyit on 2011-11-29
Best thing to stick into Alsa for the 660R is

```
options snd-hda-intel index=0
options snd-hda-intel model=acer-aspire-7730g
```

It doesn't break with updates and it correctly mutes the headphone jack. You do loose the extra audio out jack though, and I don't know of a way to fix that yet. It wont affect most people though because the headphone and mic jacks are all you need for most uses.

---

