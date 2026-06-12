---
title: "Volume change way high and almost silent at 50%"
date: 2008-09-11
forum: Hardware
---

### Post by bismark on 2008-09-11
I've used both Xubuntu & Kubuntu and with the volume control in them I could modify the steps that a key press changed it.  With KDE you could hold down CTRL (i think) and get a single increment or just adjust normally to change by 5 or 10.

Now with Ubuntu I hit volume down on my keyboard (MS 4000) or on the laptop keys and it changes dramatically.  Also at 50% it's almost silent and it seems to have no change in volume below 50% until muted. I'm running pulseaudio but I noticed the same problems when setup through ALSA (never tried OSS).

I'm wondering if there is a configuration setting that I'm missing somewhere and if anyone could point me in the right direction.

My laptop is a Lenovo t60p using the Intel HDA module (snd_hda_intel).

Thanks
Bismark

---

### Post by tobiax on 2008-10-15
I'm having the exact same problem, and finding it hard to see a good reason beyond bad drivers :-)

---

### Post by bismark on 2008-10-15
I don't know if it's the drivers or the hardware for the volume at 50% is basically mute but I have changed the dramatic volume steps.

Open up Configuration Editor and then go to /apps/gnome_settings_daemon and modify volume_step.  I set it to 3 and it works quite a bit better.

---

### Post by Amorget on 2008-10-15
I am having the some problem.

I ran the Configuration Editor, but I don't see a volume_step in the gnome_settins_deamon

---

### Post by bismark on 2008-10-15
> **Amorget said:**
> I am having the some problem.

I ran the Configuration Editor, but I don't see a volume_step in the gnome_settins_deamon

I don't know what puts that setting there but that's where I found it.  Maybe you could try creating it?  I've attached a picture of what I see.

---

### Post by Amorget on 2008-10-15
Ahhh, okay, found it.

Unfortunately no help, volume is still basically mute at 50%.

Thanks though!!

Douglas

---

### Post by bismark on 2008-10-16
> **Amorget said:**
> Ahhh, okay, found it.

Unfortunately no help, volume is still basically mute at 50%.

Thanks though!!

Douglas

Yeah this won't help the mute @ 50%, it just helps the dramatic jumps when changing volume from the keyboard.

---

