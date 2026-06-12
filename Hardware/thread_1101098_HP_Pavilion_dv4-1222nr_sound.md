---
title: "HP Pavilion dv4-1222nr sound"
date: 2009-03-19
forum: Hardware
---

### Post by anthropop on 2009-03-19
I am technically capable and can't get sound to work properly in this laptop.  I have sound through the headphone jack but not the speakers.  I have read all of the many posts with this type of problem, but none of the solutions fix it for this laptop.  I believe there may be a new bug or bios problem for this model as there are no posts regarding this model.

Vista was pre-installed and sound works through both the headphone and the built-in speakers.  I have the following configuration after installing ubuntu:

Ubuntu rev: 8.10
Kernel rev: 2.6.27-11-generic
Alsa rev: tried both and upgraded from 1.0.17 to 1.0.19
Upgrade script rev: 1.16

alsa-base added lines:
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-m4
options snd-hda-intel enable_msi=1


I also tried these 3 model values for the "model" (tested one at a time in alsa-base):
options snd-hda-intel model=dell-m4-1
options snd-hda-intel model=hp-dv4
options snd-hda-intel model=hp-dv41222nr

The upgrade script was successful in upgrading alsa but it did not help.  Actually it broke the sound icon on the keyboard so it is "muted" even when it is not actually muted in the volume/mixer control.  I also tried to select all output paths through the sound control.

The output of aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

My run from also-info.sh (version 0.4.56):
Your ALSA information is located at [http://www.alsa-project.org/db/?f=6ef6fbf4c329c1cf6bc02a61287750067b1d19c6](http://www.alsa-project.org/db/?f=6ef6fbf4c329c1cf6bc02a61287750067b1d19c6)

I also will upload my output of uxchecker.  I don't know how to file a bug report so I am hoping this is the starting point!  Thanks!!

---

### Post by anthropop on 2009-03-19
I attached uxchecker-1 and uxchecker-2 output files from the uxchecker utility.  I had to break them up into the two parts to upload them.

---

### Post by markbuntu on 2009-03-20
There is a long ongoing thread about the dv4 here. 

[http://ubuntuforums.org/showthread.php?t=984538](http://ubuntuforums.org/showthread.php?t=984538)

It is better to keep information from becoming fragmented by joining an ongoing thread instead of starting a new one.

---

### Post by anthropop on 2009-03-20
That seems reasonable if the problem is similar and if you are only taking the steps outlined on the one thread.  In my case I took steps compiled from 3 threads, most of them from a thread that was not specific to any one model. So do I post to all 3 threads or start a new thread?  I guess your point is that it is better to post to a related model laptop, which I'm glad to do if that is the convention.  


> **markbuntu said:**
> There is a long ongoing thread about the dv4 here. 

[http://ubuntuforums.org/showthread.php?t=984538](http://ubuntuforums.org/showthread.php?t=984538)

It is better to keep information from becoming fragmented by joining an ongoing thread instead of starting a new one.

---

### Post by jharvey71 on 2009-03-22
I am having the same problem.  New HP dv4-1222nr, replaced Vista with Linux, everything functioning properly except for the sound.  I too followed all advice on the other 3 threads resolving this problem for other model computers (including dv4-1224nr), but nothing has resolved my issue.

---

### Post by anthropop on 2009-03-22
That is why I started a new thread for this model.  I know enough about Linux that this did not appear to be the same problem as previous models and their related fixes.  I guess we will now see how well the GNU system works for resolving this type of issue!  

> **jharvey71 said:**
> I am having the same problem.  New HP dv4-1222nr, replaced Vista with Linux, everything functioning properly except for the sound.  I too followed all advice on the other 3 threads resolving this problem for other model computers (including dv4-1224nr), but nothing has resolved my issue.

---

### Post by bosox on 2009-04-04
This thread might help:

[http://georgia.ubuntuforums.org/showthread.php?t=1073090](http://georgia.ubuntuforums.org/showthread.php?t=1073090)

---

### Post by bosox on 2009-04-04
I'm contemplating purchasing this notebook at Staples tommorow. Are you guys (with the DV4 1222nr) experiencing any issues other than sound? It looks like from the other thread some DV4 (not 1222nr) user is experiencing low throughput with wifi.

Any feedback is appreciated. Thanks!

---

### Post by htc5555 on 2009-04-08
Same problem here. DV4-1222nr, got dual boot on it (vista and ubuntu), works fine with vista, in ubuntu I get sound from the headphone jack but no sound from the speakers.

Already tried a couple of steps from the other threads, but this seems to be something else entirely


i'm also having trouble connecting to wireless networks with Shared Key authetication (instead of the Open Key), both in windows and ubuntu... but thats a whole new Thread

---

### Post by Iowan on 2009-05-06
Just finished download/install of Jaunty on my dv4-1222nr. Unsurprisingly, I'm having same sound issues.  Thought I had NO sound until I turned up headphones.  Mute button doesn't change color (mine is stuck on red), but that's for another thread...

Update: [This]("http://georgia.ubuntuforums.org/showpost.php?p=6860920&postcount=11") one got my speakers working - and the mute button turned white... but won't turn red when muted...

Updated update: Tried editing the line:```
options snd-hda-intel model=dell-m4-1 
``` to read "model=hp-dv4" or "model=hp-dv5" and speakers quit.  Put it back - speakers still don't work. :(

Every time I say it works, then it quits.  When I say it quit, then it starts again.  Guess better wait for awhile to see what kind of mood it's in...

---

### Post by sotoj159 on 2009-11-13
I HAD the same problem with my hp pavilion 1222-nr.  I dont know what i did, but both my speakers and headphones work properly; also, the mute button turns orange when mute, and white when not mute.   The only thing i can think of that i did was upgrade to Ubuntu 9.10......maybe that's what fixed it...

---

