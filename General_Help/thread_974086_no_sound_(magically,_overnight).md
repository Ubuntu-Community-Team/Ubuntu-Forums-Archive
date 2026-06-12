---
title: "no sound (magically, overnight)"
date: 2008-11-07
forum: General Help
---

### Post by Kymus on 2008-11-07
I upgraded to Ibex last night, and everything was fine. Ran things for a few hours, audio was fine.

Go to bed, turn the system off, turn it back on this morning and of course the magic computer goblin paid my box a visit last night because I am not getting any audio at all.

When I first booted this morning, I noticed that the sound was automatically muted, so I changed that, and I've of course fiddled with the volume and nothing. :confused:

I'm using the onboard sound from my motherboard (**Foxconn NF4UK8AA**), which the Sound Preferences says is *NVidia CK804 with ALC850 NVidia CK804*.

I've fiddled with every option under *sound playback* and every test has thus far produced no results.

---

### Post by Kymus on 2008-11-07
just an update...

I was browsing through the forum and found this suggestion:

```
sudo killall pulseaudio

sudo alsa force-reload

```

> and then go to System>Preferences>Sound and change everything to ALSA

Unfortunately, this produced no results >_<

---

### Post by Yellow Pasque on 2008-11-07
Did you update the kernel before you turned off your system? Make sure your card is seen with aplay and that lsw shows a driver/kernel module loaded for it:
```
sudo lshw -C multimedia
aplay -l
```

---

### Post by Kymus on 2008-11-07
Hi Temüjin,

Unfortunately, I know nothing about "kernel updating", so the answer to your question is probably *no*.

I'll boot over to my Ubuntu partition and try the code you mentioned and report back, thanks.

---

### Post by Kymus on 2008-11-07
Well, it seems to me that it is recognizing the hardware. Here's what it spit back at me:

```
kymus@Shouxing:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0

```

```
kymus@Shouxing:~$ sudo lshw -C multimedia
[sudo] password for kymus: 
  *-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0

```

---

### Post by niko7865 on 2008-11-07
I have this same problem (same hardware), sound stopped without rebooting or anything. Tried booting to an earlier kernel and still without sound. "sudo alsa force-reload" produced a few 'pops' from my speakers. Everything shows up in aplay and lshw/lspci. I'm at a loss as to what the problem is, works fine in dualboot windows xp.

---

### Post by Kymus on 2008-11-07
likewise niko, all I got was a pop :)

---

### Post by Yellow Pasque on 2008-11-07
Well, Ubuntu recognizes your card and the kernel driver is loaded (and someone else is reporting the same issue) This points to a problem with the ALSA module (snd-intel-8x0).

My advice would be to either file a bug with the Ubuntu devs in Launchpad or try OSS4 (an alternative to ALSA/PulseAudio): [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by niko7865 on 2008-11-08
Sound works after install OSS4, haven't tried all applications yet though.

---

### Post by tuwxyz on 2008-11-08
The same problem here. Pulse and ALSA stoped working.

My hw:
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

Last night I've installed these:
cups (1.3.9-2) to 1.3.9-2ubuntu1
cups-bsd (1.3.9-2) to 1.3.9-2ubuntu1
cups-client (1.3.9-2) to 1.3.9-2ubuntu1
cups-common (1.3.9-2) to 1.3.9-2ubuntu1
cupsys (1.3.9-2) to 1.3.9-2ubuntu1
cupsys-bsd (1.3.9-2) to 1.3.9-2ubuntu1
cupsys-client (1.3.9-2) to 1.3.9-2ubuntu1
libcups2 (1.3.9-2) to 1.3.9-2ubuntu1
libcupsimage2 (1.3.9-2) to 1.3.9-2ubuntu1
libcupsys2 (1.3.9-2) to 1.3.9-2ubuntu1
libpam-modules (1.0.1-4ubuntu5) to 1.0.1-4ubuntu5.2
libpam-runtime (1.0.1-4ubuntu5) to 1.0.1-4ubuntu5.2
libpam0g (1.0.1-4ubuntu5) to 1.0.1-4ubuntu5.2
linux-libc-dev (2.6.27-7.16) to 2.6.27-8.17
rhythmbox (0.11.6svn20081008-0ubuntu4.1) to 0.11.6svn20081008-0ubuntu4.2


[solved]
It was trivial. The PCM was muted after update in the mixer.

---

### Post by Kymus on 2008-11-08
Thank you for your suggestions Temüjin.

I have filed a bug report [here]("https://bugs.launchpad.net/ubuntu/+bug/295822"), and also, I experienced some issues with trying to install OSS4, which I posted about [here]("http://4front-tech.com/forum/viewtopic.php?p=10893#10893").

---

### Post by AlainJLEB on 2008-11-09
Hi there,

I have a similar issue with no working sound ... have already checked mute ;) ... alsa force-reload doesn't help and even give an error:
```
Terminating processes: 6187.  
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-devicesh: /lib/alsa/modprobe-post-install: not found
FATAL: Error running install command for snd_hda_intel                                                                                                                                                                                                          
 (failed).   
```
Below is the output of the 2 commands mentioned here before
```
lshw -C multimedia
  *-multimedia
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

What looks strange is the fact that, when running alsamixer, it is mentioning this:
```
&#9474; Card: HDA Intel                                                                                                                                                                                                                                                             &#9474;
&#9474; Chip: Realtek ALC889A                                                                                                                                                                                                                                                       &#9474;
&#9474; View: [Playback] Capture  All                                                                                                                                                                                                                                               &#9474;
&#9474; Item: Master [dB gain=-13.00]  
```
So ... why is one talking ALC885 and another ALC889. Would this be part of the problem?

---

### Post by Keith_Beef on 2008-11-16
This is a problem for me, too: sound has simply stopped working since I upgraded to Intrepid.:(

It worked in Feisty and in Gutsy, so well that I didn't make any notes of the settings. Now there is just silence.:confused:

I have a Gigabyte GA-P35-DS3P mainboard; the handbook lists "Realtek ALC889A codec".


```
$ sudo lshw -C multimedia

  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

```
$ lsmod | grep snd
snd_hda_intel         489264  2 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  14 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
```

Is it normal to have both snd_hda_intel *and* snd_pcm_oss modules loaded?

When I try looking in the sound mixer, I see several devices listed:
```
HDA Intel (Alsa mixer)
Realtek ALC885 (OSS mixer)
Playback: ALSA PCM on front (...
Capture: Monitor Source of ALS ...
Capture: ALSA PCM on front (...
```

I've tried each in turn (even the those named "Capture..."): no joy.

Help, please?


K.

---

### Post by Keith_Beef on 2008-11-16
Thinking back, I think it might have worked for a day or two...

I did an upgrade to 8.04 recently, then to 8.10 a few days ago, so I don't remember clearly if I ever had sound working.

So, imagining that sound had worked straight after install, and then stopped, I looked in Synaptic for packages I installed deliberately (i.e., not as part of the upgrade to 8.10).

Here's the log of what I removed tonight.

```
Commit Log for Sun Nov 16 22:10:23 2008


Removed the following packages:
freepats
gbsplay
gpsd
gpsd-clients
gpsdrive
libboost-filesystem1.34.1
libboost-regex1.34.1
libboost-thread1.34.1
libgdal1-1.5.0
libgps17
libmapnik0.5
libmapnik1d
libogdi3.2
mikmod
openstreetmap-map-icons-classic
openstreetmap-map-icons-square
proj
timidity
```

Still no sound, though. :(

K.

---

### Post by GnuSense on 2008-11-17
I did some updates last week on Hardy last week, and the update notification icon showed that I should reboot the computer, which I didn't do for a couple of days.  I'm guessing that means that my updates must have upgraded the kernel. Last night I shut the machine down.

When I tried to log in  this morning I was greeted by a white screen in the gnome desktop (which automatically starts compiz fusion).  I killed X with Ctrl+Alt+Backspace and logged in to the KDE desktop (which also whites out when I start compiz with fusion-icon).  I'm guessing the fglrx proprietary driver is unhappy for some reason.

And I noticed that I had no sound, xine couldn't initialize a driver in Amarok, Audacious didn't play music, there was no mixer available in kmix.  I tried playing around with the Kubuntu System Setting -> Sound Settings, including restarting sound, which didn't work (actually, it seemed to take forever, so I killed it). Why the heck doesn't Ubuntu use the old alsaconf command from Debian? 

What did work for me was switching /boot/grub/menu.lst from booting /boot/vmlinuz-2.6.24-21-386 to starting /boot/vmlinuz-2.6.24-21-generic.  CF now works and sound seems normal.  Hopefully the next kernel upgrade will work properly.  I'm guessing there were changes in the i386 kernel that didn't agree with my chipset.  FWIW, I have a RS780 chipset board, I believe an ASUS M3A78-EM AM2+ AMD 780G HDMI Micro Motherboard:

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

---

### Post by Keith_Beef on 2008-11-17
> **GnuSense said:**
> When I tried to log in  this morning I was greeted by a white screen in the gnome desktop (which automatically starts compiz fusion).  I killed X with Ctrl+Alt+Backspace and logged in to the KDE desktop (which also whites out when I start compiz with fusion-icon).  I'm guessing the fglrx proprietary driver is unhappy for some reason.

I noticed that, too... I got a message bubble that told me there was a problem loading the gnome configuration. I changed session at the login screen, started an Enlightenment session (that brought back memories) and in e eterm I renamed my .gnome2 directory to not_working_gnome2. I thought this would have lost all my desktop shortcuts and icons, but next time I started up a normal gnome session, the problem was cured...

I have an nVidia based video card, using the nVidia proprietary driver version 177.

> **GnuSense said:**
> What did work for me was switching /boot/grub/menu.lst from booting /boot/vmlinuz-2.6.24-21-386 to starting /boot/vmlinuz-2.6.24-21-generic.  CF now works and sound seems normal.  Hopefully the next kernel upgrade will work properly.

```
~$ uname -a
Linux Saturn 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux
```

I'll try using an earlier kernel and report back what happens.

Well, booting 2.6.24-21-generic did not help! I got a message about an error with the video system, and a prompt to ask if was OK to boot into "low graphics mode". I accepted that and sound still doesn't work.

K.

---

### Post by Keith_Beef on 2008-11-23
Well, I'm not sure yet if all these steps were necessary, but I'll describe them in the hope they'll help others.

I found other threads discussing sound problems and followed a link to [this page]("http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/").

I followed all the steps, and still had no sound.

But when I turned the amp all the way up, I heard a slight "bump" noise at ```
sudo alsa force-reload
```.

So I thought that the problem must have been half solved, at last: the sound card was sending a signal, however low, down the line to the amp.

I went into the siound mixer and turned on every single channel available... and found that the channel named "Front", which had been turned off, was muted. I unmuted it, and glorious stereo sound was restored!

Now, this makes me think that I could perhaps have got back sound this was days ago, without getting rid of PulseAudio.

If I can find no reason to restore PulseAudio, I'll leave it as it is...

K.

---

### Post by izm81 on 2008-11-24
I have the same problem.  Upgraded from Hardy to Intrepid, and now my sound doesn't work.  I will note, however, that booting from a Live CD also fails to produce sound.

If I do: ```
aplay -l
``` no devices are found - hence, no sound produced.  ```
lsmod | grep snd_hda_intel
``` shows that **snd_hda_intel** is installed, but nothing depends on it (the zero beside the module name).  That's a problem!


For a quick fix (your results may vary) you can:
```
sudo rmmod snd_hda_intel
```

followed by a ```
sudo modprobe snd_hda_intel
```

You'll have to do it every login.

I believe the cause is a bug in the **snd_hda_intel** module shipped with intrepid.  You can try installing the latest ALSA from scratch to permanently solve the issue.  I'm content with the quick-fix, for now.  I'm lazy.  ^.^

See also:
[http://forums.fedoraforum.org/showthread.php?t=203389](http://forums.fedoraforum.org/showthread.php?t=203389)

---

### Post by Kymus on 2008-11-24
Thanks for that input *izm81*!

peculiarly, I get an error after trying the example you gave

```
kymus@Shouxing:~$ sudo rmmod snd_hda_intel
ERROR: Module snd_hda_intel does not exist in /proc/modules

```

I will probably just end up reinstalling ALSA (or really, upgrading to the newer version) because I'm sort of stuck in limbo.. I disabled ALSA to try OSS, but that didn't work, and now I can't figure out how to re-enable ALSA so that I can finish with the bug report on launchpad.

---

### Post by oedenfield on 2008-12-10
> **Kymus said:**
> just an update...

I was browsing through the forum and found this suggestion:

```
sudo killall pulseaudio

sudo alsa force-reload

```



Unfortunately, this produced no results >_<

Last night audio worked fine (as it always has on this system) with Intrepid..  today no dice.  I double-click a track in Rhythmbox and the art pops up but the counter never changes.  Did the above and now it seems like audio is working again. *fingers crossed*

---

### Post by Kymus on 2009-01-11
Well, today I sat down and updated alsa and still nothing; no sound. At this point, I am wondering as to what would possibly fix this issue outside of reinstalling Ubuntu (which I would really like to avoid).

---

### Post by Kymus on 2009-01-12
bump

---

### Post by clb on 2009-03-30
> **Kymus said:**
> just an update...

I was browsing through the forum and found this suggestion:

```
sudo killall pulseaudio

sudo alsa force-reload

```



Unfortunately, this produced no results >_<

This did it for me. I'm on a fresh install of Intrepid x86_64

---

### Post by Kymus on 2009-03-30
> **clb said:**
> This did it for me. I'm on a fresh install of Intrepid x86_64

I'm glad you found success :)

At this point, I've tried all sorts of things and I've met failure at each of them. My last resort is to hope that the next upgrade will magically fix this....

---

### Post by bcrowell on 2009-03-30
I'm having the same problem, and none of the ideas suggested above seem to help. This is on Intrepid, x64, with ALC880 audio. Sound used to work fine with Ubuntu, and still works fine when I boot with a live CD. I can't remember now whether it stopped working when I upgraded to intrepid, or whether it was after that. Doing "lsmod | grep snd_hda_intel" shows that I have the relevant module loaded. Doing an "alsa force-reload" doesn't fix anything.

---

### Post by bcrowell on 2009-04-04
Aha, I get it. I just wasn't understanding the user interface. I had a speaker icon in the Gnome menu bar with a red circle with a slash through it. I had interpreted it to mean "your sound card isn't working," or something like that. What it actually meant was that I had my sound *muted*. IMO this is really bad UI design. I had no idea that it meant my sound was muted, that I could bring up the gnome-volume-control application by double-clicking on the icon, or that the way to unmute it was with gnome-volume-control.

---

### Post by Kymus on 2009-05-16
Well, I just upgraded to 9.04 and still no sound.

I was hoping that upgrading would magically fix things (which has happened some in the past), but no luck here. 

I have [tried posting this bug on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324879?comments=all") and there were no suggestions that worked.

At this point I am wondering if it will either require a miracle to fix things or if I am just going to have to reinstall Ubuntu.

**EDIT:** Very interesting! I decided to see if KDE would play any sound for me. After living 6+ months with no sound, I'm pretty desperate so I tried a shot in the dark. KDE is playing sound for me just fine. Gnome however, is not... The plot thickens..

---

### Post by Kymus on 2009-05-20
6+ months and the solution was right under my nose. 

[This]("https://answers.launchpad.net/ubuntu/+question/71573") is what helped me.

---

### Post by paradigm2 on 2009-05-20
> **Kymus said:**
> 6+ months and the solution was right under my nose. 

[This]("https://answers.launchpad.net/ubuntu/+question/71573") is what helped me.

Thanks for sharing the solution to your issue.  It may help others. :)

---

