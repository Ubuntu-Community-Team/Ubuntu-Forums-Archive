---
title: "*THE* Laptop Sound Coming From Headphones and Speakers Thread"
date: 2011-01-30
forum: Hardware
---

### Post by htedrom on 2011-01-30
hey all, so I had the problem of sound coming out of both the laptop speakers and headphones when my headphones are plugged in on my HP G60-549DX.

I fixed the problem when I first got the laptop (I think) by adding this to /etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel model=dell-vostro
```

however I'm not sure what happened recently; I tried getting my mic working, I might have played around in the alsamixer, something may have updated to a new version (although I checked my synaptic log and didn't see anything too suspect), but now the problem is back with a vengeance. I've googled around, and have tried all of these lines individually in alsa-base.conf:
```

#options snd_hda_intel model=auto
#options snd_hda_intel model=hp-dv5
#options snd-hda-intel index=0 model=toshiba position_fix=1
```

but to no avail. 

```
anewson@melvin:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
anewson@melvin:~$ 
```

alsamixer has no "front" channel or anything where I can manually turn down the laptop speakers and just keep the headphones going, and while that would be an inelegant fix, I'd be happy with it... Also I've messed with the Output options in the gnome volume mixer, but also no dice. I can't listen to music while I study in the library, which is freaking debilitating for me.

thanks for the help =)

---

### Post by lidex on 2011-01-30
What I have for G60 is this:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```
However you may have mis-configured something else. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by htedrom on 2011-01-31
hey lidex, thought I posted a reply already but guess it didn't go through... thanks for the response, I've tried your line in alsa-config, but no dice.

here's the link to the diag script output

[http://www.alsa-project.org/db/?f=2ef9fc5ad86101970522cd439c9917c9a5cf7a79](http://www.alsa-project.org/db/?f=2ef9fc5ad86101970522cd439c9917c9a5cf7a79)

---

### Post by lidex on 2011-01-31
Alsa is not doing the best job of recognizing your codec and is using the generic parser. Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by slooksterpsv on 2011-01-31
Gateway NV53
Added the following lines to /etc/modprobe.d/alsa-base.conf

```

options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes

```

That fixed an issue with the Microphone too, not sure if that would work for you as well.

---

### Post by htedrom on 2011-01-31
thanks for the responses all. I just tried updating alsa (edit: the alsa kernel modules as suggested above, not actual alsa) but it complained about some missing backports, 
```

linux-backports-modules-alsa-lucid-generic:
 Depends: linux-backports-modules-alsa-2.6.32-28-generic  but it is not installable
```

and a quick google search landed me here:

[http://ubuntuforums.org/showthread.php?t=1676135](http://ubuntuforums.org/showthread.php?t=1676135)

could this be related? it's late now I've got to crash but I'll take a look tomorrow

---

### Post by htedrom on 2011-01-31
well I downgraded the kernel and now it's working again, so I guess that settles it. Cheers for the help all!

---

