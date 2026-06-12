---
title: "sound problems"
date: 2008-10-15
forum: General Help
---

### Post by Tag_yer_dead on 2008-10-15
hey guys
I've been on ubuntu for about a year now and nothing like this has ever happened to me... the sound has just stopped.

It worked as of yesterday and now it doesn't, i have the alsa drivers so im not sure what gives.  Any ideas?

Thanks,
Corey


P.S. I need music or I will be driven insane

---

### Post by phidia on 2008-10-15
There is a sound troubleshooting howto [here]("http://ubuntuforums.org/showthread.php?t=205449") (it's rather long) and the somewhat shorter wiki guide [here]("https://help.ubuntu.com/community/SoundTroubleshooting"). Hope that's useful.

---

### Post by Psykotik on 2008-10-16
Same issue here. Sound card integrated Realtek ALC882 on a gigabyte mainboard.

It was perfectly working before the update; tried many remedies, but still ill. Hope it's not dead.

---

### Post by kcox5342 on 2008-10-16
Me too.  Both my Ubuntu machines worked fine yesterday, after the update now my desktop is silent - which REALLY sucks because it's my mythtv box, as well as my Open Arena and Doom 3 machine.  But my laptop is fine.  Laptop is running 32-bit, desktop is 64-bit, both running Ubuntu 7.10.  If this is indeed a bug caused by yesterday's "restart is required" update (which was applied to both machines) then I hope there's a patch on the way post-haste.

When I open the Sound preference pane on the desktop machine and try the "test" button I get: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosing: Could not open resource for writing.

Trying the shorter wiki guide linked above, I get a success on aplay -l, so I go to alsamixer, but launching that just shows a terminal program that has nothing going on - there's no graphic EQ, left right & up & down do nothing, the only thing I can do is hit escape to exit it.  Digging around in Sound Preferences shows a number of the options on the Devices screen (such as Default Mixer Tracks) have Conexant CX8801 two times in the list with the other options... neither one works, of course.  I have two TV tuner cards in this box, perhaps that's why this option shows up twice?  Or is it accidentally installed twice which makes neither of them functional?  I just want to watch the debate wrapup from last night... help!!

Also I should mention that I tried the mythtv volume controls - [ and ] control its playback volume and, when working, pops up something on the screen saying "Volume 98%" or whatever.  This window doesn't pop up now.

(I'm editing this as I find more stuff - in response to the poster below me, my login sounds don't even work!)

---

### Post by thestig_992 on 2008-10-16
I have a similar problem; my login screen sound works, but nothing else. It was working earlier today though, before I updated

---

### Post by kcox5342 on 2008-10-16
Update... I've run  aplay -l and get the following:

**** List of PLAYBACK Hardware Devices ****
card 2: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

When I go to Sound Preferences and change Sound Events or Movies And Music to ALC883 Analog and hit "Test", I get a tone through my speakers, until I hit OK, but neither mythtv nor XMMS nor the system sounds in the Sound Prefs pane will play, just the tone.  I just tried opening an MP3 in VLC, xmms, neither works, but oddly enough xine works just fine, whether I have Movies And Music set to autodetect or ALC883 Analog.

Was yesterday's update a kernel upgrade?  I didn't see a new kernel in the list before I hit upgrade, but AFAIK that's the only thing that requires a reboot.  If so, would loading an older kernel solve the problem for all applications?  I can runs xine if I want to listen to an MP3, but Open Arena and mythtv are still silent, and they're my top priorities.

---

### Post by Psykotik on 2008-10-16
> **kcox5342 said:**
> 
Was yesterday's update a kernel upgrade?  I didn't see a new kernel in the list before I hit upgrade, but AFAIK that's the only thing that requires a reboot.  If so, would loading an older kernel solve the problem for all applications?  I can runs xine if I want to listen to an MP3, but Open Arena and mythtv are still silent, and they're my top priorities.

Yes. You can downgrade to the previous kernel (-19) and get back your sound.

---

### Post by thestig_992 on 2008-10-17
How do i downgrade my kernal?
In the grub boot menu i booted the x.x.x.19 kernal, and i have the same problem.

I can play embeded flash in my browser, and the 'login screen ready' sound plays, but nothing else.

---

### Post by kcox5342 on 2008-10-17
I tried booting with the x.x.x.14 kernel (the current one on the list being x.x.x.15) and still no sound.  

To others with this problem: which specific OS are you running?  Mine is Ubuntu 7.10 64-bit, with the laptop running Ubuntu 7.10 32-bit not having the problem.  I'm wondering if we're all on Gutsy or if this also affects Hardy users.

---

### Post by thestig_992 on 2008-10-17
Nope, im on hardy with the same issue.
I noticed thismorning that my update manager cant retreive the update info. is this somthing to do with the kernel problem?

---

### Post by kcox5342 on 2008-10-19
I'm not having any trouble retrieving the update info, so that's probably a separate issue on your part.

---

### Post by kcox5342 on 2008-10-23
Doing a little more digging on this very annoying problem... there's threads where other people have the same issues, but it's not all from the same time (some from earlier in this year) so it seems like this is the kind of thing that an upgrade can screw up, not the fault of the upgrade itself but something going wrong in the upgrade process.

I also found a suggestion to run dmesg... interestingly enough my output had a *lot* of lines which look like this:

[161202.638970] cx88_wakeup: 3 buffers handled (should be 1)
[161222.652360] cx88_wakeup: 3 buffers handled (should be 1)
[161263.503649] cx88_wakeup: 3 buffers handled (should be 1)
[169803.647479] cx88_wakeup: 3 buffers handled (should be 1)
[169815.634342] cx88_wakeup: 3 buffers handled (should be 1)
[170494.626625] cx88_wakeup: 3 buffers handled (should be 1)

---

### Post by Baltazar72 on 2008-10-31
*Just confirming .. I did a distro upgrade last night ... from 8.04 to 8.10 (ubuntu) .. And now my laptop is dead silent .. played around in sound-prefrences, and could not get any sound on any "tests" .. frustrating ..

---

### Post by kcox5342 on 2008-11-06
I did a distro-upgrade (7.10 to 8.04) and now there's login sounds and VLC has sound.  But Alien Arena, Open Arena, Doom3 and MythTV still don't.  When I select ALSA from the Sound preferences I still get the same error.  But Alsamixer finally does something for me - I can ramp up and down "playback" with the up and down arrow keys, although the left and right don't bring anything else up besides "playback".  It doesn't make any sound, but it's more than it had done under 7.10.

The Comprehensive Sound Problem Solutions Guide recommends 

```
cat /proc/asound/modules
```

Which gives me:
```

 0 cx88_alsa
 1 snd_usb_audio
 2 cx88_alsa
 3 snd_hda_intel
```

So now I have two cx88_alsa listings in there - perhaps that's part of the problem?

---

