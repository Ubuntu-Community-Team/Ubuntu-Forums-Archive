---
title: "No sound, everything seems fine tho........?!"
date: 2009-05-11
forum: Hardware
---

### Post by erikenglund on 2009-05-11
I have some serious issues with my sound... Everything seems to work fine, the driver finds the soundcard, the pavucontrol starts fine, lshw -c multimedia gives this:

```
sudo lshw -c multimedia
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

I have tried to check all my mixers, and none seems to be muted. If I start playing something I can see that it is playing in the pavucontrol, but I can't hear any sound. I have tried to unplug the spakers for the internal laptop sound but no use. I have searched around a lot but haven't found anything that helps me, also this is a clean install of 9.04!

It might be something really stupid, but I just cant figure it out?!

Here's my configuration: 

[http://www.alsa-project.org/db/?f=d9c66a65490ea33e2786c759e390638097b85761](http://www.alsa-project.org/db/?f=d9c66a65490ea33e2786c759e390638097b85761)

---

### Post by Forgotten Path on 2009-05-11
Do you have a HP Pavilion?  I had a similar problem.

Open volume control.
Go to Edit->Preferences.
Make sure PCM, PCM-2, Headphones, and Speaker are checked.
Then, in Volume control, recheck to make sure nothing is muted.

On my HP Pavilion dv2000t, PCM controls all outputs at once, PCM-2 and Speaker together control the speakers, and Headphones controls the headphone output.  My PCM track wasn't visible and was muted.

*Edit*
No, wait, Headphone doesn't appear to do anything...  But PCM definitely has to be turned up for anything to work.

If that isn't it, try [Comprehensive Sound Problem Solutions Guide v0.5e]("http://ubuntuforums.org/showthread.php?t=205449").  Good luck!

---

### Post by erikenglund on 2009-05-11
Thanks a lot for you reply.

Yes, I do have a HP-Pavilion, I have a DV3600 tho, and the settings seems slightly different from yours. I'll attach a screenshot from my alsamixer!

I also tried that guide, and everything seems to be fine :S

Do you think uninstalling pulseaudio might solve the problem?

---

### Post by Forgotten Path on 2009-05-11
Hmmm.  I honestly don't know whether uninstalling PulseAudio may help or not. :confused: You'll have to consult someone more experienced now...  Sorry I couldn't help at all! :(

---

### Post by erikenglund on 2009-05-11
> **Forgotten Path said:**
> Hmmm.  I honestly don't know whether uninstalling PulseAudio may help or not. :confused: You'll have to consult someone more experienced now...  Sorry I couldn't help at all! :(

No worries, thanks anyway :)

I don't know if this helps someone, but I get this when I do "sudo /etc/init.d/pulseaudio restart":

```
$ sudo /etc/init.d/pulseaudio restart
 * PulseAudio configured for per-user sessions
```

I read somewhere that it isn't supposed to be per-user based? Does someone know if that is still valid and what I should do then?!

---

### Post by belock on 2009-06-07
Hello, Have you finally solved out the sounds problem? I've just got my new bran hp dv3600 and as soon as I got home I installed the new ubuntu, but I don't have sound on it.

thanks

---

### Post by erikenglund on 2009-06-08
> **belock said:**
> Hello, Have you finally solved out the sounds problem? I've just got my new bran hp dv3600 and as soon as I got home I installed the new ubuntu, but I don't have sound on it.

thanks

Yes, after a lot of trying I finally installed a newer version of ALSA through the upgrade script found here: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Hope that works for you as well! :D

---

