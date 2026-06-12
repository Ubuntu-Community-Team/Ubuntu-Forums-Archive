---
title: "HP dv7t Subwoofer not working/GRUB question"
date: 2009-11-28
forum: Hardware
---

### Post by Lancelot59 on 2009-11-28
Hi there everyone. I recently put Ubuntu on my machine as a dual boot with Windows 7, and I have two things that need to be solved:

1. The sub on my laptop doesn't work anymore. All the other threads with audio issues have the speakers not working at all. My main speakers are working, just not the sub. HP support says I'm using an intel chipset, but I can't find a linux version of the drivers, either from Intel, or the IDT High-Definition Audio CODEC Driver that windows uses. 

2. I had to reinstall Ubuntu after I broke it, and now GRUB has two entries for Linux. How can I delete those entries?

Thanks in advance.

---

### Post by naiku on 2009-11-28
Ah ha, someone with the same issue as me! I also have an HP Pavilion DV7 and noticed a couple days ago that the sub is not working. 

I have found one other thread of a user with the same problem, but no one replied and they have no solution. I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=1236208](http://ubuntuforums.org/showthread.php?t=1236208) to add 3 lines to the alsa-base.conf file, but I don't think that it fixed the issue with the subwoofer not working.

---

### Post by Lancelot59 on 2009-11-28
Yeah, all the methods I've seen have had people saying that they don't work.

---

### Post by Lancelot59 on 2009-11-29
Does anyone have any ideas on how to fix this?

There must be some intel chipset drivers available for Linux, but I can't find any.

---

### Post by iaswni on 2011-03-31
Hey guys, I understand that this is quite an old thread, but I haven't found a workable solution yet to this and I've been searching like crazy.

I've tried everything suggested in other threads too but it doesn't fix the problem, nothing changes.
The sound is low quality and the subwoofer doesn't work at all...

Is there a way maybe to install the proprietary drivers for the sound card?

Thank and best regards

---

### Post by Lancelot59 on 2011-03-31
> **iaswni said:**
> Hey guys, I understand that this is quite an old thread, but I haven't found a workable solution yet to this and I've been searching like crazy.

I've tried everything suggested in other threads too but it doesn't fix the problem, nothing changes.
The sound is low quality and the subwoofer doesn't work at all...

Is there a way maybe to install the proprietary drivers for the sound card?

Thank and best regards
More information would be help us help you. I guess you're running on a dv7t. How old is the machine?

---

### Post by ClyN3il on 2011-03-31
Yeah, I'm having the same problem. HPdv7t. Subwoofer huh? That makes sense. I was just wondering why the sound was so quiet and bad. All the "sound problem" threads are about sound not working, or other obvious problems--my sound works...I can hear it, there are no weird pops or hisses or anything...it sounds normal...just quiet, and not very good. I have to turn the main volume up past 100% to the maximum, and VLC's volume to 400%, but then the quality gets worse, and it's sort of loud enough, but still not very loud. If plug in headphones without changing the volume, it's almost enough to deafen me. If I then turn the volume way down, it sounds great with headphones.

Help would appreciated, as this problem makes Ubuntu practically worthless for listening to music or watching videos.

---

### Post by Lancelot59 on 2011-04-01
Well I didn't have many issues. I just had to edit the alsaconfig file and install the backports. Now that I follow the link in the second post the instructions aren't all too clear. 

Now I know at some point HP started using some beats audio system, my laptop is before that point. I can't guarantee that those same steps will still work. 

This is a set of notes I made for just such an occasion. I've cut out certain things involving an equalizer and some other stuff that isn't relevant:

```
STEPS FOR HP-DV7t
Forum sticky: http://ubuntuforums.org/showthread.php?t=1073090
The thread I made: http://ubuntuforums.org/showthread.php?t=1353340

General Steps:

Need to install the backports for the alsa drivers: ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz
That is posted in the thread. There is a copy kept in the ubuntu resource files.

Preferably use the one for the latest kernel build off of the repositories.
'linux-backports-modules-alsa 2.6.31-22-generic' is the latest for karmic headers. There should be a copy in the ubuntu resource files. 
Use local copies only if the synaptic repositories fail.


Edit the ALSA Config File

Terminal: gksudo gedit /etc/modprobe.d/alsa-base.conf

change: options snd-hda-intel power_save=10 power_save_controller=N
to read: # options snd-hda-intel power_save=0 power_save_controller=N

add: options snd_hda_intel model=hp-dv5 to the end of the file

in terminal: sudo reboot

```That's all I had to do. Then I go into terminal and run:
```
alsamixer
```
**NOTE**: MAKE SURE YOU GET THE VERSION OF THE BACKPORTS THAT IS THE SAME AS YOUR SYSTEM KERNEL!!! Also, try editing the file BEFORE getting the backports.

It's a terminal program that is a mixer for the various bits of hardware. For me the sub shows up as "Bass Speaker". I just unmuted that and I was set. I also recommend muting "Beep" if you have any issues with random noises. Just press M and leave the volume up somewhere.

---

### Post by lidex on 2011-04-02
Generic fix for Dv7:
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=hp-dv5 enable_msi=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

More here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio)

---

### Post by Viper92Z on 2011-04-03
That is caused by the internal audio hardware, so what I tried to use ALSA mixer, give it a try it worked on my DV7.


```
sudo apt-get install gnome-alsamixer
```

HTH.

---

