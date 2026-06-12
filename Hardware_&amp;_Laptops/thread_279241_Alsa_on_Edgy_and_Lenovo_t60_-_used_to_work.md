---
title: "Alsa on Edgy and Lenovo t60 - used to work"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by akvik on 2006-10-17
Hi, I'm running latest edgy on a lenovo t60. I remember that the sound used to work when I installed edgy, but now it doesn't work anymore. Anyone knows how to solve this? I have tried several different .asoundrc and looked at the  how-tos but with no luck so far.

The modules seems to be loaded:
```

:~$ lsmod | grep snd
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

```

And the hardware is detected:
```

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

..but still:
```
:~$ aplay Desktop/Music/Iron\ Maiden\ -\ Can\ I\ Play\ Wi.mp3 
ALSA lib pcm_direct.c:819:(snd_pcm_direct_initialize_slave) snd_pcm_hw_params_any failed
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to initialize slave
aplay: main:547: audio open error: Invalid argument

```

Anyone that knows?

:-)

---

### Post by akvik on 2006-10-21
Bump?

---

### Post by akvik on 2006-10-23
I recently discovered that a friend of mine has the exact same computer, lenovo t60, with the exact same system, latest dapper, and his sound works! I tried to copy his settings, but with no luck. 

This is strange, I've tried everything, from booting the live cd (no luck - still no sound) to compiling the latest alsa version. still getting the
```
 aplay login.wav
ALSA lib pcm_direct.c:867:(snd_pcm_direct_initialize_slave) snd_pcm_hw_params_any failed
ALSA lib pcm_dmix.c:876:(snd_pcm_dmix_open) unable to initialize slave
aplay: main:550: audio open error: Invalid argument

```

---

### Post by akvik on 2006-10-23
By looking at this thread:
[http://ubuntuforums.org/showthread.php?t=261246&highlight=t60](http://ubuntuforums.org/showthread.php?t=261246&highlight=t60)

I found out what the problems were - it probably has to do with the modules being loaded in the wrong way or something. By doing:
```

# sudo /etc/init.d/alsa-utils stop

# sudo /etc/init.d/alsasound stop [edited - used to be alsabase, which is wrong :-)]

# modprobe snd-hda-intel

```
The modules load up right and sound is back again!

---

### Post by lamborghiniwang on 2006-11-02
> **akvik said:**
> 
```

# sudo /etc/init.d/alsabase stop

```


I'm having the same problem, and when I run this command I got error message says 
```

# sudo /etc/init.d/alsabase stop
sudo: /etc/init.d/alsabase: command not found

```
:( 
Any suggestions?

btw, I also got the following error message when running lsmod:
```

$  lsmod | grep snd | cut -d' ' -f1 | xargs -n 1 sudo rmmod
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_hda_codec is in use by snd_hda_intel
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_hda_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd is in use by snd_hda_intel,snd_hda_codec,snd_pcm,snd_timer
ERROR: Module soundcore is in use by snd
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm

```

---

### Post by akvik on 2006-11-04
That's right, it's supposed to be:
```
# sudo /etc/init.d/alsasound stop 
```

But I have found another reason for this problem - I had my modem disabled in BIOS and it seems that the sounds works perfectly when i enable the modem again - have you also disabled the modem in BIOS?

---

### Post by aetherane on 2006-11-05
I have been having a similar problem. I got alsa sound to work when I uninstalled the alsa-base package. I haven't been able to get oss to work yet though, even when using aoss.

---

### Post by akvik on 2006-11-05
Oss works for me - do you have the /dev/dsp device for instance? And you've installed alsa-oss? 

The only packages I have installed with "alsa" in it is alsa-base, alsa-oss, alsa-utils plus gnome-alsa-mixer (not necessary) and naturally, linux-sound-base.

Running latest edgy.

---

### Post by lamborghiniwang on 2006-11-05
Thanks guys. It's working now.:)

---

### Post by cmavr8 on 2006-11-08
Sound problem on a Lenovo 3000 V100, too.

Tried the three above commands but got an error during executing the second: 
```
chris@chris-laptop:~$ sudo /etc/init.d/alsasound stop
sudo: /etc/init.d/alsasound: command not found

```
("The three commands:" ```
# sudo /etc/init.d/alsa-utils stop

# sudo /etc/init.d/alsasound stop [edited - used to be alsabase, which is wrong :-)]

# modprobe snd-hda-intel
```)

Please note that sound works once in a blue moon. If I reboot 10 times, it will work 2-3 of them...

---

### Post by cmavr8 on 2006-11-08
Also tried to add to the file /etc/modprobe.d/options the line: options snd-hda-intel model=laptop-eapd, as recommended in another thread of this forum...

Still no luck... (sound works 2/6reboots)

---

### Post by cmavr8 on 2006-11-08
Sorry for double posting... can't delete it now... Moderators please delete this post for me.

Thanks

---

### Post by akvik on 2006-11-08
Hi,

the three commands won't always work, it's just when you have this particular problem with the modules not being loaded correctly (or whatever the reason is). 

A lot of factors can mess up your alsa setup. Did you try any of the howto's on the forum? Has it worked for you consistently in the past, not just two out of six? You need to give more info, such as the output of:
```

$ cat /proc/asound/version 
$ cat /etc/modprobe.d/alsa-base

```

---

### Post by cmavr8 on 2006-11-09
> **akvik said:**
> Hi,

the three commands won't always work, it's just when you have this particular problem with the modules not being loaded correctly (or whatever the reason is). 

A lot of factors can mess up your alsa setup. Did you try any of the howto's on the forum? Has it worked for you consistently in the past, not just two out of six? You need to give more info, such as the output of:
```

$ cat /proc/asound/version 
$ cat /etc/modprobe.d/alsa-base

```

Hello akvik, and thanks for the reply.
I have tried many different methods (about 4) and still no solution. I still get the 2/6 sound. But when it works it is perfect. I mean nice quality, mic works, speakers mute when headphones are plugged etc.

It worked perfectly out of the box with kernels up to 2.6.15.26. When I upgraded to kernel 2.6.15.27 it stopped. I didn't pay attention, I just used .26.

But now with edgy (2.6.17.10-generic) it does the 2/6 strange behavior again.

Here are the results you asked for:

```
chris@chris-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).
```

```
chris@chris-laptop:~$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

```

Thanks for the professional help!

Chris

---

### Post by cmavr8 on 2006-11-09
Please note I've tried

1. [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME)

2. "Opening a terminal window and doing "asoundconf reset-default-card" didn't initially change anything, but then I restarted; all is well." from [http://ubuntuforums.org/showthread.php?t=286016&highlight=edgy+sound+problem](http://ubuntuforums.org/showthread.php?t=286016&highlight=edgy+sound+problem)

3. Also tried unmuting and # alsamixer

No, nope, nothing... no sound. Two times working, 4 (I think) not...

I tried changing the sound preferences to OSS, or alsa, but no change. Default was Autodetect. (all drop-down lists from the first tab, except for the last one..)

---

### Post by akvik on 2006-11-09
Strange...

You have a Realtek ALC883 chipset on your audio card, so you should definetly go for the  snd-hda-intel module. 

Try:
```

$ aplay /usr/share/sounds/login.wav

```
What the output of that command?

By the way, I don't use an .asoundrc or a /etc/asound.conf at all, so if you have one, maybe it could be an option to move them or remove them, and then see what happens.-

---

### Post by cmavr8 on 2006-11-09
```
chris@chris-laptop:~$ aplay /usr/share/sounds/login.wav
Playing WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
chris@chris-laptop:~$ 
```

What are .asoundrc or a /etc/asound.conf? How do I disable them? (I found the second file... but what is it?)

---

### Post by akvik on 2006-11-09
It's a file that you use if you have a particular setup. Sometimes it's necessary to get it to work at all, and sometimes it's the reason for it not working... 

To me it seems to be nothing wrong with the alsa setup, since you can play the audio. There is something trivial at play, here. Such as alsa muting itself, or some other program interfering with alsa. Try to turn off the ESD sound system in the sound preferences, and see if that works. Also try to rename the asound config file.

:-)

---

### Post by cmavr8 on 2006-11-14
Hi akvik again,

I did something a few days ago (after your post) that seems to have fixed the problem.

I've been playing with the ESD checkbox in sound settings, and changing the devices from AUTODETECT to ALSA.

I think it now works but something big has been changed. Maybe I have executed some command I found on the web but can't remember where it was. (reboot was needed).

Anyway, I now have sound but the generic volume control has no effect! Only the "front" vol control controls the sound. This is true when accessing vol control from alsamixer or the default volume manager.

Also, skype doesn't work anymore. 

Maybe I should search for the command I executed, if any..

---

### Post by cmavr8 on 2006-11-14
Update!

When in Sound Preferences, Devices tab I set to all autodetect (except for the last), the 2-reboot-working effect appears. If I choose ALSA to all, I get the following:

No notification to enter my username at beginning.
Loging in sound
Music ok.
Skype calls (tone is heard) but after a while "Problem with sound device". In skype's setting I have set  ALSA, not OSS. (although it says "1 device found" for both of them)

Should I try anything else in sound preferences other than autodetect and ALSA? I have another 3 options..

---

### Post by cmavr8 on 2006-11-14
I renamed asound.conf and set all (except for the last) to AUTODETECT.

WHen rebooted, no username sound, but login and other sounds work ok! Volume controls ok. Skype ok!

I wish it is a constant effect and not just one of the two times it works... I'll keep you posted!

Thanks!

---

### Post by cmavr8 on 2006-11-14
Well it's not...

Not good. Nothing is working even with a renamed asound.conf.

I will set ALSA instead of autodetect and try again..

---

### Post by akvik on 2006-11-14
Well, you seem to be working hard with this. I think that your last Autodetect setup where also Skype works is the correct setup. Then I think that something else is messing with your sound, that is not directly related to your sound setup. But I don't know what...

---

### Post by TAA_carames on 2006-11-15
I have a Lenovo 3000 v100 too and after trying a lot of the suggested commands i tried reinstalling alsa-base and libasound2 and then everything worked.. 
So:
```
sudo aptitude reinstall alsa-base
sudo aptitude reinstall libasound2
```
And all sounds should work once again.
I don't know what i did to destroy it but.. Well now it works.

---

### Post by cmavr8 on 2006-11-16
Thanks for the tip TAA. I tried it and had the same results... Did three reboots, sound worked perfectly on the first two... I have the sound settings set to "autodetect".

I noticed  that when booted for the third time, someone (some program) has touched the volume controls...

What can be causing that?
Anybody?

Thanks for the intrest, anyway..

---

### Post by Znero on 2007-03-02
I just wanted to mention that the problem still seams to exist. 
I've tried everything from this thread (playing with hardware-keys, looking at the alsa-mixer, reinstalling the stuff, loading snd_hda_intel on bootup, setting everything to autodetect and finally recompiling newest alsa-drivers and installing them) but nothing helped. 
There where a few sessions it worked pefectly, but most of the time i just hear an extremely quiet whisper if i put all sound-controls to maximum.

---

### Post by akvik on 2007-03-02
Hi,

It's been a while since I had this problem, but for me it works without problems now. I don't have t do anything special to make alsa work at this moment. The problem was solved for me when i activated the modem in BIOS.

:)

---

### Post by Athropos on 2007-03-16
Hi all,

just installed an Edgy on a T60 and I'm unable to get any sound. Everything seems OK, all modules are correctly loaded and I get no error when I try to play something. I just get no sound at all. The modem is enabled in the BIOS.

Any idea?

---

### Post by cmavr8 on 2007-03-16
Tried suspending/resuming?
Tried restarting/loging in/ trying sound at least 3 times?

You could search in the thread/forum for possible solutions. Some work for some...

---

### Post by scoot1212 on 2007-03-16
I have a T60 WS and I had problems with my sound.  Turns out that if you have the modem disabled in the bios you will have problems in linux.
Scott

---

### Post by Athropos on 2007-03-17
I tried everything I could find on this board or other ones. All modules are correctly loaded. Everything is unmuted in alsamixer. The modem IS enabled in the bios. Still no sound...

I can't understand why there's no error. If something is wrong with the driver it should output some kind of error...

---

### Post by Athropos on 2007-03-17
I finally got it to work by playing with the volume buttons on top of the keyboard...

---

### Post by akvik on 2007-03-17
What the output of:
```

aplay /usr/share/sounds/login.wav 

```

if your output is:
```
Playing WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
```

Then that's normal, and good news. Then you should look into your sound preferences and your alsa mixer, and see if something is not set.

---

### Post by koremoke on 2007-03-20
Sorry to just randomly jump in, but I seem to have a similar problem, soI tried that  code and it gives the correct output, but I'm a complete newbie to all of this linux stuff, Could you assist me with the alsamixer and sound preferences?

---

### Post by Athropos on 2007-03-21
Do you have the same laptop? I discovered that in my case the sound was muted internally and absolutely not linked to what alsamixer was showing. When I use the mute key on the keyboard, the sound is muted but everything is still displayed unmuted in alsamixer. Pressing again the mute key has no effect, I have to use the volume up/down keys for that.

---

### Post by koremoke on 2007-03-21
Oops, i feel dumb, i didn't really explain the situation.

It is exactly the same problem with no sound whatsoever, but with my Dell Dimension 8300, a desktop. ^_^

No real mute/volume keys as i'm using a fairly standard keyboard that came with the machine.

---

### Post by kanzie on 2007-04-06
I have this problem as well... I've had sound before, but then one day, it stopped. I have no direct idea to what caused the sound to disappear, but it did. T60 model, all settings are just like recommended in this thread, all commands generate the proper output. The aplay of the login shows that it is playing nicely, tried fiddeling with the buttons on the keyboard, the top-right-icon shows sound enabled, the alsamixer says its 98% soundlevel, the sound-preferences is auto-detect. 

Nothing complains, but still no sound.

Where to look now?

---

### Post by cmavr8 on 2007-04-23
Upgraded to Feisty Fawn 7.04.

Sound even worse now. Skype won't recognise my sound devices. Avidemux won't play audio ("trouble initializing audio device" error when ALSA is selected, no error, no sound when DUMMY selected) and Totem Movie player won't start (crashes on start).

reinstalled audio device but nothing changed...

Rhythmbox plays music normally

---

### Post by akvik on 2007-04-23
Hi,

that sounds strange (literally ;) ), my t60 works like a charm with feisty. Do you have the restricted modules for the kernel installed? Not that I know if this will solve your problem, but I suspect I have some packages installed, that you don't. Does your sound work with the Feisty live CD, by the way?

---

### Post by npcomplete on 2007-04-24
I fixed my sound problem by referring the following thread,

[http://ubuntuforums.org/showthread.php?p=2529058#post2529058](http://ubuntuforums.org/showthread.php?p=2529058#post2529058)

Just unmuting each item shown in alsamixer.

---

### Post by RustyWyatt on 2007-05-31
FYI,

With my brand new T60, turning off the modem kills the sound, turning it back fixes everything (running 7.04).

Thanks once again to all of the users who provide support!!

Tom

---

### Post by Athropos on 2007-05-31
FIY, I also noticed that using the suspend to /disk/RAM/ also kills the sound. I followed the instructions given on [this page]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T60") but it seems that the module cannot recover properly.

---

### Post by ibzter on 2007-08-31
The HDA Intel won't work if the internal modem is disabled in the BIOS settings. When you boot your computer, get into the BIOS settings and make sure that it hasn't been disabled.

---

