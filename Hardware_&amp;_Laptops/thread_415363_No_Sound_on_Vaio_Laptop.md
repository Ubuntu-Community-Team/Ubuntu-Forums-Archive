---
title: "No Sound on Vaio Laptop"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by Orochi on 2007-04-20
I just installed Feisty on my Sony Vaio laptop, and the sound does not appear to work. Is there a way to fix this?

---

### Post by jdawdy on 2007-04-22
What model of Vaio?  Have you searched Google and Launchpad for similar problems with your model?  Are you using a docking station (my VGN-A60GP does not have sound when docked)...What are your sound settings...ALSA, OSS...?

Jim

---

### Post by Adhémar on 2007-04-23
Hello guys !

I've the same problem. Sound doesn't work with my brand new vaio on kubuntu. The soundcard is however well detected, as a quick lspci shows:

```
augustin@vaio:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

I think there is something wrong with kmix, because i can't for instance disable the PCM channel.

I'll let you know if I find something new.

Oh, btw, this is my first post here. I am not a native english speaker so forgive my mistakes. I'm working with kubuntu since breezy and i'm already part of the (very active) [french-speaking ubuntu community](http://www.ubuntu-fr.org/) :) 

Adhémar

---

### Post by Adhémar on 2007-04-23
Ok, i got it working on my computer.

First, check your soundcard. 

```
augustin@vaio:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation **82801G** (ICH7 Family) High Definition Audio Controller (rev 02)

```

The model of this soundcard is then 82801G, and alsa doesn't seems to be fully aware of that. So, let's add a  line to /etc/modprobe.d/alsa-base.

```
sudo vim /etc/modprobe.d/alsa-base
```

and add the following line at the end of the file

```
options snd-hda-intel model=laptop-eapd
```

Now, just reboot and everything should be fine. I found this solution [here [fr]]("http://doc.ubuntu-fr.org/materiel/chipset_intel_hda_realtek").

Adh'

---

### Post by chriswyatt on 2007-05-02
Didn't work :( .  I have an HP dv2058ea laptop btw, it has the same chipset.  Sound worked (sort of) with last Ubuntu Edgy, I usually needed to plug and unplug my USB soundcard to get the damn thing to work (internal sound that is).

I heard talks that Realtek were going to assist with making better Linux drivers for their chipsets, I hope this materialises soon.

---

### Post by Vankata on 2007-06-11
Hi guys,

I have the same problem on my VAIO VGN-B1XP. I hardly hear sound using earphones - it's a very weak sound and no one of the mixer controls can change it. It seems the problem is in the mixer (som uncontrolled mutting?!). Adding that line at the end of alsa-base did not work for me.

---

### Post by Fliipn on 2007-06-12
Im in the same boat.. I have the same car on my Toshiba u205 and adding that line didn't work..

---

### Post by crab on 2007-06-12
Similar problem on a Vaio VGN A197XP. sound stopped working after last weeks Kernel update:

"No volume control GStreamer plugins and/or devices found." 

when using the volume control and this with alsamixer:

"alsamixer: function snd_ctl_open failed for default: No such device"

thanks!

crab

---

### Post by crab on 2007-06-13
Solved the problem on my Vaio VGN - hope its useful:



 1. "sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils"

2. "sudo apt-get install linux-sound-base alsa-base alsa-utils"

reboot

---

### Post by mfs_bg on 2007-06-22
> **Adhémar said:**
> Ok, i got it working on my computer.

First, check your soundcard. 

```
augustin@vaio:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation **82801G** (ICH7 Family) High Definition Audio Controller (rev 02)

```

The model of this soundcard is then 82801G, and alsa doesn't seems to be fully aware of that. So, let's add a  line to /etc/modprobe.d/alsa-base.

```
sudo vim /etc/modprobe.d/alsa-base
```

and add the following line at the end of the file

```
options snd-hda-intel model=laptop-eapd
```

Now, just reboot and everything should be fine. I found this solution [here [fr]]("http://doc.ubuntu-fr.org/materiel/chipset_intel_hda_realtek").

Adh'


Thanks for the tips

my problem solved
 I'm using hp v3105

---

